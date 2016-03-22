## Method 1:

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

Please note [this comment](https://github.com/petrockblog/RetroPie-Setup/issues/256#issuecomment-32708108):

Actually, the hid-wiimote included in 3.6.y kernel is buggy.
Here's the version I use: [https://github.com/Alex131089/raspberrypi-linux/compare/raspberrypi:rpi-3.6.y...rpi-3.6.y-hid-wiimote](https://github.com/Alex131089/raspberrypi-linux/compare/raspberrypi:rpi-3.6.y...rpi-3.6.y-hid-wiimote)

But to make the classic controller work with my remote, [http://www.thinkgeek.com/product/f3a7/](http://www.thinkgeek.com/product/f3a7/), I had to force ext as WIICLASSIC, so it's a bit hacky for this part ; the rest is only bug fix (from 3.11 version) / adaptation to be working with RetroArch (D-Pad).

Also, while a simple ```hidd --search``` handles the connection, it doesn't handle the Wii leds enumeration, I'll try to write a script that continuously search for specified Wiimote (or all) and set the right leds.

## Method 2:

The basis of this setup was taken from [here](http://blog.petrockblock.com/forums/topic/tutorial-to-get-wiimotes-with-classic-controllers-to-work-with-retropie/). It has however been slightly updated and modified to work with the current version of retropie (3.6). 

This tutorial shows how to get one to four wiimotes (the controller of Nintendo Wii) running with RetroPie with or without a classic controller (attached to the wiimote).

### Prerequisites

1. For the following I assume that RetroPi was installed and is running with other controls (like keyboard, joystick etc.). I followed the excellent tutorial http://supernintendopi.wordpress.com/2013/01/23/an-a-to-z-beginners-guide-to-installing-retropie-on-a-raspberry-pi/  for this (using the “RetroPie Project SD Card Image”).

2. You have a blue-tooth dongle (sometimes called blue-tooth adapter). For a list of dongles known to work with Raspberry Pi see http://elinux.org/RPi_USB_Bluetooth_adapters#Working_Bluetooth_adapters ).

Note: Put the dongle in one of the USB ports of the Raspberry Pi directly, don't put it into a USB hub (I read somewhere that it doesn't work even with an active USB hub).

*Note 2: I can now confirm putting the bluetooth adapter into a usb 2.0 powered hub works. Your results may vary though depending on your hardware.      

Its important to update retropie to the latest version to avoid problems later down in the tutorial. Type the following into the command line:

```shell
cd RetroPie-Setup/
```
In this folder, we will load up the retropie post install script:
```shell
 sudo ./retropie_setup.sh
```
In the menu, choose to update the RetroPie-Setup script (option U) first. The pi will connect to the internet and fetch the latest version. After that's done, choose Binary-based installation (option 1). Depending on your pi version, this can take a while. On a pi zero, it too about 30 minutes.  

### Installation

Now install the needed parts:
```shell
sudo apt-get install bluetooth vorbis-tools python-cwiid wminput
```

### Getting the wiimotes to work

uinput device needs to work with non-root users. To do so, create a wiimote rule file using your text editor of choice ( I use nano) as a root user (using `sudo`):

```shell
sudo nano /etc/udev/rules.d/wiimote.rules
```
and paste the text below into it:
```shell
KERNEL=="uinput", MODE="0666"

```

That's the rule implementation done. Save the text file with CTRL + X and press Y to confirm. To make this change active, reboot the Raspberry Pi, or paste this command at the command line:
```shell
sudo service udev restart
```

Check that the blue-tooth dongle works with the command below:
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
nano /home/pi/mywminput
```
and paste the following contents:
```shell
# Classic-Controller
Classic.Dpad.X = ABS_X
Classic.Dpad.Y = ABS_Y
Classic.LStick.X = ABS_HAT0X
Classic.LStick.Y = ABS_HAT0Y
Classic.RStick.X = ABS_HAT1X
Classic.RStick.Y = ABS_HAT1Y
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
```

If you want your WiiMotes giving a connection status, just add an additional line to your `mywminput` file:
```shell
Plugin.led.Led1 = 1
#Plugin.led.Led2 = 1
#Plugin.led.Led3 = 1
#Plugin.led.Led4 = 1
```
You probably also want different LEDs active on two controllers, which means you have to provide different `mywminput` files to wminput, e.g. `mywminputA`, `mywminputB` etc with `LED1` and another with `LED2` activated. In the above example, `LED 1` is activated and `LED's 2`, `3` and `4` are commented out. You can replace the above example with your chosen `LED` status. 

Updated Note: I've had problems using the above button layout with a classic controller. It will cause the button remapping which we will do later in emulationstation to be off. I fixed this by just copy pasting the classic controls only. (I will use the classic controller to control everything and have no intention of using the controls off the wiimote).

```shell
Classic.Dpad.X = ABS_X
Classic.Dpad.Y = ABS_Y
Classic.LStick.X = ABS_HAT0X
Classic.LStick.Y = ABS_HAT0Y
Classic.RStick.X = ABS_HAT1X
Classic.RStick.Y = ABS_HAT1Y
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


#### Quick and Dirty Wiimote Configuration

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

#### Manual Wiimote Configuration

Use this method if you want to use the same wiimotes every time and don't want to re-register the wiimotes every time you restart your Raspberrypi.

First, scan for the wiimotes. Start
```shell
hcitool scan
```
and press 1+2 on your wiimote(s). After a short while, the output should be something like
```shell
Scanning ...
	00:19:1D:87:90:38		Nintendo RVL-CNT-01
	00:19:1D:88:EF:12		Nintendo RVL-CNT-01
```

Take a note of the addresses of your wiimotes (the 00:19:1D:87:90:38 in the output above), we need that later.
Note: If the scan is not successful try it again. Sometimes you need to try it several times (I read that somewhere, but it always worked for me the first time).


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

Note: You need one wminput line for every wiimote you want to use (i.e. the above is for two wiimotes)

Note 2: You need to replace the addresses of the wiimotes above by the addresses of your wiimotes (shown by command "hcitool scan" as shown above).

Note 3: I've had more success with 2 classic controllers pairing when both are sharing the same mywminput path. Since both wiimotes are using the same "mywminput" config, the LED status on port 1 of the wiimote will light up on both wiimotes. This is fine and does not interfere with anything. I simply use the light to tell me when and if both controllers are paired successfully. That is it's only purpose. I've had less success configuring a second mywinput to the 2nd controller so the LED lights differs on the 2nd controller. 

### Register Wiimotes Before Emulationstation Starts ###

Make your wiimote detection script executable with:
```shell
chmod 775 /home/pi/bin/attachwii.sh
```

**Caution:** The next step is dependent related to the installed version of RetroPie!

#### RetroPie 2.6 and earlier ####

To start the script before emulationstation starts, edit the file: `/etc/profile`.  The last line should be
```shell
[ -n "${SSH_CONNECTION}" ] || emulationstation
```
Then, right before that line, add the line:
```shell
rebootWithoutWiimotes=0 /home/pi/bin/attachwii.sh
```
and save the file.

#### RetroPie 3.x ####

To start the script before emulationstation starts, edit the file: `/etc/profile.d/10-emulationstation.sh`.  The last line should be
```shell
[ "`tty`" = "/dev/tty1" ] && emulationstation
```
Then, right before that line, add the line:
```shell
rebootWithoutWiimotes=0 /home/pi/bin/attachwii.sh
```
and save the file.

To make the Pi restart automatically if no wiimotes are detected, change rebootWithoutWiimotes to 1.

### Register Wiimotes Before Emulationstation Starts (continue) ###

If you now do a reboot using "sudo reboot", wait until emulationstation has been started. When it does, press 1+2 on all of your wiimotes to register the wiimotes.
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

The input commands specified above, allow you to exit out the emulator when SELECT and START are pressed at the same time. Pressing SELECT enables the hoykey whilst START is assigned to exit. Pressing SELECT and the HOME button however, will enable retroarch's menu for in game adjustments. 

**DONE!**
*I highly encourage you to read the "Known Issues" section below for optional fixes:

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

Note: I actively use SSH with my retropie so I had to apply this fix so I could use my SSH terminal without being hammered with socket control errors. 
This is what my revised attachwii looks like for comparison. We created this file earlier in /home/pi/bin/attachwii.sh

```shell
#!/bin/bash
sleep 1 # Wait until Bluetooth services are fully initialized
hcitool dev | grep hci >/dev/null
if test $? -eq 0 ; then
    wminput -d -q -c  /home/pi/mywminput 00:19:1D:92:90:38 > /dev/null 2>&1 &
    wminput -d -q -c  /home/pi/mywminput 00:19:1D:84:EF:33 > /dev/null 2>&1 &
else
    echo "Blue-tooth adapter not present!"
    exit 1
fi
```

As you can see the addition of the -q is supposed to help keep wminput quiet. If you're doing troubleshooting of any kind remember to remove the `> /dev/null 2>&1 &"`. 

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

**2. My retroarch controls aren't working/messed up!**
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
