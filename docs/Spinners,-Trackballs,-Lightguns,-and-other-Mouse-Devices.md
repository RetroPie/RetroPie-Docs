## Overview
Spinners and Trackballs appear on the control panels of many arcade classics. Lightguns were common accessories for both arcade and console games. Although RetroPie is often able to accommodate the use of a joystick instead, _many_ popular titles are best played with their native controls.

Spinners, Trackballs, and Lightguns are often described together because they are seen as mouse devices by the operating system. Spinners operate by rotating a spindle which turns an encoder wheel. Optical sensors detect the movement of the encoder wheel and forward the speed and rotational direction to the arcade game. Trackballs are essentially the same but they have two spindles oriented perpendicular to one another. By rolling a ball that is in direct contact with the spindles, trackballs can provide two-dimensional input like a mouse. In this respect, a spinner is also like a mouse that only moves in a straight line (left/right or up/down).

## Hardware for Emulators
Because mouse input is ubiquitous on modern computers, spinners and trackballs translate nicely to emulators that can accept input from a mouse. For trackballs, the input is practically identical to a mouse. Spinners can also be setup like a mouse with separate X and Y tracking (like an Etch-a-Sketch).

Adding a USB mouse to a Raspberry Pi is trivial. Attaching a trackball or spinners requires a USB interface. Fortunately, arcade hardware is available that will work, and often comes with (or is compatible with) a USB interface. There are several options available from Ultimarc, Groovy Game Gear, Happ, and others. The key to making this hardware work on the Raspberry Pi is to ensure that the interface behaves like a USB mouse.

### Testing Mouse Inputs in Linux
A convenient hardware test is to simply boot the Pi to a desktop and see if you can move the cursor with your trackball or spinner. This can also help you troubleshoot the connections for X and Y inputs. If you have movement, you should be able to configure MAME to use it.

Another test can be performed at the command prompt. Type:`cat /dev/input/mice` and press enter. Now, rotate your spinner or move your trackball. It should produce characters on the screen and move the cursor from side to side on the line. Depending on other devices you have attached, Linux might see more than one USB mouse at the same time. You can determine which one is your spinner or trackball by trying each device individually using `cat /dev/input/mouse0` or `cat /dev/input/mouse1` and so on.

### Configuring RetroArch emulators for mouse-like device use

**Input Drivers**: As of September 2017, there is only one RetroArch input driver for Linux with support for multi-mouse: `udev`.

#### Determining mice index numbers

