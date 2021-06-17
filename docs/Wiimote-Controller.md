## About
Three different tutorials to help get your wiimotes/nunchuck/classic controllers etc.. to work with RetroPie. 

```Method 1``` uses wminput and cwiid to get the wiimotes to connect. Its fairly simple method to follow with easy instructions to follow. I recommend this one for beginners who are new to RetroPie and don't want to dabble too much with linux.   

```Method 2``` uses MoltenGamepad which is described as a flexible input device remapper, geared towards gamepads. This method is also simple to follow along if you can't get the first method working.  

```Method 3``` was the original tutorial using xwiimote before we found and developed easier ways of connecting wiimotes for use with RetroPie. It is simply listed here for those wishing to still view it. 

***

## Method 1 (wminput and cwiid):
The basis of this method was taken from [here](http://blog.petrockblock.com/forums/topic/tutorial-to-get-wiimotes-with-classic-controllers-to-work-with-retropie/). It has however been slightly updated and modified to work with the current version of RetroPie(3.7). 

This tutorial shows how to get one to four wiimotes (the controller of Nintendo Wii) running with RetroPie with or without a classic controller (attached to the wiimote).

### Prerequisites

1. For the following I assume that RetroPi was installed and is running with other controls (like keyboard, joystick etc.). I followed the excellent tutorial http://supernintendopi.wordpress.com/2013/01/23/an-a-to-z-beginners-guide-to-installing-retropie-on-a-raspberry-pi/  for this (using the “RetroPie Project SD Card Image”).

2. You have a Raspberry Pi 3 or for Raspberry Pi 2 and below, you need a Bluetooth dongle (sometimes called Bluetooth adapter). For a list of dongles known to work with Raspberry Pi see http://elinux.org/RPi_USB_Bluetooth_adapters#Working_Bluetooth_adapters ).

I can confirm putting the Bluetooth adapter into a USB 2.0 powered hub works. Your results may vary though depending on your hardware.      

Its important to update RetroPie to the latest version to avoid problems later down in the tutorial. Type the following into the command line:

```shell
cd RetroPie-Setup/
```
In this folder, we will load up the Retropie post install script:
```shell
 sudo ./retropie_setup.sh
```
In the menu, choose to update the RetroPie-Setup script (option U) first. The pi will connect to the internet and fetch the latest version. After that's done, choose Binary-based installation (option 1). Depending on your pi version, this can take a while. On a pi zero, it took about 30 minutes.  

### Installation

Now install the needed parts:
```shell
sudo apt install bluetooth vorbis-tools python-cwiid wminput
```

### Getting the wiimotes to work

uinput device needs to work with non-root users. To do so, create a wiimote rule file.

```shell
sudo tee /etc/udev/rules.d/wiimote.rules << EOF
KERNEL=="uinput", MODE="0666"
EOF
```

That's the rule implementation done. Save the text file with ```CTRL + X``` and press ```Y``` to confirm. To make this change active, reboot the Raspberry Pi, or paste this command at the command line:
```shell
sudo service udev restart
```

Check that the bluetooth dongle works with the command below:
```shell
/etc/init.d/bluetooth status
```
You should get something similar to the below output which returns that the bluetooth is working.
```shell
● bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled)
   Active: active (running) since Tue 2016-03-22 16:10:39 GMT; 33min ago
     Docs: man:bluetoothd(8)
 Main PID: 337 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           └─337 /usr/lib/bluetooth/bluetoothd
```
### Correct usage of wminput

For every wiimote, we need one wminput command to map the wiimote (and the classic controller) buttons to something emulationstation and the emulators can work with. wminput comes with configuration files (in directory /etc/cwiid/wminput). I created my own configuration file, which works if you use a wiimote with or without a classic controller. Create the file wminput which will reside in our pi's home directory:
```shell
tee /home/pi/mywminput << EOF
# Classic-Controller
Classic.Dpad.X = ABS_HAT0X
Classic.Dpad.Y = -ABS_HAT0Y
Classic.LStick.X = ABS_X
Classic.LStick.Y = -ABS_Y
Classic.RStick.X = ABS_RX
Classic.RStick.Y = -ABS_RY
Classic.A = BTN_A
Classic.B = BTN_B
Classic.X = BTN_X
Classic.Y = BTN_Y
Classic.Minus = BTN_SELECT
Classic.Plus  = BTN_START
Classic.Home  = BTN_MODE
Classic.L  = BTN_TL
Classic.R  = BTN_TR
Classic.ZL = BTN_TL2
Classic.ZR = BTN_TR2

# WiiMote
Wiimote.A		= BTN_A
Wiimote.B		= BTN_B
Wiimote.Dpad.X		= ABS_Y
Wiimote.Dpad.Y		= -ABS_X
Wiimote.Minus	= BTN_SELECT
Wiimote.Plus	= BTN_START
Wiimote.Home	= BTN_MODE
Wiimote.1		= BTN_X
Wiimote.2		= BTN_Y

# Nunchuk
Nunchuk.C = BTN_C
Nunchuk.Z = BTN_Z
EOF
```
If you want your WiiMotes giving a connection status, just add an additional line to your `mywminput` file:
```shell
Plugin.led.Led1 = 1
#Plugin.led.Led2 = 1
#Plugin.led.Led3 = 1
#Plugin.led.Led4 = 1
```
You probably also want different LEDs active on two controllers, which means you have to provide different `mywminput` files to wminput, e.g. `mywminputA`, `mywminputB` etc with `LED1` and another with `LED2` activated. In the above example, `LED 1` is activated and `LED's 2`, `3` and `4` are commented out. You can replace the above example with your chosen `LED` status. 

```Updated Note```: I've had problems using the above button layout with a classic controller. It will cause the button remapping which we will do later in emulationstation to be off. I fixed this by just copy pasting the classic controls only. (I will use the classic controller to control everything and have no intention of using any buttons on the actual wiimote itself).

```shell
Classic.Dpad.X = ABS_HAT0X
Classic.Dpad.Y = -ABS_HAT0Y
Classic.LStick.X = ABS_X
Classic.LStick.Y = -ABS_Y
Classic.RStick.X = ABS_RX
Classic.RStick.Y = -ABS_RY
Classic.A = BTN_A
Classic.B = BTN_B
Classic.X = BTN_X
Classic.Y = BTN_Y
Classic.Minus = BTN_SELECT
Classic.Plus  = BTN_START
Classic.Home  = BTN_MODE
Classic.L  = BTN_TL
Classic.R  = BTN_TR
Classic.ZL = BTN_TL2
Classic.ZR = BTN_TR2
Plugin.led.Led1 = 1
```

**N.B.:** The configurations below use wminput in "daemon mode" (with the -d command line switch), which causes it to constantly poll for Wii Remotes until it finds them. If you have separate Bluetooth and wifi hardware or otherwise don't suffer severely from interference (or just don't plan to use wifi), this is the most convenient behavior. However, if you do see poor wifi performance during heavy Bluetooth activity this can become a problem, particularly when you disconnect a Wii Remote (either manually or via loss of battery power), because wminput will hammer away attempting to reconnect and likely kill or at least significantly hamper your wifi connection. If you are in this situation, you may wish to use the -q command line switch **instead** of -d. This will cause wmimput to attempt to connect for a short period before giving up, and it will never attempt to reconnect by itself.

