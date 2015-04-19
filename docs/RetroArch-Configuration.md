![Retroarch Logo](http://www.libretro.com/wp-content/uploads/2014/01/retroarch-logo-300x611.png)
***
RetroArch is the official front end for the [Libretro](http://www.libretro.com/) API which essentially means that RetroArch will be what manages controls and configurations for all of the emulators that are part of the Libretro-Core (i.e. any emulator with an "lr" before it). This is a beautiful thing because it means you can configure controllers only once for many emulators instead of having to configure each emulator individually. RetroArch also gives us the freedom to configure emulators individually as discussed below under "Custom RetroArch Controls" (There are also emulator specific configurations under each emulator in the emulator section.)

## Retroarch-Joyconfig
Plug in one controller you wish to configure and in the terminal type:
```shell
cd RetroPie-Setup
sudo ./retropie_setup.sh
Option 3 Setup
Option 317 Configure Retroarch Controller

Follow the on screen directions and your controller should now work on all libretro-core emulators- 
including hotkeys (select+start to exit, select+right bumper to save, select+left bumper to load) 
```

All RetroArch based emulators can be configured in the following way:

**Global** settings - that are settings which should apply to all systems - are done in the file 

    /opt/retropie/configs/all/retroarch.cfg 

**System-specific** settings are done in the files 

    /opt/retropie/configs/SYSTEMNAME/retroarch.cfg

Here, SYSTEMNAME is atari2600, snes, etc.. All settings in these files will overwrite the corresponding global setting.

These configurations are used when starting a rom for a specific system. The individually used commands for starting a single rom can be found in the settings file of Emulation Station 

    ~/.emulationstation/es_systems.cfg

see these videos:

<a href="http://www.dailymotion.com/video/x2i0njr_retropie-testing-joystick-on-raspberry-pi_videogames" target="_blank"><img src="https://lh4.ggpht.com/MFywT7QpnT6WA2vgh1Fb0bfaz2Si4BRCnWV53Hiu9lr1ZpE6tJ_mP7AmXzC7hy2wFFlD=w300" 
alt="N64 Configuration Video" width="100" height="100" border="10" /></a> |
<a href="http://www.dailymotion.com/video/x2hudlt_retropie-configure-usb-controller-retroarch_videogames" target="_blank"><img src="https://lh4.ggpht.com/MFywT7QpnT6WA2vgh1Fb0bfaz2Si4BRCnWV53Hiu9lr1ZpE6tJ_mP7AmXzC7hy2wFFlD=w300" 
alt="N64 Configuration Video" width="100" height="100" border="10" /></a>  |      <a href="http://www.dailymotion.com/video/x2i0s10_retropie-configuring-a-wireless-ps3-controller_videogames" target="_blank"><img src="https://lh4.ggpht.com/MFywT7QpnT6WA2vgh1Fb0bfaz2Si4BRCnWV53Hiu9lr1ZpE6tJ_mP7AmXzC7hy2wFFlD=w300" 
alt="N64 Configuration Video" width="100" height="100" border="10" /></a>   |       <a href="http://www.dailymotion.com/video/x2i0ufc_retropie-xbox-wireless-controller-setup-on-raspberry-pi_videogames" target="_blank"><img src="https://lh4.ggpht.com/MFywT7QpnT6WA2vgh1Fb0bfaz2Si4BRCnWV53Hiu9lr1ZpE6tJ_mP7AmXzC7hy2wFFlD=w300" 
alt="N64 Configuration Video" width="100" height="100" border="10" /></a>  |  <a href="http://www.dailymotion.com/video/x2i0lsy_retropie-multiple-usb-controllers_videogames" target="_blank"><img src="https://lh4.ggpht.com/MFywT7QpnT6WA2vgh1Fb0bfaz2Si4BRCnWV53Hiu9lr1ZpE6tJ_mP7AmXzC7hy2wFFlD=w300" 
alt="N64 Configuration Video" width="100" height="100" border="10" /></a> 


 [Testing Joystick](http://www.dailymotion.com/video/x2i0njr_retropie-testing-joystick-on-raspberry-pi_videogames) | [Setting up Controller](http://www.dailymotion.com/video/x2hudlt_retropie-configure-usb-controller-retroarch_videogames) | [Wireless PS3 Controller](http://www.dailymotion.com/video/x2i0s10_retropie-configuring-a-wireless-ps3-controller_videogames) | [Wireless Xbox Controller](http://www.dailymotion.com/video/x2i0ufc_retropie-xbox-wireless-controller-setup-on-raspberry-pi_videogames) | [Setting Up Multiple Controllers](http://www.dailymotion.com/video/x2i0lsy_retropie-multiple-usb-controllers_videogames) 
----- | ----- | ----- |----- | -----
## Custom Retroarch Controls

## Example retroarch.cfg file for custom controls to override defaults
```shell
input_player1_joypad_index = 0
input_player1_b_btn = 2
input_player1_a_btn = 1
input_player1_y_btn = 3
input_player1_x_btn = 0
input_player1_l_btn = 4
input_player1_r_btn = 5
input_player1_start_btn = 9
input_player1_select_btn = 8
input_player2_joypad_index = 1
input_player2_b_btn = 2
input_player2_a_btn = 1
input_player2_y_btn = 3
input_player2_x_btn = 0
input_player2_l_btn = 4
input_player2_r_btn = 5
input_player2_start_btn = 9
input_player2_select_btn = 8

# Axis for RetroArch D-Pad. 
# Needs to be either '+' or '-' in the first character signaling either positive or negative direction of the axis, then the axis number. 
input_player1_up_axis = -1
input_player1_down_axis = +1
input_player1_left_axis = -0
input_player1_right_axis = +0
input_player2_up_axis = -1
input_player2_down_axis = +1
input_player2_left_axis = -0
input_player2_right_axis = +0

#Hotkeys- Hotkeys enable you to press a combination of buttons to do such things as exit emulators, save states,
# and load states, as well as any other functionality in an emulator. (In the example below 8 is the select key
# and 9 is the start key so when I hold down select and press start it will exit the emulator.)
input_enable_hotkey_btn = 8
input_exit_emulator_btn = 9
input_save_state_btn = 5
```

## Hotkeys

Hotkeys are combinations of buttons you can press in order to access options such as saving, loading, and exiting games.

see this video:

<a href="http://www.dailymotion.com/video/x2hxlc3" target="_blank"><img src="https://lh4.ggpht.com/MFywT7QpnT6WA2vgh1Fb0bfaz2Si4BRCnWV53Hiu9lr1ZpE6tJ_mP7AmXzC7hy2wFFlD=w300" 
alt="N64 Configuration Video" width="150" height="150" border="10" /></a>

## Default joypad shortcuts:

* 'select' + 'start' - exit game and return to Emulationstation
* 'select' + 'B' - restart game
* 'select' + 'X' - open RetroArch menu that allows you to save/load game state, make a screenshot etc.

***


![InputStation Logo](https://cloud.githubusercontent.com/assets/10035308/7110815/a2c49968-e174-11e4-941c-960290311bca.png)
***
_InputStation is the product of hard work from the EmulationStation Team (Aloshi and Nils) and the RetroPie Team (petrockblog, joolswills, and gizmo98). It is currently in development but once completed it will be an all-in-one controller configuration module for EmulationStation, RetroArch, and other specific emulators._

***
As it stands right now, there are diagrams for 3 controllers: Super Nintendo, Xbox 360, and PlayStation 3.

## Super Nintendo Controller
![Super Nintendo Controller](https://cloud.githubusercontent.com/assets/10035308/7110174/0f2fdb54-e16a-11e4-8f3d-37bdca8f1ddf.png)

## Xbox 360 Controller
![Xbox 360 Controller](https://cloud.githubusercontent.com/assets/10035308/7110173/0f2ea784-e16a-11e4-9c6f-5fe7c594b05a.png)

## PlayStation 3 Controller
![PlayStation 3 Controller](https://cloud.githubusercontent.com/assets/10035308/7111199/e29365ec-e179-11e4-87b4-f00685661d7e.png)