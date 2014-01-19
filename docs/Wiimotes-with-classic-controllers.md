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
sudo apt-get install bluetooth 
sudo apt-get install python-cwiid 
sudo apt-get install wminput
```

### Getting the wiimotes to work

uinput device needs to work with non-root users. To do so, create a file called /etc/udev/rules.d/wiimote.rules with the following line:
```shell
KERNEL==“uinput“, MODE:=“0666“
```

Reboot the Raspberry Pi to make this change active.

Check that the blue-tooth dongle works: Command
```shell
/etc/init.d/bluetooth status
```
should return that bluetooth is working. 

Scan for the wiimotes. Start
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
Wiimote.Dpad.X		= -ABS_Y
Wiimote.Dpad.Y		= ABS_X
Wiimote.Minus	= BTN_SELECT
Wiimote.Plus	= BTN_START
Wiimote.Home	= BTN_MODE
Wiimote.1		= BTN_X
Wiimote.2		= BTN_Y
```

If the Raspberry Pi is started and emulationstation starts, we want to register the wiimotes so they can be used with emulationstation and the emulators.
I did it the following way:
```shell
mkdir /home/pi/bin
```
create file /home/pi/bin/attachwii.sh with the following content:
```shell
#!/bin/bash
hcitool dev | grep hci >/dev/null
if test $? -eq 0 ; then
	wminput -d -c  /home/pi/mywminput 00:19:1D:92:90:38 &
	wminput -d -c  /home/pi/mywminput 00:19:1D:84:EF:33 &
else
	echo "Blue-tooth adapter not present!"
fi
```

Note: You need one wminput line for every wiimote you want to use (i.e. the above is for two wiimotes)
Note 2: You need to replace the addresses of the wiimotes above by the addresses of your wiimotes (shown by command „hcitool scan“ as shown above).  
make the script executable with
```shell
chmod 775 /home/pi/bin/attachwii.sh
```
have the script be started just before emulationstation starts. To do so, edit the file /etc/profile
The last line should be
```shell
[ -n "${SSH_CONNECTION}" ] || emulationstation
```
right before this line, add the line
```shell
/home/pi/bin/attachwii.sh
```
and save the file.

If you now do a reboot, wait until emulationstation has been started. When it did, press 1+2 on all of your wiimotes to register the wiimotes. Now you can „tell“ emulationstation and the emulators to use the wiimotes (and the classic controllers). Here are my configuration files.
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
</inputList>`
```

For retroarch:
End of file /home/pi/RetroPi/configs/all/retroarch.cfg (for two wiimotes):
```shell
input_player1_joypad_index = "0"
input_player1_b_btn = "0"
input_player1_y_btn = "2"
input_player1_select_btn = "8"
input_player1_start_btn = "9"
input_player1_up_axis = "+1"
input_player1_down_axis = "-1"
input_player1_left_axis = "-0"
input_player1_right_axis = "+0"
input_player1_a_btn = "1"
input_player1_x_btn = "3"
input_player1_l_btn = "4"
input_player1_r_btn = "5"
input_player1_l2_btn = "6"
input_player1_r2_btn = "7"
input_player1_l3_btn = "10"
input_player1_r3_btn = "10"
input_player1_l_x_plus_axis = "+2"
input_player1_l_x_minus_axis = "-2"
input_player1_l_y_plus_axis = "-3"
input_player1_l_y_minus_axis = "+3"
input_player1_r_x_plus_axis = "+4"
input_player1_r_x_minus_axis = "-4"
input_player1_r_y_plus_axis = "-5"
input_player1_r_y_minus_axis = "+5"
input_player2_joypad_index = "1"
input_player2_b_btn = "1"
input_player2_y_btn = "3"
input_player2_select_btn = "8"
input_player2_start_btn = "9"
input_player2_up_axis = "+1"
input_player2_down_axis = "-1"
input_player2_left_axis = "-0"
input_player2_right_axis = "+0"
input_player2_a_btn = "0"
input_player2_x_btn = "2"
input_player2_l_btn = "4"
input_player2_r_btn = "5"
input_player2_l2_btn = "6"
input_player2_r2_btn = "7"
input_player2_l3_btn = "10"
input_player2_r3_btn = "10"
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

Finally, add the following two lines at the end of /home/pi/RetroPi/configs/all/retroarch.cfg:
```shell
input_enable_hotkey_btn = "0"
input_exit_emulator_btn = "1"
```

This will exit the emulator when you press A+B simultaneously on the wiimote (or the classic controller).

Note: the config files above work for wiimotes with or without classic controller.
Note 2: If you want to use the wiimote (i.e. not only the classic controller) and you are using my config files, you need to hold the wiimote horizontally (with the power button on the right).