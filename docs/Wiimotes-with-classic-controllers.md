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

From [here](http://blog.petrockblock.com/forums/topic/tutorial-to-get-wiimotes-with-classic-controllers-to-work-with-retropie/):

This tutorial shows how to get one to four wiimotes (the controller of Nintendo Wii) running with RetroPie with or without a classic controller (attached to the wiimote).

### Prerequisites

1. For the following I assume that RetroPi was installed and is running with other controls (like keyboard, joystick etc.). I followed the excellent tutorial http://supernintendopi.wordpress.com/2013/01/23/an-a-to-z-beginners-guide-to-installing-retropie-on-a-raspberry-pi/  for this (using the “RetroPie Project SD Card Image”).

2. You have a blue-tooth dongle (sometimes called blue-tooth adapter). For a list of dongles known to work with Raspberry Pi see http://elinux.org/RPi_USB_Bluetooth_adapters#Working_Bluetooth_adapters ).

Note: Put the dongle in one of the USB ports of the Raspberry Pi directly, don't put it into a USB hub (I read somewhere that it doesn't work even with an active USB hub).

### Installation

Now install the needed parts:
```shell
sudo apt-get install bluetooth vorbis-tools python-cwiid wminput
```

### Getting the wiimotes to work

uinput device needs to work with non-root users. To do so, create a file as root user (using `sudo`) called `/etc/udev/rules.d/wiimote.rules` with the following line:
```shell
KERNEL=="uinput", MODE:="0666"
```

To make this change active, reboot the Raspberry Pi, or paste this command at the commandline:
```shell
sudo service udev restart
```

Check that the blue-tooth dongle works: Command
```shell
/etc/init.d/bluetooth status
```
should return that bluetooth is working.

### Correct usage of wminput

For every wiimote, we need one wminput command to map the wiimote (and the classic controller) buttons to something emulationstation and the emulators can work with. wminput comes with configuration files (in directory /etc/cwiid/wminput). I created my own configuration file, which works if you use a wiimote with or without a classic controller. Create the file /home/pi/mywminput with the following content:
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
Wiimote.A		= BTN_A
Wiimote.B		= BTN_B
Wiimote.Dpad.X		= ABS_Y
Wiimote.Dpad.Y		= -ABS_X
Wiimote.Minus	= BTN_SELECT
Wiimote.Plus	= BTN_START
Wiimote.Home	= BTN_MODE
Wiimote.1		= BTN_X
Wiimote.2		= BTN_Y
```

If you want your WiiMotes giving a connection status, just add an additional line to your `mywminput` file:

    Plugin.led.Led1 = 1

You probably also want different LEDs active on two controllers, which means you have to provide different `mywminput` files to wminput, e.g. one with `Led1` and another with `Led2` activated.

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
    aplay $begin_sound &> /dev/null &
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
                wminput -d -c /home/pi/bin/wiimote.input $id &
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
create file /home/pi/bin/attachwii.sh with the following content:
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
Note 2: You need to replace the addresses of the wiimotes above by the addresses of your wiimotes (shown by command „hcitool scan“ as shown above).  

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

#### RetroPie 3.0 ####

To start the script before emulationstation starts, edit the file: `/etc/profile.d/10-emulationstation.sh`.  The last line should be
```shell
[ "`tty`" = "/dev/tty1" ] && emulationstation
```
Then, right before that line, add the line:
```shell
rebootWithoutWiimotes=0 /home/pi/bin/attachwii.sh
```
and save the file.

### Register Wiimotes Before Emulationstation Starts (continue) ###

To make the Pi restart automatically if no wiimotes are detected, change rebootWithoutWiimotes to 1.

If you now do a reboot, wait until emulationstation has been started. When it does, press 1+2 on all of your wiimotes to register the wiimotes.

Now you can „tell“ emulationstation and the emulators to use the wiimotes (and the classic controllers). Here are my configuration files.

For emulationstation:
Content of /home/pi/.emulationstation/es_input.cfg for two wiimotes:
```shell
<?xml version="1.0"?>
<inputList>
	<inputConfig type="joystick" deviceName="Nintendo Wiimote">
		<input name="a" type="button" id="0" value="1" />
		<input name="b" type="button" id="1" value="1" />
		<input name="down" type="axis" id="1" value="-1" />
		<input name="left" type="axis" id="0" value="-1" />
		<input name="menu" type="button" id="2" value="1" />
		<input name="pagedown" type="button" id="4" value="1" />
		<input name="pageup" type="button" id="5" value="1" />
		<input name="right" type="axis" id="0" value="1" />
		<input name="select" type="button" id="3" value="1" />
		<input name="up" type="axis" id="1" value="1" />
	</inputConfig>
	<inputConfig type="joystick" deviceName="Nintendo Wiimote">
		<input name="a" type="button" id="0" value="1" />
		<input name="b" type="button" id="1" value="1" />
		<input name="down" type="axis" id="1" value="-1" />
		<input name="left" type="axis" id="0" value="-1" />
		<input name="menu" type="button" id="2" value="1" />
		<input name="pagedown" type="button" id="4" value="1" />
		<input name="pageup" type="button" id="5" value="1" />
		<input name="right" type="axis" id="0" value="1" />
		<input name="select" type="button" id="3" value="1" />
		<input name="up" type="axis" id="1" value="1" />
	</inputConfig>
	<inputConfig type="keyboard">
		<input name="a" type="key" id="13" value="1" />
		<input name="b" type="key" id="8" value="1" />
		<input name="down" type="key" id="274" value="1" />
		<input name="left" type="key" id="276" value="1" />
		<input name="menu" type="key" id="32" value="1" />
		<input name="right" type="key" id="275" value="1" />
		<input name="up" type="key" id="273" value="1" />
	</inputConfig>
</inputList>
```

For retroarch:
End of file /opt/retropie/emulators/retroarch/retroarch.cfg (for two wiimotes):
```shell
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

Make sure that the settings are only one time in retroarch.cfg file (i.e. if you have a line 
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

Finally, add the following four lines at the end of `/opt/retropie/configs/all/retroarch.cfg`:
```shell
savestate_auto_save = true
savestate_auto_load = true
input_enable_hotkey_btn = "8"
input_exit_emulator_btn = "9"
input_menu_toggle_btn = "10"
```

This will open the menu when you press the Home key and exit the emulator when you press Select and Start simultaneously on the wiimote (or the classic controller).  When you quit a game through this method, your game state will be saved and reloaded.

Note: the config files above work for wiimotes with or without classic controller.
Note 2: If you want to use the wiimote (i.e. not only the classic controller) and you are using my config files, you need to hold the wiimote horizontally (with the power button on the left).