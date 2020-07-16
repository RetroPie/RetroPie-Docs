The instructions below show how to setup an N64 USB controller.

Ironically, setting up an N64 Controller requires several tweaks to play N64 games with an N64 Controller. Most emulators were designed to work with a more modern controller with left and right analog sticks, not C-buttons.

- Every controller could be different! The example below was created using a "Classic-Controller-kiwitatá-Controllers-Joystick" USB controller _(google it - 2 pack was about \$30 USD)._
- Tested on several mupen64 emulators and all seemed to work (Mupen64plus, lr-mupen64plus, lr-mupen64plus-next). Note, the lr-mupen64plus-next emulator seemed to be the only active project in 2020
- Used RetroPie 4.6 on a Raspberry Pi 4b

The steps are as follows:

1.  [Map Controller in Emulationstation](#map-controller-in-emulationstation)
2.  [Figure Out Button Mapping](#figure-out-button-mapping)
3.  [Setup Hotkeys](#setup-hotkeys) _(optional)_
4.  [Remap Emulationstation buttons](#remap-emulationstation-buttons) _(optional)_
5.  [Update N64 Retroarch Input]()
6.  [Fix Retroarch Mapping for C buttons](#fix-retroarch-mapping-for-c-buttons)

## Map Controller in Emulationstation

The best start to configure the N64 USB controller is to start with the Mupen64plus diagram.

Do **NOT** setup Hotkeys. Default hotkeys will not work and cause major frustration!

![nintendo_n64_mupen64plus_diagram](https://cloud.githubusercontent.com/assets/10035308/16599635/7f35579a-42c0-11e6-9615-9a3670932332.png)

- For clarity, the **C-Down** button should be mapped to A and **C-Left** should be mapped to X. Right analog left and down will be unmapped.
- This mapping leave the C-Down button as the "A" button and the A button as the "B" when navigating retropie UI. We'll fix that in step 4 [Remap Emulationstation buttons](#remap-emulationstation-buttons)

## Figure Out Button Mapping

It is important to know the button layout as these numbers will be used in future steps.

Once you configure the controller in Emulation Station using mapping image above, look at the file generated in EmulationStation. To get here, open a terminal or browse to remote file and view the .cfg file (name will vary) in `/opt/retopie/configs/all/retroarch-joypads`. (Example: `/opt/retropie/configs/all/retroarch-joypads/SWITCH\ CO.\,LTD.\ Controller\ \(Dinput\).cfg`)

The output will look lke the following. Comments were added after mapping was figured out, but will not be generated automatically.

```
input_device = "SWITCH CO.,LTD. Controller (Dinput)"
input_driver = "udev"

input_b_btn = "1"               # A
input_y_btn = "2"               # B
input_l_btn = "4"               # L Shoulder
input_r_btn = "5"               # R Shoulder
input_l2_btn = "6"              # Z trigger
input_r_y_minus_btn = "9"       # C Up
input_a_btn = "0"               # C Down
input_x_btn = "3"               # C Left
input_r_x_plus_btn = "8"        # C Right
input_start_btn = "12"          # Start
input_up_btn = "h0up"
input_down_btn = "h0down"
input_left_btn = "h0left"
input_right_btn = "h0right"
input_l_y_plus_axis = "+1"
input_l_y_minus_axis = "-1"
input_l_x_minus_axis = "-0"
input_l_x_plus_axis = "+0"

```

_Example output after generating Controller mapping, every controller may have different mapping_

## Setup Hotkeys

_(optional step)_

The default retroarch hotkeys do not work well with the N64 layout. Feel free to map differently, but a useful way is to use Start as the main hotkey. You cannot use Start as hotkey and Exit, or everytime you hit the button, you'll kick yourself out of the emulator.

In the controller config file in the step above, add the hotkey mapping in .cfg file (name will vary) in `/opt/retopie/configs/all/retroarch-joypads`. (Example: `/opt/retropie/configs/all/retroarch-joypads/SWITCH\ CO.\,LTD.\ Controller\ \(Dinput\).cfg`). Again, button mapping may vary by controller used.

```
[...ommitted mapping lines from previous step...]

input_state_slot_decrease_btn = "h0left"   # D-pad left
input_state_slot_increase_btn = "h0right"  # D-pad right
input_enable_hotkey_btn = "12"  # Start
input_load_state_btn = "4"      # L Shoulder
input_save_state_btn = "5"      # R Shoulder
input_reset_btn = "2"           # B
input_exit_emulator_btn = "6"   # Z Trigger
input_menu_toggle_btn = "3"     # C Left

```

_(exact values vary by controller)_

Save and restart emulationstation for changes to take effect.

## Remap Emulationstation Buttons

_(optional step)_

As this controller works slightly differently when navigating Retropie games, the defaults when mapping to the above image leaves the C-Down button as the "A" button and the A button as the "B" when navigating retropie UI. To navigate games/menus using A and B buttons, make the following edit to the controller's section in `/opt/retropie/configs/all/emulationstation/es_input.cfg`

Make sure to not doublemap the same key, you may have to shuffle a few inputs around. Should not affect anything else as only A and B are important in ES.

```
  <inputConfig type="joystick" deviceName="SWITCH CO.,LTD. Controller (Dinput)" deviceGUID="03000000632500007505000011010000">
    <input name="up" type="hat" id="0" value="1"/>
    <input name="left" type="hat" id="0" value="8"/>
    <input name="right" type="hat" id="0" value="2"/>
    <input name="x" type="button" id="3" value="1"/>
    <input name="down" type="hat" id="0" value="4"/>
    <input name="start" type="button" id="12" value="1"/>
    <input name="b" type="button" id="2" value="1"/>  # change ID to B button Value
    <input name="a" type="button" id="1" value="1"/>  # change ID to A button Value
    <input name="rightanalogup" type="button" id="9" value="1"/>
    <input name="pageup" type="button" id="4" value="1"/>
    <input name="leftanalogdown" type="axis" id="1" value="1"/>
    <input name="leftanalogright" type="axis" id="0" value="1"/>
    <input name="leftanalogleft" type="axis" id="0" value="-1"/>
    <input name="rightanalogright" type="button" id="8" value="1"/>
    <input name="pagedown" type="button" id="5" value="1"/>
    <input name="leftanalogup" type="axis" id="1" value="-1"/>
    <input name="y" type="button" id="0" value="1"/>
    <input name="rightanalogdown" type="button" id="0" value="1"/>
    <input name="rightanalogleft" type="button" id="3" value="1"/>
  </inputConfig>
```

_(exact values vary by controller)_

Save and restart emulationstation. Navigation/menu selection should now work with A and B.

## Update N64 Retroarch Input

The details of changes may vary by Controller used, but in the example USB controller used, the default retroarch input for the N64 emulator did not map properly. Make sure all the buttons are mapped to the correct button number per previous steps.

Edit the "InputAutoCfg.ini" file location in `/opt/retropie/configs/n64/InputAutoCfg.ini` (recommend to make a backup of this file prior to editing).

_(I had to add C Button L and C Button Down lines and C Up had a double map)_

Final file should look like this:

```
[...ommitted lines above...]

; SWITCH CO.,LTD. Controller (Dinput)_START
[SWITCH CO.,LTD. Controller (Dinput)]
plugged = True
plugin = 2
mouse = False
AnalogDeadzone = 4096,4096
AnalogPeak = 32768,32768
Mempak switch =
Rumblepak switch =
DPad U = hat(0 Up)
DPad L = hat(0 Left)
DPad D = hat(0 Down)
DPad R = hat(0 Right)
Start = button(12)
C Button U = button(9)
C Button R = button(8)
C Button D = button(0)
C Button L = button(3)
L Trig = button(4)
Y Axis = axis(1-,1+)
X Axis = axis(0-,0+)
Z Trig = button(6)
R Trig = button(5)
B Button = button(2)
A Button = button(1)

; SWITCH CO.,LTD. Controller (Dinput)_END

[...ommitted lines below...]
```

_(exact values vary by controller)_

## Fix Retroarch Mapping for C Buttons

This step may vary by emulator used, but the retroarch settings were not correct when playing a game (hotkey to retroarch menu and change config map). To fix, make sure the "Auto : \[button\]" settings are pointed to the right button from the InputAutoCfg map above.

Once change was made to retroarch config, save the config map and resume game. The generated file (rmp) from this change will be located in an emulator folder (name may vary), but will be located in a folder like: `/opt/retropie/configs/n64/Mupen64Plus-Next GLES3/Mupen64Plus-Next GLES3.rmp`

The a and x buttons were the buttons incorrect in my default mapping, 22 and 21 were added by retroarch (I have no idea what this means). You can manually modify the file to add it to each player, or you can repeat the steps with each player input setting on retroarch.

```
input_libretro_device_p1 = "1"
input_libretro_device_p2 = "1"
input_libretro_device_p3 = "1"
input_libretro_device_p4 = "1"
input_libretro_device_p5 = "1"
input_player1_analog_dpad_mode = "0"
input_player1_btn_a = "22"     # added by system on change
input_player1_btn_x = "21"     # added by system on change
input_player2_analog_dpad_mode = "0"
input_player2_btn_a = "22"
input_player2_btn_x = "21"
input_player3_analog_dpad_mode = "0"
input_player3_btn_a = "22"
input_player3_btn_x = "21"
input_player4_analog_dpad_mode = "0"
input_player4_btn_a = "22"
input_player4_btn_x = "21"
input_player5_analog_dpad_mode = "0"
```

Changes should take effect when resuming game, but restart retropie to confirm change are saved properly.

- Ensure map is saved for the entire emulator, not just per game.
- Same remapping can be done for specific games by saving Per Game, which will make a file with game name.
