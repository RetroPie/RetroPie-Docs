![Retroarch Logo](http://www.libretro.com/wp-content/uploads/2014/01/retroarch-logo-300x611.png)
***

RetroArch is the official front end for the [libretro API](http://www.libretro.com/). RetroArch and libretro provide a way to take an existing emulator and load that emulator as a library or "core". RetroArch then handles the input (controls) and output (graphics and audio) while the emulator core handles the emulation of the original system. With a few simple changes to the emulator source code, almost any existing emulator could become a libretro core.

In RetroPie, the libretro emulator cores are identified with a `lr-` in front of their name. For example, `lr-snes9x-next` is the libretro core of the SNES emulator called snes9x.

RetroArch and libretro provide ability to configure controllers once for many emulators instead of having to configure each emulator individually. However, RetroArch also provides the freedom to configure specific emulators individually and even individual games differently if the user wants. This allows a specific setting or button mapping for a certain console or even just for a certain game.

For emulators which are not libretro cores, there are emulator-specific configurations under the respective system's wiki page.

### The RetroPad concept

When you configure your controller in EmulationStation, the RetroPie setup script automatically configures RetroArch with the same controls.

RetroArch controls map real-world controller buttons to a virtual controller called a "RetroPad". A RetroPad does not exist in real life, it's a concept only within RetroArch. A RetroPad has an ABXY layout like a SNES controller plus four shoulder buttons and dual analog sticks like a Sony DualShock.

You don't have to map all of the RetroPad buttons to a real world button. If your real controller has less buttons than a DualShock, then the virtual RetroPad also has less buttons, that's perfectly fine.

As RetroArch starts an emulator core, it maps the RetroPad configuration to the emulated system's original controls. The mapping for many consoles is represented by the pictures below and on each system's wiki page. If you wish, you can reconfigure this control mapping, either for all RetroArch, for a specific system, or even for a specific ROM.

# Retroarch Controls

There are 3 main ways to configure input for RetroArch:

- [**Autoconfigurations**](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration#autoconfigurations) - made in EmulationStation
- [**Hardcoded Configurations**](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration#hardcoded-configurations) - made by editing `retroarch.cfg` file(s)
- [**Core Input Remapping**](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration#core-input-remapping) - an easy way to do specific control configurations for specific cores, made in the RetroArch RGUI

## AutoConfigurations

RetroArch controls have been integrated into EmulationStation and will be the first thing you see when you boot from the RetroPie SD image the first time. You can also access it from the start menu within EmulationStation under the Configure Input option. Your joypad is automagically configured for libretro (RetroArch) emulators when you configure your controller in EmulationStation. You'll know if your controller has been automagically configured if you see a flash of yellow text on the bottom of the screen with your gamepad ID when you start a game.  

The following diagrams are for the 3 most common controllers: Super Nintendo, Xbox 360, and PlayStation 3. They can be used as a reference when configuring your controllers. Each emulator page on the wiki has a diagram of the original controller for its respective console that will correspond to the same inputs listed below.

![nintendo_snes_diagram](https://cloud.githubusercontent.com/assets/10035308/16599633/7f34d356-42c0-11e6-92c0-f8774d795bd1.png)

![microsoft_xbox360_diagram](https://cloud.githubusercontent.com/assets/10035308/16599644/7f50121a-42c0-11e6-8ef5-50c4b5672216.png)

![playstation3_diagram](https://cloud.githubusercontent.com/assets/10035308/16599634/7f353148-42c0-11e6-9023-dbaf074bc933.png)

After you've configured your controller the autoconfig will be created here:

```
/opt/retropie/configs/all/retroarch-joypads
```

This is an example config for a USB SNES controller

```
input_device = "USB gamepad           "
input_driver = "udev"
input_r_btn = "5"
input_save_state_btn = "5"
input_start_btn = "9"
input_exit_emulator_btn = "9"
input_l_btn = "4"
input_load_state_btn = "4"
input_up_axis = "-1"
input_a_btn = "1"
input_b_btn = "2"
input_reset_btn = "2"
input_down_axis = "+1"
input_right_axis = "+0"
input_state_slot_increase_axis = "+0"
input_x_btn = "0"
input_menu_toggle_btn = "0"
input_select_btn = "8"
input_enable_hotkey_btn = "8"
input_y_btn = "3"
input_left_axis = "-0"
input_state_slot_decrease_axis = "-0"
```

#### Hotkeys

Hotkeys are combinations of buttons you can press in order to access options such as saving, loading, and exiting games. The following defaults are set automatically the first time you set up your controller from EmulationStation (the numbers will vary depending the controller you use).

#### Default joypad hotkeys:
Hotkeys | Action | Code Example
| :---: | :---: | :---: |
Select | Hotkey | input_enable_hotkey_btn = "6"
Select+Start | Exit | input_exit_emulator_btn = "7"
Select+Right Shoulder | Save | input_save_state_btn = "5"
Select+Left Shoulder | Load | input_load_state_btn = "4"
Select+Right | Input State Slot Increase | input_state_slot_increase_btn = "h0right"
Select+Left | Input State Slot Decrease | input_state_slot_decrease_btn = "h0left"
Select+X | RGUI Menu | input_menu_toggle_btn = "3"
Select+B | Reset | input_reset_btn = "0"

### Video Tutorial

* [RetroPie: Using hotkeys in retroarch - mapping to joypad by Floob](https://www.youtube.com/watch?v=DBnKFRflEV4)

## Hardcoded Configurations

These configurations are manual edits you can make that are locked to a specific libretro core and controller. Hardcoded controls can be configured either globally, specific to the emulator core, or specific to an individual game.

### Config Hierarchy

All RetroArch based emulators can be configured in the following way:

**Global** settings - that are settings which should apply to all systems - are done in the file:

```
/opt/retropie/configs/all/retroarch.cfg
```

([example](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration#example-default-per-system-retroarchcfg))

**System-specific** settings are done in the files:

```
/opt/retropie/configs/SYSTEMNAME/retroarch.cfg
```

([example](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration#example-per-system-control-override-retroarchcfg))

Here, SYSTEMNAME is `atari2600`, `snes`, etc. All settings in these files will overwrite the corresponding global setting as long as they are placed **above** the `#includeconfig` line.

**ROM-specific** settings can be created in the [runcommand](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand) menu and show up as configuration files by ROM title:

```
/home/pi/RetroPie/roms/SYSTEMNAME/ROMNAME.cfg
```

([example](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration/#example-per-system-control-override-retroarchcfg))

The `ROMNAME` includes the original file extension before the `.cfg`, e.g. `supermariobros.zip.cfg` These configurations are used when starting this specific ROM.
 
## Custom RetroArch Override Examples

### Example Default Per-System retroarch.cfg

```
# Settings made here will only override settings in the global retroarch.cfg if placed above the #include line

input_remapping_directory = /opt/retropie/configs/megadrive/


#include "/opt/retropie/configs/all/retroarch.cfg"
```

### Example Per-System Control Override retroarch.cfg

**Note** the values below are for one person's controller, your values may differ. Make sure that these values are placed **above** the `#includeconfig` line:

```
# Settings made here will only override settings in the global retroarch.cfg if placed above the #include line

input_remapping_directory = /opt/retropie/configs/megadrive/

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
input_load_state_btn = 4
input_menu_toggle_btn = 0
input_state_slot_increase_axis = +0
input_state_slot_decrease_axis = -0


#include "/opt/retropie/configs/all/retroarch.cfg"
```

### Example Per-ROM Override retroarch.cfg

```
aspect_ratio_index = "19"

# Never save-on-exit after an override config
# or the override will make into the core config.
config_save_on_exit = false
```

## Core Input Remapping

Core Input Remapping differs from the other two methods as it remaps how the core receives input rather than how the gamepad is coded, for example you can tell the snes core to switch button A and B on the controller for gameplay, but you can still use "A" to select in the RGUI and "B" to go back where as hard-coding would make B select and A back. Core Remapping is much more practical than hard-coded mapping but is limited to the cores that support it. 

Quick way to do it:

* Start a game of the system you want to remap the buttons
* Invoke RGUI (**Select+X** with player 1)
* Go to **Quick Menu** and then **Controls**
* Configure the buttons the way you want
* Select **Save Core Remap File**
* OR, if you want to save this remapping for the current game only, select **Save Game Remap File**

## Video Tutorials

* Core input remapping: [Remapping your controller](https://www.youtube.com/watch?v=liJKFUZX4PM) by Floob
* Testing Joypad: [Testing joystick](https://www.youtube.com/watch?v=fcRVcPkpLfQ) by Floob
* [Configuring USB Controllers With Retroarch, Controller not configured fix](https://www.youtube.com/watch?v=AhkEnDdygbQ) by Herb Fargus
* [Configure a wireless PS3 controller with RetroPie 3](https://www.youtube.com/watch?v=oCq6drv5wbE) by Floob
* [XBox 360 Wireless Controller Configuration](https://www.youtube.com/watch?v=IjEA85BUDKs) by Herb Fargus

## Default Core Controls for All Emulators

***

## 3do
![goldstar_3do_diagram](https://cloud.githubusercontent.com/assets/10035308/16599643/7f450bd6-42c0-11e6-84d7-9cc0944e7b01.png)
## Atari 2600
![atari2600diagram](https://cloud.githubusercontent.com/assets/10035308/8237960/02aa13fc-15b0-11e5-92c2-311e8960883b.png)
## Atari Lynx
![atari_lynx_diagram](https://cloud.githubusercontent.com/assets/10035308/16599640/7f435408-42c0-11e6-8034-d04fec9310ce.png)
## Gameboy
![gameboy](https://cloud.githubusercontent.com/assets/10035308/7334402/bd640072-eb4e-11e4-8251-d2bc3b876153.png)
## Gameboy Color
![gameboycolor](https://cloud.githubusercontent.com/assets/10035308/7334404/bd65e496-eb4e-11e4-82e6-78494534d305.png)
## Gameboy Advance
![nintendo_gameboyadvance_diagram](https://cloud.githubusercontent.com/assets/10035308/16599631/7f238b14-42c0-11e6-90e0-eac12cb4db3d.png)
## Game Gear
![segagamegeardiagram](https://cloud.githubusercontent.com/assets/10035308/8245009/b4c87e72-15e5-11e5-8ee5-691daa4d1dd5.png)
## Mastersystem
![mastersystem](https://cloud.githubusercontent.com/assets/10035308/7334954/59794038-eb60-11e4-989d-6367c1fda8ef.png)
## Megadrive/Genesis (3 Button)
![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)
## Megadrive/Genesis (6 Button)
![sega_megadrive_6button_arcadepad_diagram](https://cloud.githubusercontent.com/assets/10035308/16599641/7f43ae62-42c0-11e6-924a-50ca4e44f401.png)
![sega_megadrive_6button_diagram](https://cloud.githubusercontent.com/assets/10035308/16599642/7f43e53a-42c0-11e6-9152-c33099878ccc.png)
## Nintendo 64
![nintendo_n64_diagram](https://cloud.githubusercontent.com/assets/10035308/16599636/7f3630fc-42c0-11e6-952f-60d97a511f38.png)
## Nintendo DS
![nintendo_ds_diagram](https://cloud.githubusercontent.com/assets/10035308/16599645/7f549f56-42c0-11e6-88a8-3acda5287da3.png)
## NES
![nesdiagram](https://cloud.githubusercontent.com/assets/10035308/8245062/4f0c5b8e-15e6-11e5-9255-b920543518d6.png)
## Neo Geo
![neogeodiagram](https://cloud.githubusercontent.com/assets/10035308/8245309/a575cc8c-15e9-11e5-8735-0a4ab2a4e137.png)
## Neo Geo Pocket
![neogeopocketdiagram](https://cloud.githubusercontent.com/assets/10035308/8244887/0e06c54a-15e4-11e5-8f8f-28758d16c446.png)
## PS1
![playstation3_diagram](https://cloud.githubusercontent.com/assets/10035308/16599634/7f353148-42c0-11e6-9023-dbaf074bc933.png)
## PSP
![psp_diagram](https://cloud.githubusercontent.com/assets/10035308/16599632/7f34c9ec-42c0-11e6-8988-0b2d6e795d10.png)
## SG-1000
![sg-1000diagram](https://cloud.githubusercontent.com/assets/10035308/8238988/4aee1770-15b6-11e5-90d4-5bf66ac7e3dd.png)
## Super Nintendo
![snes](https://cloud.githubusercontent.com/assets/10035308/7334403/bd655d6e-eb4e-11e4-8fd7-a4424aad1034.png)
## Sega Saturn
![sega_saturn_diagram](https://cloud.githubusercontent.com/assets/10035308/16599639/7f42ac24-42c0-11e6-8978-5f3cce723393.png)
## Turbografx16
![turbografx16diagram](https://cloud.githubusercontent.com/assets/10035308/8239221/aa5f3602-15b7-11e5-9c9f-54322c0a18bc.png)
## Videopac/Odyssey2
![videopacdiagram](https://cloud.githubusercontent.com/assets/10035308/8236975/679e6a58-15a9-11e5-98de-4ca681404eca.png)
## Vectrex
![vectrex](https://cloud.githubusercontent.com/assets/10035308/8196876/168671c6-144e-11e5-8139-d2d980a936fa.png)
## VirtualBoy
![nintendo_virtualboy_diagram](https://cloud.githubusercontent.com/assets/10035308/16599637/7f382d3a-42c0-11e6-8e7d-bdbacf7afd82.png)
## Sega Dreamcast
![sega_dreamcast_diagram](https://cloud.githubusercontent.com/assets/10035308/16599638/7f411634-42c0-11e6-811c-456f02b2ea47.png)
## Intellivision
![intellivision](https://cloud.githubusercontent.com/assets/10035308/8246393/3e98c8c2-15fb-11e5-9398-3f5abd60361b.png)