* Make sure that your RetroArch input driver is set to `udev` (default in RetroPie)
* Start a RetroArch emulator with the option `--verbose` to generate a detailed log. Verbose mode is selected via [Runcommand launch menu](https://retropie.org.uk/docs/Runcommand/#launch-with-verbose-logging)
* The resulting log is saved to `/dev/shm/runcommand.log`

There should be a section of the log similar to this (RetroArch ver. 1.9.6 and later)
```
[INFO] [udev]: Added Device Keyboard#0 G.SKILL Corporation G.SKILL RIPJAWS KM780 MX GAMING KEYBOARD (/dev/input/event8) .
[INFO] [udev]: Added Device Keyboard#1 G.SKILL Corporation G.SKILL RIPJAWS KM780 MX GAMING KEYBOARD (/dev/input/event13) .
[INFO] [udev]: Added Device Keyboard#2 USB Laser Game Mouse (/dev/input/event15) .
[INFO] [udev]: Added Device Keyboard#3 Valve Software Steam Controller (/dev/input/event18) .
[INFO] [udev]: Added Device Keyboard#4  (/dev/input/mouse3) .
[INFO] [udev]: Added Device Keyboard#5 AT Translated Set 2 keyboard (/dev/input/event4) .
[INFO] [udev]: Added Device mouse#0 G.SKILL Corporation G.SKILL RIPJAWS KM780 MX GAMING KEYBOARD (/dev/input/event9) .
[INFO] [udev]: Added Device mouse#1 USB Laser Game Mouse (/dev/input/event14) .
[INFO] [udev]: Added Device mouse#2 Valve Software Steam Controller (/dev/input/event18) .
[INFO] [udev]: Added Device mouse#3 DELL0802:00 06CB:7E92 Mouse (/dev/input/event30) .
[INFO] [udev]: Added Device mouse#4 DELL0802:00 06CB:7E92 Touchpad (/dev/input/event31) .
[INFO] [udev]: Added Device mouse#5 SynPS/2 Synaptics TouchPad (/dev/input/event7) .
```
or this (RetroArch ver. 1.9.5 or earlier)
```
[INFO] [udev] Adding device /dev/input/event1 as type ID_INPUT_MOUSE.
[INFO] [udev] Adding device /dev/input/mouse0 as type ID_INPUT_MOUSE.
[INFO] [udev] Adding device /dev/input/event2 as type ID_INPUT_MOUSE.
[INFO] [udev] Adding device /dev/input/mouse1 as type ID_INPUT_MOUSE.
```

**Interpretation**: Look for the `/dev/input/event*` indexes. In the examples above there are mouselike devices at indexes `0`, `1`, `2`, `3,` `4`, and `5` (first example log) and `0`, and `2` (second example log).

**Beware**: The index of a specific device may change depending on what device you have attached to which port. For example, if you boot with an external mouse, it might be detected by `udev` as `mouse#0` and your spinner as `mouse#1`, but if you boot the same system without the external mouse attached, everything might ratchet down (spinner becomes `mouse#0`).

#### Setting mouse indexes via the RetroArch GUI

For each user and mouse you wish to configure, visit the corresponding RetroArch user 'binds' screen and set `Mouse Index` to match the indexes discovered earlier.

#### Setting mouse indexes via retroarch.cfg

As an alternative to using the RetroArch GUI to set the mouse indexes, you can map mice to users via the `retroarch.cfg` in this format: `input_player1_mouse_index = "0"`

## Configuring Emulators
Not all emulators support mouse input. Fortunately, software evolves as developers add more functionality. The two MAME emulators that offer the best mouse support for arcade games in RetroPie are lr-mame2003 and AdvanceMAME.

### lr-mame2003
As of August 4, 2016, [mame2003-libretro](https://github.com/libretro/mame2003-libretro) has been capable of trackball and spinner support. Following the steps above for RetroArch mouse support, it is even possible to adjust the mouse index to get multiple mouse devices working for different players. Index settings may be necessary even for single player functionality, depending on the mouse devices detected on your system. Once configured, the Player 1 DIAL control (spinner, steering, etc.) receives input from the X-axis of the mouse device, and TRACKBALL inputs come from both X and Y. For two-player spinner control where the spinners share a single mouse device (together comprising both X and Y axes), an additional core option allows you to split the player 1 mouse device into two players.

If your spinner rotates in the wrong direction (e.g. happens with Spintrak with own dedicated USB interface) you need to enter the Mame menu (thru TAB on your keyboard) and reverse the direction in the Analog input options.

If you enable a core option ([described here](lr-mame2003#2-player-dialspinner-devices)), it is possible to share the mouse input to effectively copy the Y axis to the Player 2 DIAL control. This makes sense, as most interfaces are for either trackballs or two spinners. 

This flexibility is sufficient for most games, but there are exceptions on complex control panels. If you need to map multiple trackballs, or your Player 1 and Player 2 spinners are on different mouse inputs, you will need to assign the indices accordingly following the details above or use AdvanceMAME to map your devices to the proper controls.

### AdvanceMAME
AdvanceMAME offers the most versatility when it comes to trackball and spinner controls. Using the configuration file, You can exert very granular control to override the setup for specific games, or just configure your default settings for all games. This section describes important configuration steps necessary to enable mouse inputs in AdvanceMAME. Unfortunately AdvanceMAME does not support absolute pointing devices such as used in many light guns (e.g. the mayflash dolphin bar).

#### AdvanceMAME Mouse Input Testing
If you were successful with the Linux tests above, you might be able to skip this step, as the configuration below is flexible enough for most situations. However, if you plan to configure multiple input devices, it can be helpful to know how AdvanceMAME will see them. Like the Linux test above, AdvanceMAME has its own mouse testing command that allows you to see which mouse is controlling which axis. At a command prompt, type this: `/opt/retropie/emulators/advmame-1.4/bin/advm` and press ENTER. You will see output like this:
```
Driver event, mouses 2
mouse 0, axes 3, buttons 3
	axe 0 [x]
	axe 1 [y]
	axe 2 [z]
	button 0 [left]
	button 1 [right]
	button 2 [middle]
mouse 1, axes 3, buttons 3
	axe 0 [x]
	axe 1 [y]
	axe 2 [wheel]
	button 0 [left]
	button 1 [right]
	button 2 [middle]

Press Break to exit
mouse 0, [---], [     0,     0,     0]
``` 
In this example AdvanceMAME is detecting two mice, (mouse 0 and mouse 1) each with three axes (x,y,z) and three buttons. As you move your mouse controls you will see rows appear:
```
mouse 0, [---], [     0,     0,     0]
mouse 1, [---], [     0,     1,     0] (   1 ms)
mouse 0, [---], [     0,     0,     0]
mouse 1, [---], [     0,     2,     0] (   1 ms)
mouse 0, [---], [     0,     0,     0]
mouse 1, [---], [     0,     0,     0] (   1 ms)
```
You can press CONTROL-C to exit the test. In this example, moving the second spinner is being picked up as mouse 1, y-axis. No movement is registered as 0 input, while movement in one direction or another will show up as positive and negative numbers. This type of feedback can be very handy, as it tells you the index number and the axis of a specific controller _from MAME's perspective_. Just keep in mind, if you attach another external mouse later, it might change which mouse is detected as mouse 0, etc., and your configurations below may need to be adjusted.

### Configuring RAW, PS2 for all possible mouse inputs

**Beware**: The index of a specific device may change depending on what device you have attached to which port. For example, if you boot with an external mouse, it might be detected by `udev` as `event0` and your spinner as `event1`, but if you boot the same system without the external mouse attached, everything might ratchet down (spinner becomes `event0`). As long as you aren't changing your hardware configuration everything should stay where it is, but if you routinely connect an external mouse to troubleshoot or launch the desktop, this can be frustrating. We can overcome it by mapping multiple inputs _together_ in AdvanceMAME or by using a persistent device path, both methods shown below.

To overcome the problem with an inconsistent device index, you can use the `/dev/input/by-id/` device symlinks set for each `/dev/input/mouse<X>` device file. For instance, given the mouse device `/dev/input/mouse1`, find out the correspoding symlink by running:  
```
udevadm info /dev/input/mouse1 | grep S:
```
Look for the line containing the `/dev/input/by-id` symlink:
```
S: input/by-id/usb-1241_1111-mouse
```
You can then can substitute `/dev/input/mouse1` with `/dev/input/by-id/usb-1241_1111-mouse` in AdvanceMAME's configuration file wherever you need to set the mouse device path.  
Depending on the device type and vendor/model, the will be different than in the example above.

For starters, we need to enable all possible mouse inputs in the configuration file (we will edit the configuration for AdvanceMAME 1.4, but if you use multiple versions of AdvanceMAME, you need to make edits in each respective config).

Find these lines in `/opt/retropie/configs/mame-advancemame/advmame-1.4.rc` and update them as shown:
```
device_mouse raw
device_raw_mousedev[0] /dev/input/mouse0
device_raw_mousedev[1] /dev/input/mouse1
device_raw_mousedev[2] /dev/input/mouse2
device_raw_mousedev[3] /dev/input/mouse3
device_raw_mousetype[0] ps2
device_raw_mousetype[1] ps2
device_raw_mousetype[2] ps2
device_raw_mousetype[3] ps2
```
This establishes 4 different mouse inputs which is probably more than most people will need.

### Mapping Specific Controls
The following configurations can depend on your hardware setup. You can make adjustments as needed, especially if you have multiple inputs you are trying to configure. Note that you cannot make the mapping selections inside the MAME GUI. Even a properly configured mouse input may not look correct inside the MAME menus even though it works. To setup the proper mapping, you need to edit the configuration again in `/opt/retropie/configs/mame-advancemame/advmame-1.4.rc`.

#### Trackball
Since most trackball games will be emulated in AdvanceMAME using Player1, configure these lines as follows:
```
input_map[p1_trackballx] mouse[0,x] mouse[1,x] mouse[2,x] mouse[3,x]
input_map[p1_trackbally] mouse[0,y] mouse[1,y] mouse[2,y] mouse[3,y]
```
This tells MAME to map the Player 1 Trackball to the X and Y inputs for all four of our possible mouse inputs. We are covering all possibilities here so if the mouse indexes change (maybe you boot up with an external mouse attached and next time you don't) it won't affect the gameplay. Basicially, all attached mouse inputs will map to the game input.

#### Spinner
One spinner will send input on either X or Y for a given mouse. Assuming you have yours connected to the X axis of your interface, configure this line:
```
input_map[p1_dialx] mouse[0,x] mouse[1,x] mouse[2,x] mouse[3,x]
```
Here again, we are covering the possibilities. No matter how Linux and MAME are indexing your mouse devices, the x-axis of all four should map to the game.

If it doesn't work, and you know you have functioning inputs (see tests above) you might have your spinner on the y-axis. You could switch the hardware connection or change the input map to
```input_map[p1_dialx] mouse[0,y] mouse[1,y] mouse[2,y] mouse[3,y]```

You might also find that your spinner rotates in the wrong direction. You can fix that too with a minus sign as follows:
```input_map[p1_trackballx] -mouse[0,x] -mouse[1,x] -mouse[2,x] -mouse[3,x]```

There are many possibile combinations if you have more than one input device. Here's an example for two spinners, both connected to the same USB interface, but the Player 2 spins backwards. So. . .
```
input_map[p1_dialx] mouse[0,x]
input_map[p2_dialx] -mouse[0,y]
```
Notice that from MAME's perspective, both DIAL inputs use the x-axis, but we are using two spinners on the same USB interface, so player 1 of our "mouse0" is x and player 2 is on y. As you can see, AdvanceMAME can handle this easily. Also note that we are not mapping mouse1, 2, 3. On this arcade cabinet we have a dedicated trackball on mouse1 and we don't want people to be able to interfere with our game if they touch the trackball while the spinners are in use.

## Other Considerations
Sometimes, a game doesn't use the DIAL input. It uses Paddle. It can be convenient map inputs for the paddle device just in case:

```input_map[p1_paddlex] mouse[0,x] mouse[1,x] mouse[2,x] mouse[3,x]```

It is also possible to configure controls for certain games only. While this is not generally necessary, you do have the option to override defaults you might have configured above by specifying a ROM/ at the beginning of an input line. For example, if Tempest worked just like every other game but for some reason, just that game has the spinner working backwards, you could specify an additional input for that game only:

```tempest/input_map[p1_trackballx] -mouse[0,x] -mouse[1,x] -mouse[2,x] -mouse[3,x]```

### Sensitivity
Each game may require adjustments to the sensitivity. This too can be configured in the .rc file, but it is easier to adjust this within the MAME GUI. Bring up the menu in AdvanceMAME and adjust the analog inputs and test as needed. The results will be saved into the .rc file when you exit.

### Poll Rate
Some spinner hardware is designed with high precision. The encoder + optical sensors are capable of extreme sensitivity. However, this can work against you if Linux is not observing the mouse interface fast enough. It can cause a strange negative effect called "backspin". If you have ever watched an old western movie and noticed how a fast turning wagon wheel can appear to spin backwards--that's the same effect caused by a low frame rate during filming. It can be very frustrating to give a quick spin in Tempest only to watch it move backwards in the game until it slows down. One way to overcome this is to tell Linux to increase the poll rate of the mouse interface. You need to edit your `/boot/cmdline.txt` by appending `usbhid.mousepoll=2` to increase the mouse poll rate.

### Driving Games
Don't just limit your spinners to traditional titles. You might not have considered the fact that steering wheels are just big spinners. Driving games like Pole Position are perfectly suited for spinners.

### Unmapping Joysticks
Once you have your spinners working, you might want to remove the joystick controls for some games. MAME pre-configures joystick inputs in lieu of analog controls for some games to make them playable by users without a spinner/trackball. You could ignore this, but it can be annoying if you bump the joystick or if an observer accidentally touches it and affects your game. Simply go into the MAME GUI menu and edit controls for "this game" and remove the joystick inputs.
