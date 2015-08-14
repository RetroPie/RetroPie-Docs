![Retroarch Logo](http://www.libretro.com/wp-content/uploads/2014/01/retroarch-logo-300x611.png)
***
RetroArch is the official front end for the [Libretro](http://www.libretro.com/) API which essentially means that RetroArch will be what manages controls and configurations for all of the emulators that are part of the Libretro-Core (i.e. any emulator with an "lr" before it). This is a beautiful thing because it means you can configure controllers only once for many emulators instead of having to configure each emulator individually. RetroArch also gives us the freedom to configure emulators individually as discussed below under "Custom RetroArch Controls" (There are also emulator specific configurations under each emulator in the emulator section.)

## Retroarch-Joyconfig

#### From the RetroPie Menu

```
Choose configure retroarch keyboard/joystick
```
(you'll need a keyboard) plug in the controller you wish to configure and follow the steps.
Alternatively you can access the same function through the terminal:

Then follow the on screen directions and your controller should now work on all libretro-core emulators- 
including hotkeys (see below).

## Config Hierarchy

All RetroArch based emulators can be configured in the following way:

**Global** settings - that are settings which should apply to all systems - are done in the file 

    /opt/retropie/configs/all/retroarch.cfg 

**System-specific** settings are done in the files 

    /opt/retropie/configs/SYSTEMNAME/retroarch.cfg

Here, SYSTEMNAME is atari2600, snes, etc.. All settings in these files will overwrite the corresponding global setting as long as they are placed **above** the #includeconfig line.

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
**Note** the values below are for one person's controller, your values may differ.
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
input_enable_hotkey_btn = "8"
input_exit_emulator_btn = "9"
input_save_state_btn = "5"
input_load_state_btn = "4"
input_menu_toggle_btn = "0"
input_state_slot_increase_axis = "+0"
input_state_slot_decrease_axis = "-0"
```

## Hotkeys

Hotkeys are combinations of buttons you can press in order to access options such as saving, loading, and exiting games.

see this video:

<a href="http://www.dailymotion.com/video/x2hxlc3" target="_blank"><img src="https://lh4.ggpht.com/MFywT7QpnT6WA2vgh1Fb0bfaz2Si4BRCnWV53Hiu9lr1ZpE6tJ_mP7AmXzC7hy2wFFlD=w300" 
alt="N64 Configuration Video" width="150" height="150" border="10" /></a>

## Default joypad hotkeys:
Hotkeys | Action
| :---: | :---: |
Select+Start | Exit
Select+Right Shoulder | Save
Select+Left Shoulder | Load
Select+Right | Input State Slot Increase
Select+Left | Input State Slot Decrease 
Select+X | RGUI Menu
Select+B | Reset

***

![InputStation Logo](https://cloud.githubusercontent.com/assets/10035308/7110815/a2c49968-e174-11e4-941c-960290311bca.png)
***
_InputStation is the product of hard work from the EmulationStation Team (Aloshi and Nils) and the RetroPie Team (petrockblog, joolswills, and gizmo98). It is an all-in-one controller configuration module for EmulationStation, RetroArch, and will include other specific emulators in the future such as pifba, mupen64plus, etc._

***

This is integrated into emulationstation and will be the first thing you see when you boot from the RetroPie SD image (3.0) the first time. You can also access if from the start menu within emulationstation under the configure option.

The following diagrams are for the 3 most common controllers: Super Nintendo, Xbox 360, and PlayStation 3. They can be used as a reference when configuring your controllers. Each emulator page on the wiki has a diagram of the original controller for its respective console that will correspond to the same inputs listed below.

## Super Nintendo Controller
![Super Nintendo Controller](https://cloud.githubusercontent.com/assets/10035308/7110174/0f2fdb54-e16a-11e4-8f3d-37bdca8f1ddf.png)

## Xbox 360 Controller
![Xbox 360 Controller](https://cloud.githubusercontent.com/assets/10035308/7110173/0f2ea784-e16a-11e4-9c6f-5fe7c594b05a.png)

## PlayStation 3 Controller
![PlayStation 3 Controller](https://cloud.githubusercontent.com/assets/10035308/7111199/e29365ec-e179-11e4-87b4-f00685661d7e.png)


***
# Default Controls for All Emulators:
## 3do
![3dodiagram](https://cloud.githubusercontent.com/assets/10035308/8237801/0ae4d6fc-15af-11e5-803f-8ba408d48362.png)
## Atari 2600
![atari2600diagram](https://cloud.githubusercontent.com/assets/10035308/8237960/02aa13fc-15b0-11e5-92c2-311e8960883b.png)
## Atari Lynx
![atari_lynx](https://cloud.githubusercontent.com/assets/10035308/8176465/8d4a4c74-13b8-11e5-9956-c059ac3fc9e1.png)
## Gameboy
![gameboy](https://cloud.githubusercontent.com/assets/10035308/7334402/bd640072-eb4e-11e4-8251-d2bc3b876153.png)
## Gameboy Color
![gameboycolor](https://cloud.githubusercontent.com/assets/10035308/7334404/bd65e496-eb4e-11e4-82e6-78494534d305.png)
## Gameboy Advance
![gameboyadvance](https://cloud.githubusercontent.com/assets/10035308/7334407/bd688f52-eb4e-11e4-8899-246bad0ad139.png)
## Game Gear
![segagamegeardiagram](https://cloud.githubusercontent.com/assets/10035308/8245009/b4c87e72-15e5-11e5-8ee5-691daa4d1dd5.png)
## Mastersystem
![mastersystem](https://cloud.githubusercontent.com/assets/10035308/7334954/59794038-eb60-11e4-989d-6367c1fda8ef.png)
## Megadrive/Genesis (3 Button)
![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)
## Megadrive/Genesis (6 Button)
![genesis6btn](https://cloud.githubusercontent.com/assets/10035308/7336429/7e524110-ebbb-11e4-8777-05a824384d34.png)
## Nintendo 64
![nintendo_n64_diagram](https://cloud.githubusercontent.com/assets/10035308/7334793/6b406d8c-eb5b-11e4-8474-56a340521e71.png)
## Nintendo DS
![dsdiagram](https://cloud.githubusercontent.com/assets/10035308/8240819/99893d9a-15c2-11e5-9d52-c86db39493f6.png)
## NES
![nesdiagram](https://cloud.githubusercontent.com/assets/10035308/8245062/4f0c5b8e-15e6-11e5-9255-b920543518d6.png)
## Neo Geo
![neogeodiagram](https://cloud.githubusercontent.com/assets/10035308/8245309/a575cc8c-15e9-11e5-8735-0a4ab2a4e137.png)
## Neo Geo Pocket
![neogeopocketdiagram](https://cloud.githubusercontent.com/assets/10035308/8244887/0e06c54a-15e4-11e5-8f8f-28758d16c446.png)
## PS1
![playstation](https://cloud.githubusercontent.com/assets/10035308/8194532/8213433e-1439-11e5-8e69-87c6a7dc275c.png)
## SG-1000
![sg-1000diagram](https://cloud.githubusercontent.com/assets/10035308/8238988/4aee1770-15b6-11e5-90d4-5bf66ac7e3dd.png)
## Super Nintendo
![snes](https://cloud.githubusercontent.com/assets/10035308/7334403/bd655d6e-eb4e-11e4-8fd7-a4424aad1034.png)
## Sega Saturn
![saturn](https://cloud.githubusercontent.com/assets/10035308/7449063/327bfb76-f1e9-11e4-9c58-4b38a3c1284d.png)
## Turbografx16
![turbografx16diagram](https://cloud.githubusercontent.com/assets/10035308/8239221/aa5f3602-15b7-11e5-9c9f-54322c0a18bc.png)
## Videopac/Odyssey2
![videopacdiagram](https://cloud.githubusercontent.com/assets/10035308/8236975/679e6a58-15a9-11e5-98de-4ca681404eca.png)
## Vectrex
![vectrex](https://cloud.githubusercontent.com/assets/10035308/8196876/168671c6-144e-11e5-8139-d2d980a936fa.png)
## VirtualBoy
![virtualboydiagram](https://cloud.githubusercontent.com/assets/10035308/8246349/6552ef7a-15fa-11e5-9a78-1800b51cccc5.png)
***
## Intellivision
![intellivision](https://cloud.githubusercontent.com/assets/10035308/8246393/3e98c8c2-15fb-11e5-9398-3f5abd60361b.png)
## Sega Dreamcast
![dreamcast](https://cloud.githubusercontent.com/assets/10035308/8246417/9c839e08-15fb-11e5-9747-cf0b25727c11.png)