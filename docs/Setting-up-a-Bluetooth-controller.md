# Adding a Bluetooth controller to RetroPie  
This guide is geared to using a controller from [8bitdo](http://www.8bitdo.com) but should work with a range.



<a href="https://www.youtube.com/watch?v=EiDJFdWXweI
" target="_blank"><img src="https://i.ytimg.com/vi_webp/EiDJFdWXweI/mqdefault.webp" 
alt="RetroPie with Bluetooth" width="300" height="190" border="10" /></a>  
  
**Video Guide**: https://www.youtube.com/watch?v=EiDJFdWXweI  

**Controller Firmware**  
Make sure you have the latest firmware for your controller. You will need a USB cable to do this. The firmware for 8bitdo controllers is here: http://8bitdo.com/Support.html

**Step 1 - Download and install the Bluetooth packages**  
Quit Emulation Station with F4 (stop it restarting by pressing another key within 5 secs) and type this at the command line:  
`sudo apt-get install bluetooth bluez-utils blueman` (_Press Y if prompted_)  
`sudo apt-get install bluez python-gobject`  

**Step 2 - Make sure the Bluetooth pair works**  
Then, whilst this step could be avoided with a command line parameter later, for the moment edit this file  
`sudo nano /usr/bin/bluez-simple-agent`  
  
Find the text "KeyboardDisplay" in the file, and replace it with "DisplayYesNo", making sure to get the case sensitivity correct.  
  
Now reboot, and quit Emulation Station to get back to a command prompt.  
  

**Step 3 - Pairing and connecting the Bluetooth controller**  
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


**Some useful threads**  
http://blog.petrockblock.com/forums/topic/8bitdo-bluetooth-controller-setup-retropie-v3/  
http://blog.petrockblock.com/forums/topic/the-old-story-setting-up-2x-8bitdo-nes30-bluetooth/  
http://forum.8bitdo.com/thread-328-1-1.html