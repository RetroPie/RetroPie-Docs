# Adding a Bluetooth controller to RetroPie  
This guide is geared to using a controller from [8bitdo](http://www.8bitdo.com) but should work with a range of bluetooth devices.  
The examples below are assuming you have just a keyboard and bluetooth dongle plugged into your Pi.  


<a href="https://www.youtube.com/watch?v=EiDJFdWXweI
" target="_blank"><img src="https://i.ytimg.com/vi_webp/EiDJFdWXweI/mqdefault.webp" 
alt="RetroPie with Bluetooth" width="300" height="190" border="10" /></a>  
  
**Video Guide**: https://www.youtube.com/watch?v=EiDJFdWXweI  

**Controller Firmware**  
Make sure you have the latest firmware for your controller. You will need a USB cable to do this. The firmware for 8bitdo controllers is here: http://8bitdo.com/Support.html

### Step 1 - Download and install the Bluetooth packages  
Quit Emulation Station with F4 (stop it restarting by pressing another key within 5 secs) and type this at the command line:  
`sudo apt-get update`  
`sudo apt-get install bluetooth bluez-utils blueman` (_Press Y if prompted_)  
`sudo apt-get install bluez python-gobject`  

### Step 2 - Make sure the Bluetooth pair works  
Then, whilst this step could be avoided with a command line parameter later, for the moment edit this file  
`sudo nano /usr/bin/bluez-simple-agent`  
  
Find the text "KeyboardDisplay" in the file, and replace it with "DisplayYesNo", making sure to get the case sensitivity correct.  
  
Now reboot, and quit Emulation Station to get back to a command prompt.  
  

### Step 3 - Pairing and connecting the Bluetooth controller  
Set your Bluetooth controller to pair in "joypad" mode. For example, for the FC30 Pro, you do this by holding the power switch for 3 secs. The guide is here: [FC30 Pro Manual](http://download.8bitdo.com/Manual/FC30_Pro_Manual_ENG_v1.0.pdf)  
  
Type this at the command prompt  
`hcitool scan`  
This should find your controller and show its name and [MAC](https://en.wikipedia.org/wiki/MAC_address) address  
  
Pair the controller with this command, replace the XX data with your MAC address  
`sudo bluez-simple-agent hci0 XX:XX:XX:XX:XX:XX`  
  
Tell the system to trust your controller so you dont have to pair every time  
`sudo bluez-test-device trusted XX:XX:XX:XX:XX:XX yes`  
  
Then connect to your controller with  
`sudo bluez-test-input connect XX:XX:XX:XX:XX:XX`  
  
Your controller should then connect, with the 8bitdo controllers this is shown by a solid blue light that will begin to glow.  
  
### Step 4 - Making sure the connection attempt automatically starts when you reboot your Pi  
You may find the controller connects on startup without issue, but if not try this. There are different ways to do this, but this should work to start the connection attempt when the Pi starts up.  
Edit this startup file  
`sudo nano /etc/init.d/rc.local`  
  
under the line _. /lib/lsb/init-functions_ add this line (making sure to replace the XX values with the MAC address of the controller found earlier)  
`sudo bluez-test-input connect XX:XX:XX:XX:XX:XX`  
  
Save the file with Ctrl-X and press Return to confirm the filename.  

Now reboot the Pi.  

### Step 5 - Configuring the controller using Emulation Station  
Now the Pi is restarting, make sure your controller is turned on, and trying to pair, it should connect about when the Emulation Station splashscreen appears. Then Emulation Station will display with the "1 Gamepad Detected" message.  

Hold a button down on the controller and follow the instructions to input your buttons.  
When the is done, you click the "OK" button with the "A" button on the controller to enter Emulation Station.  
This process will have configured your controller for navigating ES. It will also have created a controller file for RetroArch to use when you play games (If you are using at least RetroPie 3 beta 3).  
  
However, the content of that file may not have the correct buttons mappings (I'm not sure why this doesn't always work, as its fine with most other controllers). So we will update that file correctly now.  
  
### Step 6 - Updating the controller file for RetroArch  
Press F4 to quit Emulation Station, and at the command prompt type  
`cd /opt/retropie/configs/all/retroarch-joypads/`  
`ls -lah`  
    
This should display the configuration file you created, delete it (although the next steps should overwrite this anyway) with:  
`rm {filename} `  
for example  
`rm 8BitdoFC30Pro.cfg`  
  
Now we will recreate this using the retroarch controller script, type  
`sudo /home/pi/RetroPie-Setup/retropie_setup.sh`  
  
Choose the "Setup" option, then "Configure input devices for RetroArch" (Do **not** choose the "Install RetroArch joypad autoconfigs)  
Then choose the "Configure joystick/controller for use with RetroArch" option  
Follow the on-screen prompts to press the buttons when prompted.  
If you make a mistake, just run it again, it happily overwrites the file it needs to.  

There should be no need to edit the retroarch.cfg to get your controller working.  
  
That should be all you need. Now when you start your Pi, set the controller to connect and it should be detected by Emulation Station and RetroArch based emulators.  
  
### Troubleshooting  
If you have installed other bluetooth programs, perhaps to support a PS3 controller, you may find there are conflicts and the above steps produce an error when you try to pair. One way around this is to uninstall the sixad program with:  
`sudo apt-get –purge remove sixad`
  
If you are unsure your USB Bluetooth dongle is detected with the Pi, you can list the USB devices with:  
`lsusb`

**Some useful threads**  
http://blog.petrockblock.com/forums/topic/8bitdo-bluetooth-controller-setup-retropie-v3/  
http://blog.petrockblock.com/forums/topic/the-old-story-setting-up-2x-8bitdo-nes30-bluetooth/  
http://forum.8bitdo.com/thread-328-1-1.html