#### Quick and Dirty Wiimote Configuration (Option A)

If you don't mind registering your wiimotes each time you restart your raspberrypi (or maybe you want the opportunity to use new wiimotes each time), you can save this script as "/home/pi/bin/attachwii.sh":
```shell
#! /bin/bash

ttl=30
alert="/home/pi/complete.oga"
fail="/home/pi/bark.oga"
begin_sound="/home/pi/robot-blip.wav"
end_sound="/home/pi/service-logout.oga"
mac="\([[:xdigit:]]\{2\}:\)\{5\}[[:xdigit:]]" # "00:" * 5 + "00"
device_file="/tmp/wiimote-scan"

function play {
    ogg123 $1 &> /dev/null &
}

function match {
    echo $1 | grep $2
}

function show {
    if [[ -n $DEBUG ]]
    then
        echo $1
    fi
}

# prevent scans from interfering with one another?
killall hcitool && sleep 5

if [[ `hcitool dev | grep hci` ]]
then
    play $begin_sound &> /dev/null &
    echo "Bluetooth detected, starting scan with ${ttl}s timeout..."

    timeout $ttl hcitool scan | while read device
    do
        show "found $device"

        if [[ `match "$device" "Nintendo"` ]]
        then
            show "matched Nintendo in $device"

            id=`echo $device | cut -d" " -f1`

            if [[ `match $id $mac` && \
                "$id"!="00:00:00:00:00:00" ]]
            then
                show "matched MAC in $id"

                echo -n "Detected Wiimote with ID: ${id}..."
                wminput -d -c /home/pi/mywminput $id &
                echo " registered."
                play $alert
            fi
        fi
    done

    play $end_sound
    echo "Scan complete."

    if [[ "$rebootWithoutWiimotes" == "1" && -z `pidof wminput` ]]
    then
        echo "No Wiimotes detected!  Restarting..."
        sudo reboot
    fi
else
    echo "Blue-tooth adapter not present!"
    play $fail
fi
```

Replace the sounds above with your own preferred sounds.

When you restart your pi, press 1+2 on each wiimote after you hear the begin-sound.  After a few seconds, you'll hear a ding for each wiimote registered, followed by the end-sound.  If the bluetooth device isn't available, you'll hear a triple-ding warning you of the error.

Now, you can skip directly to the "Register Wiimotes Before Emulationstation Starts" section.

#### Manual Wiimote Configuration (Option B)

Use this method if you want to use the same wiimotes every time and don't want to re-register the wiimotes every time you restart your Raspberrypi.

First, scan for the wiimotes.
```shell
hcitool scan
```
and press buttons 1+2 on your wiimote(s). After a short while, the output should be something like
```shell
Scanning ...
	00:19:1D:87:90:38		Nintendo RVL-CNT-01
	00:19:1D:88:EF:12		Nintendo RVL-CNT-01
```

Take a note of the addresses of your wiimotes (the 00:19:1D:87:90:38 in the output above), we need that later.
Note: If the scan is not successful try it again using the red sync button on the back.

If the Raspberry Pi is started and emulationstation starts, we want to register the wiimotes so they can be used with emulationstation and the emulators.
I did it the following way:
```shell
mkdir /home/pi/bin
```
Create the file /home/pi/bin/attachwii.sh by using the command below:
```shell
nano /home/pi/bin/attachwii.sh
```
and paste the following contents:
```shell
#!/bin/bash
sleep 1 # Wait until Bluetooth services are fully initialized
hcitool dev | grep hci >/dev/null
if test $? -eq 0 ; then
	wminput -d -c  /home/pi/mywminput 00:19:1D:92:90:38 &
	wminput -d -c  /home/pi/mywminput 00:19:1D:84:EF:33 &
else
	echo "Blue-tooth adapter not present!"
	exit 1
fi
```

