The Logitech Gamepad F310 and Logitech Gamepad F710 are a good choice of controller for RetroPie. They have a Sony DualShock style layout and good sturdy build quality.

The F310 is wired with a 1.8m (6 ft) USB cable.

![Logitech Gamepad F310](http://i.imgur.com/KN6TgtP.png)

The F710 is wireless with a range of at least 6m (20ft). It uses a small USB dongle for wireless signal, the dongle can be stored inside the controller if you wish to unplug it. Power is provided by 2x AA batteries. The controller comes with a 1.5m (5 ft) USB extension cable allowing relocation of the receiver for good signal strength if your Pi is hidden inside a busy TV cabinet.

![Logitech Gamepad F710](http://i.imgur.com/2z6Kq9E.png)

Both controller models feature a **Mode** switch which swaps the D-pad and left analog stick in hardware when enabled. This is a great feature when playing games where a joystick offers more precision than a D-pad such as fighters, beat-em-ups, and shmups.

Earlier discontinued Logitech controllers such as the Logitech Dual Action, Logitech Rumble Pad, and Logitech Precision are also a good choice and have features similar to the F310 and F710.

## DirectInput / XInput Switch

On the back of the controllers is a switch with **D** and **X**, standing for DirectInput and XInput mode. These are controller programming APIs created by Microsoft.

XInput mode is the newer mode introduced with the XBox 360 controller in 2005. ***XInput is the suggested input mode***. The controllers register with their name as "Logitech F310 Gamepad" or "Logitech F710 Gamepad". The L2/R2 triggers are analog axes in this mode.

DirectInput is the older input mode, first introduced with DirectX in 1995. These controllers actually appear as "Logitech Rumble Pad 2" or similar while in DirectInput mode. The L2/R2 triggers are digital buttons in this mode.

It is not possible to switch D/X mode in the middle of use. EmulationStation must be quit and restarted, or the Pi rebooted, so that EmulationStation realises a different controller type is plugged in and configures the system appropriately.

As of RetroPie 3.8, using two controllers in DirectInput mode requires use of the "multi input" USB HID quirk. This is added by editing `/boot/cmdline.txt` and appending `usbhid.quirks=0x046d:0xc219:0x40` to the existing line (do not make a new line) then save the file and reboot. XInput mode does not require this, so just use XInput.

## Configuration

Configuration in EmulationStation is fairly straightforward.

#### ABXY Layout

Note the RetroPad ABXY pattern is the opposite of the ABXY pattern on the controller. Just ignore the controller labeling and press ABXY as if you were holding a SNES controller (A as B, B as A, X as Y, Y as X):

If you truly wish to use the Logitech-labeled A and B buttons as A and B, edit `/opt/retropie/configs/all/autoconf.cfg` and set `es_swap_a_b = 1` then reconfigure the controller in EmulationStation. Now A and B will work as labeled in EmulationStation, but will work like the SNES/RetroPad layout in emulators. You still need to configure X as Y and Y as X.

#### Logitech Button

In XInput mode, the Logitech button in the middle of the controller can be used as another input button.

You could configure this button as the RetroArch hotkey instead of Select. This would move the quit action to Logitech+Start, the RGUI menu to Logitech+X, and so on. This would allow Select+Start, Select+B, and the rest of the usual Select-based hotkeys to be pressed in-game with no side effects.

If this is desired, edit the `retroarch-joypads` file described below and change the `input_enable_hotkey_btn` to:

~~~
input_enable_hotkey_btn = "10"
~~~

## Config Files

The RetroArch config differs only with the filename and identification string:

~~~
/opt/retropie/configs/all/retroarch-joypads/LogitechGamepadF310.cfg
input_device = "Logitech Gamepad F310"
~~~

~~~
/opt/retropie/configs/all/retroarch-joypads/LogitechGamepadF710.cfg
input_device = "Logitech Gamepad F710"
~~~

The rest of the contents are the same:

~~~
input_driver = "udev"
input_up_btn = "h0up"
input_down_btn = "h0down"
input_left_btn = "h0left"
input_right_btn = "h0right"
input_a_btn = "1"
input_b_btn = "0"
input_x_btn = "3"
input_y_btn = "2"
input_start_btn = "9"
input_select_btn = "8"
input_l_btn = "4"
input_r_btn = "5"
input_l2_btn = "6"
input_r2_btn = "7"
input_l3_btn = "11"
input_r3_btn = "12"
input_l_y_minus_axis = "-1"
input_l_y_plus_axis = "+1"
input_l_x_minus_axis = "-0"
input_l_x_plus_axis = "+0"
input_r_y_minus_axis = "-3"
input_r_y_plus_axis = "+3"
input_r_x_minus_axis = "-2"
input_r_x_plus_axis = "+2"
input_enable_hotkey_btn = "8"
input_reset_btn = "0"
input_menu_toggle_btn = "3"
input_exit_emulator_btn = "9"
input_load_state_btn = "4"
input_save_state_btn = "5"
input_state_slot_increase_btn = "h0right"
input_state_slot_decrease_btn = "h0left"
~~~

#### Mupen64plus

Only the controller name and headings differ in `/opt/retropie/configs/n64/InputAutoCfg.ini`:

~~~
; Logitech Gamepad F310_START
[Logitech Gamepad F310]
...
; Logitech Gamepad F310_END
~~~

~~~
; Logitech Gamepad F710_START
[Logitech Gamepad F710]
...
; Logitech Gamepad F710_END
~~~

The configuration is identical for the two controllers.

This layout uses the controller's L1/R1 as N64 L/R, and the controller's L2 trigger as N64 Z trigger:

~~~
plugged = True
plugin = 2
mouse = False
AnalogDeadzone = 4096,4096
AnalogPeak = 32768,32768
Mempak switch = button(11)
Rumblepak switch = button(12)
DPad U = hat(0 Up)
DPad D = hat(0 Down)
DPad L = hat(0 Left)
DPad R = hat(0 Right)
A Button = button(0)
B Button = button(2)
Start = button(9)
C Button U = button(3) axis(4-)
C Button D = button(1) axis(3+)
C Button L = axis(2-)
C Button R = axis(2+)
Y Axis = axis(1-,1+)
X Axis = axis(0-,0+)
R Trig = button(5)
L Trig = button(6)
Z Trig = button(4)
~~~

#### Dreamcast

The following file should match below: `/opt/retropie/configs/dreamcast/mappings/controller_LogitechGamepadF310.cfg`

[Source](https://www.reddit.com/r/RetroPie/comments/4u0sys/fairly_successful_controller_mapping_for_logitech)

~~~
[emulator]
mapping_name = Logitech Gamepad F310
btn_escape = 316

[dreamcast]
btn_a = 305
btn_b = 304
btn_c =
btn_d =
btn_x = 308
btn_y = 307
btn_z =
btn_start = 315
btn_dpad1_left =
btn_dpad1_right =
btn_dpad1_up =
btn_dpad1_down =
btn_dpad2_left =
btn_dpad2_right =
btn_dpad2_up =
btn_dpad2_down =
axis_x = 0
axis_y = 1
axis_trigger_left = 
axis_trigger_right =

[compat]
btn_trigger_left = 310
btn_trigger_right = 311
axis_dpad1_x = 16
axis_dpad1_y = 17
axis_dpad2_x =
axis_dpad2_y =
axis_x_inverted = no
axis_y_inverted = no
axis_trigger_left_inverted = no
axis_trigger_right_inverted = no
axis_dpad1_y_inverted = no
axis_dpad1_x_inverted = no
~~~

#### 310 Disconnecting Issue

You may or may not experience an issue where, after loading a ROM, the controller is no longer responsive. Assuming it's set up as this page, press the right shoulder or trigger button to resolve this. For me this works by pressing what was called the R1 button on the PSX.

This appears to be a firmware issue as described [here](https://www.reddit.com/r/RetroPie/comments/3yh7o3/pi_zero_latest_retropie_logitech_f310/).

#### L2/R2 Top Triggers

**This is no longer an issue as of RetroPie 4.0**, as the analog triggers register as buttons.

The "left top" (L2) and "right top" (R2) triggers can be tricky to get right. If you press and release the trigger quickly, you may configure the negative (outward) axis, which is wrong. When this occurs, RetroArch emulators will need the L2/R2 buttons to be pressed once before registering any other input. If you see "left top" as **-2** and/or "right top" as **-5** then the axis is configured incorrectly.

If this happens, complete the rest of the EmulationStation controller setup, but don't press OK at the end. Instead, go back up with the D-Pad and re-configure the "left top" and "right top" controls, this time pressing the trigger inwards more slowly. If done right, "left top" will be the **+2** axis and "right top" will be the **+5** axis. This is the correct configuration.