```Note```: You need one wminput line for every wiimote you want to use (i.e. the above is for two wiimotes)

```Note 2```: You need to replace the addresses of the wiimotes above by the addresses of your wiimotes (shown by command "hcitool scan" as shown above).

```Note 3```: I've had more success with 2 classic controllers pairing when both are sharing the same mywminput path. Since both wiimotes are using the same "mywminput" config, the LED status on port 1 of the wiimote will light up on both wiimotes. This is fine and does not interfere with anything. I simply use the light to tell me when and if both controllers are paired successfully. That is it's only purpose. I've had less success configuring a second mywinput to the 2nd controller so the LED lights differs on the 2nd controller. 

### Register Wiimotes Before Emulationstation Starts ###

Make your wiimote detection script executable with:
```shell
chmod 775 /home/pi/bin/attachwii.sh
```

#### RetroPie 3.x & 4.x ####

To start the script before emulationstation starts, edit the file: `/etc/profile.d/10-emulationstation.sh` (for 3.x) or `/etc/profile.d/10-retropie.sh` (for 4.x). Write the following line before the line with ``[ "`tty`" = "/dev/tty1" ]`` in it.
```shell
rebootWithoutWiimotes=0 /home/pi/bin/attachwii.sh
```
and save the file.

To make the Pi restart automatically if no wiimotes are detected, change rebootWithoutWiimotes to 1.

### Register Wiimotes Before Emulationstation Starts (continued) ###

If you now do a reboot using ```sudo reboot```, wait until emulationstation has been started. When it does, ```press 1+2``` on all of your wiimotes to register the wiimotes.
If it's your first time booting emulationstation then you will be automatically at the controller config menu. If you've configured a controller previously then get to the menu using a configured keyboard or an alternative controller. 

Hold any button on the wiimote (or if your using classic controller only method) then any button the classic controller.
It should say `NintendoWiimote`. Define the controls and skip and inputs that aren't necessary. Click OK, by pressing A either on the wiimote or classic controller. If your using 2 or more wiimotes/classic controllers, you only need to define one classic controller/wiimote as they will ALL share the same controls.   

You can compare my config to yours if you'd like. Don't copy and paste my config though. emulationstation needs to create this file in the menu and copy/pasting this part may cause problems later.  

In emulationstation, the mapping is located here: `/home/pi/.emulationstation/es_input.cfg`:
```xml
<?xml version="1.0"?>
<inputList>
  <inputAction type="onfinish">
    <command>/opt/retropie/supplementary/emulationstation/scripts/inputconfiguration.sh</command>
  </inputAction>
  <inputConfig type="joystick" deviceName="Nintendo Wiimote">
    <input name="pagedown" type="button" id="5" value="1"/>
    <input name="start" type="button" id="9" value="1"/>
    <input name="pageup" type="button" id="4" value="1"/>
    <input name="up" type="axis" id="1" value="1"/>
    <input name="a" type="button" id="0" value="1"/>
    <input name="b" type="button" id="1" value="1"/>
    <input name="down" type="axis" id="1" value="-1"/>
    <input name="right" type="axis" id="0" value="1"/>
    <input name="select" type="button" id="8" value="1"/>
    <input name="left" type="axis" id="0" value="-1"/>
  </inputConfig>
  <inputConfig type="keyboard" deviceName="Keyboard">
    <input name="start" type="key" id="13" value="1"/>
    <input name="up" type="key" id="1073741906" value="1"/>
    <input name="a" type="key" id="97" value="1"/>
    <input name="b" type="key" id="115" value="1"/>
    <input name="down" type="key" id="1073741905" value="1"/>
    <input name="right" type="key" id="1073741903" value="1"/>
    <input name="select" type="key" id="1073742053" value="1"/>
    <input name="left" type="key" id="1073741904" value="1"/>
  </inputConfig>
</inputList>
```



### Configuring RetroArch ###

We are going to define the controls for 2 classic controllers/wiimotes in retroarch's emulator config file:
```shell
sudo nano /opt/retropie/emulators/retroarch/retroarch.cfg
```
and at the end of the file, paste the following:
```shell
# PLAYER 1
input_player1_joypad_index = "0"
input_player1_a_btn = "0"
input_player1_b_btn = "1"
input_player1_x_btn = "2"
input_player1_y_btn = "3"
input_player1_l_btn = "4"
input_player1_r_btn = "5"
input_player1_l2_btn = "6"
input_player1_r2_btn = "7"
input_player1_select_btn = "8"
input_player1_start_btn = "9"
input_player1_up_axis = "+1"
input_player1_down_axis = "-1"
input_player1_left_axis = "-0"
input_player1_right_axis = "+0"
input_player1_l_x_plus_axis = "+2"
input_player1_l_x_minus_axis = "-2"
input_player1_l_y_plus_axis = "-3"
input_player1_l_y_minus_axis = "+3"
input_player1_r_x_plus_axis = "+4"
input_player1_r_x_minus_axis = "-4"
input_player1_r_y_plus_axis = "-5"
input_player1_r_y_minus_axis = "+5"
# PLAYER 2
input_player2_joypad_index = "1"
input_player2_a_btn = "0"
input_player2_b_btn = "1"
input_player2_x_btn = "2"
input_player2_y_btn = "3"
input_player2_l_btn = "4"
input_player2_r_btn = "5"
input_player2_l2_btn = "6"
input_player2_r2_btn = "7"
input_player2_select_btn = "8"
input_player2_start_btn = "9"
input_player2_up_axis = "+1"
input_player2_down_axis = "-1"
input_player2_left_axis = "-0"
input_player2_right_axis = "+0"
input_player2_l_x_plus_axis = "+2"
input_player2_l_x_minus_axis = "-2"
input_player2_l_y_plus_axis = "-3"
input_player2_l_y_minus_axis = "+3"
input_player2_r_x_plus_axis = "+4"
input_player2_r_x_minus_axis = "-4"
input_player2_r_y_plus_axis = "-5"
input_player2_r_y_minus_axis = "+5"
```

We need to make sure that the settings show only one time in retroarch.cfg file (i.e. if you have a line 
```shell
input_player1_b_btn = "0"
```
in the retroarch.cfg file before adding my lines, remove (or out-comment) the whole section. If you want to use more than two wiimotes, search for the line
```shell
input_player1_joypad_index = 0
```
in retroarch.cfg and add the a corresponding line for the other wiimotes. For example you should have the following lines in retroarch.cfg for four wiimotes:
```shell
input_player1_joypad_index = 0
input_player2_joypad_index = 1
input_player3_joypad_index = 2
input_player4_joypad_index = 3
```

Finally we are going to define a button to exit out the emulator.
```shell
sudo nano /opt/retropie/configs/all/retroarch.cfg
```
 Add the following lines at the end of the file:
```shell
#savestate_auto_save = true
#savestate_auto_load = true
input_enable_hotkey_btn = "8"
input_exit_emulator_btn = "9"
input_menu_toggle_btn = "10"
```
If you want to use savestates, then uncomment it out. When you quit a game through this method, your game state will be saved and reloaded. 

The input commands specified above, allow you to exit out the emulator when ```SELECT``` and ```START``` are pressed at the same time. Pressing ```SELECT``` enables the hotkey whilst ```START``` is assigned to exit. Pressing ```SELECT``` and the ```HOME``` button however, will enable retroarch's menu for in game adjustments. 

**DONE!**
*I highly encourage you to read the "Known Issues" section below for optional fixes that complement this method:

***

#### Known issues ####

**1. My SSH terminal is unusable and giving me socket control errors!**

In some cases the connection with the Wiimotes through `wminput` daemon can 
start flooding your terminal session with the message `Socket connect error 
(control channel)`. So far there is only one 
[solution](https://www.raspberrypi.org/forums/viewtopic.php?t=63784&p=482624): 
Redirecting the *standard out* and *standard error* respectively to `/dev/null`.

```shell
wminput -d -q -c  /home/pi/mywminput XX:XX:XX:XX:XX:XX > /dev/null 2>&1 &
```
Anyway, remember to undo this **hack** for debugging purposes.

```Note```: I actively use SSH with my retropie so I had to apply this fix so I could use my SSH terminal without being hammered with socket control errors. 
This is what my revised attachwii looks like for comparison. We created this file earlier in /home/pi/bin/attachwii.sh

```shell
#!/bin/bash
sleep 1 # Wait until Bluetooth services are fully initialized
hcitool dev | grep hci >/dev/null
if test $? -eq 0 ; then
    wminput -d -c  /home/pi/mywminput 00:19:1D:92:90:38 > /dev/null 2>&1 &
    wminput -d -c  /home/pi/mywminput 00:19:1D:84:EF:33 > /dev/null 2>&1 &
else
    echo "Blue-tooth adapter not present!"
    exit 1
fi
```

If you're doing troubleshooting of any kind remember to remove the `> /dev/null 2>&1 &"`. 

**2. My wiimotes paired the first time and now they won't pair or hold pairing!**

I have had some trouble with the fact that the USB Bluetooth adapter, after a restart, the bluetooth dongle would cease to scan for new devices. For me the following fix helped. It basically restarts the the bluetooth controller and enables it to scan before the "attachwii" script activates.
To apply the fix use the command below:
```shell
sudo nano /etc/rc.local
````
Delete anything there and and overwrite with the following: 

```shell
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
hciconfig hci0 up
hciconfig hci0 pscan
exit 0
```

**3. My retroarch controls aren't working/messed up!**

After creating the controls in emulationstation a .cfg was created and resides in the directory along with any other controllers configured here: `/opt/retropie/configs/all/retroarch-joypads/`
Mine is named `NintendoWiimote.cfg`. This is what my config file looks like:
```shell
input_device = "Nintendo Wiimote"
input_driver = "udev"
input_r_btn = "5"
input_save_state_btn = "5"
input_l2_btn = "6"
input_start_btn = "9"
input_exit_emulator_btn = "9"
input_l_btn = "4"
input_load_state_btn = "4"
input_up_axis = "+1"
input_a_btn = "0"
input_b_btn = "1"
input_reset_btn = "1"
input_down_axis = "-1"
input_r2_btn = "7"
input_right_axis = "+0"
input_state_slot_increase_axis = "+0"
input_x_btn = "2"
input_menu_toggle_btn = "2"
input_select_btn = "8"
input_enable_hotkey_btn = "8"
input_y_btn = "3"
input_left_axis = "-0"
input_state_slot_decrease_axis = "-0"
```

Compare the controls located here, to the ones we configured in Retroarch. If the values in your .cfg above is different then make sure to update the retroarch controls. For example, in my cfg, `input_b_btn = "1"` but yours may be of a different value. 
```shell
# PLAYER 1
input_player1_joypad_index = "0"
input_player1_a_btn = "0"
input_player1_b_btn = "1"
input_player1_x_btn = "2"
input_player1_y_btn = "3"......
..
```

If your using just the classic controls then you shouldn't be having this problem, but this is what I was referring to earlier when I said the controls may be "off" if you try and combine wiimote controls, nunchuck controls in addition to the classic controller to your mywminput file. 

**4. I want to update my Pi's bluetooth to the latest version!**

As of writing, the version shipped with RetroPie 3.7 comes with Bluez version ```5.23.``` We will update it to the latest stretch version which is ```5.36.```

```shell
sudo nano /etc/apt/sources.list
```

Copy and paste the ```jessie``` line and then change jessie to ```stretch```. Save with ```CTRL+X``` and ```Y``` to confirm changes.  

We are going to tell APT to (still) default to jessie:
```shell
sudo nano /etc/apt/apt.conf.d/40defaultrelease
```
and paste in with the following contents:

```shell
APT::Default-Release "jessie";
```

In the terminal, do and update followed by the Bluez install:
```shell
sudo apt update
```
then:
```shell
sudo apt install bluez -t stretch
```
BlueZ will be updated from 5.23 => 5.36. You can check the change with ```bluetoothd -v```. 

Now you can undo the changes we made to ```/etc/apt/sources.list``` and  ```/etc/apt/apt.conf.d/40defaultrelease```. 
***

## Method 2 (MoltenGamepad):

The original tutorial was posted by a user named rockfireredmoon on the RetroPie github. You can view it [here](https://github.com/RetroPie/RetroPie-Setup/issues/256/#issuecomment-205283258).

You can view more information about MoltenGamepad [here](https://github.com/jgeumlek/MoltenGamepad).    
It's on a github repository which we will need to copy onto our Pi. 

In the terminal, paste the command:
```shell
git clone https://github.com/jgeumlek/MoltenGamepad
```

Move to the MoltenGamepad folder:
```shell
cd MoltenGamepad/
```

Let's try making the MoltenGamepad binary file:
```shell
make eventlists
```

followed by:
```shell
make
```

Once completed, we should have our MoltenGamepad binary file. You can check this with the command terminal command ```ls``` 

Let's copy this to where it needs to go. We should already be in the MoltenGamepad directory.
```shell
sudo cp moltengamepad /usr/sbin
```

We are going to need to create a system service for MoltenGamepad. 
Lets create the file:
```shell
sudo nano /lib/systemd/system/moltengamepad.service
```

and paste in:

```shell
[Unit]
Description=MoltenGamepad
After=network.target
After=bluetooth.target

[Service]
Type=forking
PIDFile=/var/run/moltengamepad.pid
Environment="XDG_CONFIG_HOME=/etc/moltengamepad"
ExecStart=/usr/sbin/moltengamepad --daemon --pidfile /var/run/moltengamepad.pid
ExecStop=/usr/bin/kill $MAINPID

[Install]
WantedBy=default.target
```

Lets enable the service with the following command:
```shell
sudo systemctl enable moltengamepad
```

and lets make the settings permanent by rebooting:
```shell
sudo reboot
```

Thats MoltenGamepad installed, but we need to pair our wiimotes with ```bluetoothctl```. Nothing fancy, just simple bluetooth pairing in linux.

Lets first load the hid-wiimote kernel module:
```shell
sudo modprobe hid-wiimote
```

follwed by the bluetooth protocol:
```shell
sudo bluetoothctl
```

The following was taken from the bluetooth page on the ```archlinux wiki```. You can view it here under the "Configuration via the CLI"

**Bluetoothctl**

Pairing a device from the shell is one of the simplest and most reliable options. The exact procedure depends on the devices involved and their input functionality. What follows is a general outline of pairing a device using ```/usr/bin/bluetoothctl```:
* Start the ```bluetoothctl``` interactive command. There one can input ```help``` to get a list of available commands.
* Turn the power to the controller on by entering ```power on```. It is off by default.
* Turn the agent on with ```agent on```.
* Enter device discovery mode with ```scan on``` command if device is not yet on the list.
* Now press the red sync button behind the battery cover on the back of the wiimote. (This will also unpair it with your wii.)
* Enter ```pair MAC Address``` to do the pairing (tab completion works).
* If using a device without a PIN, one may need to manually trust the device before it can reconnect successfully. Enter ```trust MAC Address``` to do so.
* Finally, use ```connect MAC_address``` to establish a connection.
* Now disconnect with ```disconnect MAC_adress```. The wiimote should turn off.
* Now press the power button on the wiimote to reconnect. This should work after a reboot of RetroPie.
* If it didn't work, you may need to ```remove MAC-adress``` and try the whole process again.
* See also: https://wiki.archlinux.org/index.php/XWiimote#Auto-Reconnect_is_not_working_after_pairing_with_red_sync-button

All we need to do is pair the wiimotes and MoltenGamepad will handle any extra devices such as Classic Controllers, Nunchuck, Wii Balance Board etc.

You can start emulationstation directly from the terminal by typing in ```emulationstation```

You can now use ES the map all the buttons as you wish in the normal way.


**Some notes**:
The original tutorial stated that once the initial pairing was completed, you won't need to manually pair and enter the commands in the terminal. 

* reboot
* "Press a key once to connect, then again to activate moltengamepad."

I couldn't quite get mine to pair from a cold boot. Currently I still have to use the bluetoothctl ```connect``` command to pair my wiimotes attached to Classic Controlers and then manually start emulationstation from the terminal for the pairing to work. Your experience may vary however.

I am currently working on a script to automate the the pairing process without the need to press any buttons at all when EmulationStation starts to activate MoltenGamepad. At the moment its a bit hit and miss. I will update the tutorial once I've ironed the kinks out. :) 

**I also encourage anyone to edit this page and any other page if you have valid useful information that can make other Pi users have an easier time with connecting devices for use with RetroPie.**

***

# Method 3 OLD (xwiimote):

Hi there,

while trying to associate a non official wiimote classic controller, I found this: [http://github.com/dvdhrm/xwiimote](http://github.com/dvdhrm/xwiimote).
Since recent kernel releases (including the one used by RetroPie), an optional module, ```hid-wiimote``` can be loaded using the command ```modprobe hid-wiimote```, then you use the command ```sudo hidd --search``` to find the wiimote without a pin (bluez is not good at this, asking for a pin), and in the syslog :

```
Jan 18 21:55:21 raspberrypi hidd: New HID device 00:18:00:B2:F5:35 (Nintendo RVL-CNT-01)
Jan 18 21:55:21 raspberrypi kernel: [168934.199087] wiimote 0005:057E:0306.0007: hidraw0: BLUETOOTH HID v3a.1c Gamepad [Nintendo RVL-CNT-01] on 00:1A:7D:DA:71:13
Jan 18 21:55:21 raspberrypi kernel: [168934.200264] input: Nintendo Wii Remote Accelerometer as /devices/platform/bcm2708_usb/usb1/1-1/1-1.3/1-1.3:1.0/bluetooth/hci0/hci0:71/0005:057E:0306.0007/input/input30
Jan 18 21:55:21 raspberrypi kernel: [168934.201753] input: Nintendo Wii Remote IR as /devices/platform/bcm2708_usb/usb1/1-1/1-1.3/1-1.3:1.0/bluetooth/hci0/hci0:71/0005:057E:0306.0007/input/input31
Jan 18 21:55:21 raspberrypi kernel: [168934.213406] input: Nintendo Wii Remote as /devices/platform/bcm2708_usb/usb1/1-1/1-1.3/1-1.3:1.0/bluetooth/hci0/hci0:71/0005:057E:0306.0007/input/input32
Jan 18 21:55:22 raspberrypi kernel: [168935.216422] input: Nintendo Wii Remote Extension as /devices/platform/bcm2708_usb/usb1/1-1/1-1.3/1-1.3:1.0/bluetooth/hci0/hci0:71/0005:057E:0306.0007/input/input33
Jan 18 21:55:22 raspberrypi kernel: [168935.223466] input: Nintendo Wii Remote Motion+ as /devices/platform/bcm2708_usb/usb1/1-1/1-1.3/1-1.3:1.0/bluetooth/hci0/hci0:71/0005:057E:0306.0007/input/input34
Jan 18 21:55:22 raspberrypi kernel: [168935.224051] wiimote 0005:057E:0306.0007: New device registered
```

You can run a test with ```evtest``` or ```xwiishow```.

Please note [this comment](https://github.com/retropie/RetroPie-Setup/issues/256#issuecomment-32708108):

> Actually, the hid-wiimote included in 3.6.y kernel is buggy.
> See below the 2 patches I used (over [https://github.com/raspberrypi/linux/tree/rpi-3.6.y](https://github.com/raspberrypi/linux/tree/rpi-3.6.y)).
> But to make the classic controller work with my remote (http://www.thinkgeek.com/product/f3a7/), I had to force ext as WIICLASSIC, so it's a bit hacky for this part; the rest is only bug fix (from 3.11 version) / adaptation to be working with RetroArch (D-Pad).
> 
> Also, while a simple `hidd --search` handle the connection, it doesn't handle the Wii leds numerotation. I'll try to write a script that continuously search for specified Wiimote (or all) and set the right leds.


   * **raspberrypi-linux-3.6 - Force WIICLASSIC ext, fix Classic controls - 194ccc5 over 2a8d45e**
		
		 From 194ccc578a5a9a53c96ab4099e8a9365f29dcdfd Mon Sep 17 00:00:00 2001
		 From: "Alexandre L."
		 Date: Sun, 19 Jan 2014 14:11:16 +0100
		 Subject: [PATCH] Force WIICLASSIC ext, fix Classic controls
		 
		 -Force WIICLASSIC ext (because this version fails to detect it or my non official remote fails to report it ?)
		 -Fix classic controls (ly, rx, button invert ..) : fixed in 3.11
		 -Remove HAT3 : because it's useless
		 -Fix D-Pad input, because it's not detected in RetroArch when mapped as KEY_UP/... = BTN_0123
		 ---
		  drivers/hid/hid-wiimote-ext.c | 70 ++++++++++++++++++++---------------
		  1 file changed, 40 insertions(+), 30 deletions(-)
		 
		 diff --git a/drivers/hid/hid-wiimote-ext.c b/drivers/hid/hid-wiimote-ext.c
		 index 0a1805c9b0e52..262369f7318f0 100644
		 --- a/drivers/hid/hid-wiimote-ext.c
		 +++ b/drivers/hid/hid-wiimote-ext.c
		 @@ -69,10 +69,10 @@ static __u16 wiiext_keymap[] = {
		  	KEY_NEXT,	/* WIIEXT_KEY_PLUS */
		  	KEY_PREVIOUS,	/* WIIEXT_KEY_MINUS */
		  	BTN_MODE,	/* WIIEXT_KEY_HOME */
		 -	KEY_LEFT,	/* WIIEXT_KEY_LEFT */
		 -	KEY_RIGHT,	/* WIIEXT_KEY_RIGHT */
		 -	KEY_UP,		/* WIIEXT_KEY_UP */
		 -	KEY_DOWN,	/* WIIEXT_KEY_DOWN */
		 +	BTN_0,	/* WIIEXT_KEY_LEFT */
		 +	BTN_1,	/* WIIEXT_KEY_RIGHT */
		 +	BTN_2,		/* WIIEXT_KEY_UP */
		 +	BTN_3,	/* WIIEXT_KEY_DOWN */
		  	BTN_TL,		/* WIIEXT_KEY_LT */
		  	BTN_TR,		/* WIIEXT_KEY_RT */
		  };
		 @@ -101,6 +101,9 @@ static bool motionp_read(struct wiimote_ext *ext)
		  	ssize_t ret;
		  	bool avail = false;
		  
		 +	// Don't want to enable MotionPlus (if any)
		 +	return false;
		 +
		  	if (!atomic_read(&ext-mp_opened))
		  		return false;
		  
		 @@ -128,6 +131,12 @@ static __u8 ext_read(struct wiimote_ext *ext)
		  	ssize_t ret;
		  	__u8 rmem[2], wmem;
		  	__u8 type = WIIEXT_NONE;
		 +  
		 +  wmem = 0x55;
		 +  wiimote_cmd_write(ext-wdata, 0xa400f0, &wmem, sizeof(wmem));
		 +  wmem = 0x0;
		 +  wiimote_cmd_write(ext-wdata, 0xa400fb, &wmem, sizeof(wmem));
		 +  return WIIEXT_CLASSIC;
		  
		  	if (!ext-plugged || !atomic_read(&ext-opened))
		  		return WIIEXT_NONE;
		 @@ -197,6 +206,7 @@ static void wiiext_worker(struct work_struct *work)
		  
		  	ext_disable(ext);
		  	motionp = motionp_read(ext);
		 +	motionp = false;
		  	ext_type = ext_read(ext);
		  	ext_enable(ext, motionp, ext_type);
		  }
		 @@ -440,13 +450,13 @@ static void handler_classic(struct wiimote_ext *ext, const __u8 *payload)
		  
		  	if (ext-motionp) {
		  		lx = payload[0] & 0x3e;
		 -		ly = payload[0] & 0x3e;
		 +		ly = payload[1] & 0x3e;
		  	} else {
		  		lx = payload[0] & 0x3f;
		 -		ly = payload[0] & 0x3f;
		 +		ly = payload[1] & 0x3f;
		  	}
		  
		 -	rx = (payload[0]  3) & 0x14;
		 +	rx = (payload[0]  3) & 0x18;
		  	rx |= (payload[1]  5) & 0x06;
		  	rx |= (payload[2]  7) & 0x01;
		  	ry = payload[2] & 0x1f;
		 @@ -464,46 +474,46 @@ static void handler_classic(struct wiimote_ext *ext, const __u8 *payload)
		  	input_report_abs(ext-input, ABS_HAT1Y, ly - 0x20);
		  	input_report_abs(ext-input, ABS_HAT2X, rx - 0x20);
		  	input_report_abs(ext-input, ABS_HAT2Y, ry - 0x20);
		 -	input_report_abs(ext-input, ABS_HAT3X, rt - 0x20);
		 -	input_report_abs(ext-input, ABS_HAT3Y, lt - 0x20);
		 +	//input_report_abs(ext-input, ABS_HAT3X, rt - 0x20);
		 +	//input_report_abs(ext-input, ABS_HAT3Y, lt - 0x20);
		  
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_RIGHT],
		 -							!!(payload[4] & 0x80));
		 +							!(payload[4] & 0x80));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_DOWN],
		 -							!!(payload[4] & 0x40));
		 +							!(payload[4] & 0x40));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_LT],
		 -							!!(payload[4] & 0x20));
		 +							!(payload[4] & 0x20));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_MINUS],
		 -							!!(payload[4] & 0x10));
		 +							!(payload[4] & 0x10));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_HOME],
		 -							!!(payload[4] & 0x08));
		 +							!(payload[4] & 0x08));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_PLUS],
		 -							!!(payload[4] & 0x04));
		 +							!(payload[4] & 0x04));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_RT],
		 -							!!(payload[4] & 0x02));
		 +							!(payload[4] & 0x02));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_ZL],
		 -							!!(payload[5] & 0x80));
		 +							!(payload[5] & 0x80));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_B],
		 -							!!(payload[5] & 0x40));
		 +							!(payload[5] & 0x40));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_Y],
		 -							!!(payload[5] & 0x20));
		 +							!(payload[5] & 0x20));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_A],
		 -							!!(payload[5] & 0x10));
		 +							!(payload[5] & 0x10));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_X],
		 -							!!(payload[5] & 0x08));
		 +							!(payload[5] & 0x08));
		  	input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_ZR],
		 -							!!(payload[5] & 0x04));
		 +							!(payload[5] & 0x04));
		  
		  	if (ext-motionp) {
		  		input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_UP],
		 -							!!(payload[0] & 0x01));
		 +							!(payload[0] & 0x01));
		  		input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_LEFT],
		 -							!!(payload[1] & 0x01));
		 +							!(payload[1] & 0x01));
		  	} else {
		  		input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_UP],
		 -							!!(payload[5] & 0x01));
		 +							!(payload[5] & 0x01));
		  		input_report_key(ext-input, wiiext_keymap[WIIEXT_KEY_LEFT],
		 -							!!(payload[5] & 0x02));
		 +							!(payload[5] & 0x02));
		  	}
		  
		  	input_sync(ext-input);
		 @@ -650,16 +660,16 @@ int wiiext_init(struct wiimote_data *wdata)
		  	set_bit(ABS_HAT1Y, ext-input-absbit);
		  	set_bit(ABS_HAT2X, ext-input-absbit);
		  	set_bit(ABS_HAT2Y, ext-input-absbit);
		 -	set_bit(ABS_HAT3X, ext-input-absbit);
		 -	set_bit(ABS_HAT3Y, ext-input-absbit);
		 +	//set_bit(ABS_HAT3X, ext-input-absbit);
		 +	//set_bit(ABS_HAT3Y, ext-input-absbit);
		  	input_set_abs_params(ext-input, ABS_HAT0X, -120, 120, 2, 4);
		  	input_set_abs_params(ext-input, ABS_HAT0Y, -120, 120, 2, 4);
		  	input_set_abs_params(ext-input, ABS_HAT1X, -30, 30, 1, 1);
		  	input_set_abs_params(ext-input, ABS_HAT1Y, -30, 30, 1, 1);
		  	input_set_abs_params(ext-input, ABS_HAT2X, -30, 30, 1, 1);
		  	input_set_abs_params(ext-input, ABS_HAT2Y, -30, 30, 1, 1);
		 -	input_set_abs_params(ext-input, ABS_HAT3X, -30, 30, 1, 1);
		 -	input_set_abs_params(ext-input, ABS_HAT3Y, -30, 30, 1, 1);
		 +	//input_set_abs_params(ext-input, ABS_HAT3X, -30, 30, 1, 1);
		 +	//input_set_abs_params(ext-input, ABS_HAT3Y, -30, 30, 1, 1);
		  	set_bit(ABS_RX, ext-input-absbit);
		  	set_bit(ABS_RY, ext-input-absbit);
		  	set_bit(ABS_RZ, ext-input-absbit);

   * **raspberrypi-linux-3.6 - Disable power_supply device in sysfs - ade5a71 over 2a8d45e**

		 From ade5a7138871bf73326f4f92d8c7cc5249656307 Mon Sep 17 00:00:00 2001
		 From: "Alexandre L."
		 Date: Sun, 19 Jan 2014 14:06:10 +0100
		 Subject: [PATCH] Disable power_supply device in sysfs
		 
		 Disable power_supply device in sysfs, because it fails when you try associating 2 remotes (fixed in 3.11 version).
		 ---
		  drivers/hid/hid-wiimote-core.c | 8 +++++---
		  1 file changed, 5 insertions(+), 3 deletions(-)
		 
		 diff --git a/drivers/hid/hid-wiimote-core.c b/drivers/hid/hid-wiimote-core.c
		 index 84e2fbec5fbb8..03adecd98c111 100644
		 --- a/drivers/hid/hid-wiimote-core.c
		 +++ b/drivers/hid/hid-wiimote-core.c
		 @@ -17,7 +17,7 @@
		  #include <linux/leds.h
		  #include <linux/module.h
		  #include <linux/mutex.h
		 -#include <linux/power_supply.h
		 +//#include <linux/power_supply.h
		  #include <linux/spinlock.h
		  #include "hid-ids.h"
		  #include "hid-wiimote.h"
		 @@ -1159,7 +1159,7 @@ static void wiimote_destroy(struct wiimote_data *wdata)
		  	wiiext_deinit(wdata);
		  	wiimote_leds_destroy(wdata);
		  
		 -	power_supply_unregister(&wdata-battery);
		 +	//power_supply_unregister(&wdata-battery);
		  	input_unregister_device(wdata-accel);
		  	input_unregister_device(wdata-ir);
		  	input_unregister_device(wdata-input);
		 @@ -1220,13 +1220,15 @@ static int wiimote_hid_probe(struct hid_device *hdev,
		  	wdata-battery.type = POWER_SUPPLY_TYPE_BATTERY;
		  	wdata-battery.use_for_apm = 0;
		  
		 -	ret = power_supply_register(&wdata-hdev-dev, &wdata-battery);
		 +	/*
		 +  ret = power_supply_register(&wdata-hdev-dev, &wdata-battery);
		  	if (ret) {
		  		hid_err(hdev, "Cannot register battery device\n");
		  		goto err_battery;
		  	}
		  
		  	power_supply_powers(&wdata-battery, &hdev-dev);
		 +  */
		  
		  	ret = wiimote_leds_create(wdata);
		  	if (ret)


