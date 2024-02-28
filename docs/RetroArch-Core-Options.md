## RetroArch Core Options

RetroArch Cores (emulators) typically have options unique to them, known as Core Options. They are adjusted and stored in a different way to the general RetroArch configuration.

### Setting Core Options

Whilst a ROM for the Core in question is running, enter the RGUI via holding Player 1's [Hotkey](Controller-Configuration#hotkey) combination **Hotkey+X**. This puts you in the **Quick Menu**. Navigate down to the **Core Options** sub-menu and press **RetroPad A** (typically the east action button) to enter the sub-menu.

Within this sub-menu are all the options available to that Core. Depending on the Core used, the options could be organized under _Categories_, which group related options under a sub-menu. Navigate to the option that you want to change and press left and right to select the desired value or **RetroPad A** to open the list of available values and select from it. To apply, just close the RGUI/menu using the same Hotkey combination used to open it (**Hotkey+X**). 

**NOTE:** Some options will require you to restart the ROM to take effect, they're usually marked as such in the list of options. Core Options are saved automatically when you exit the ROM/close the emulator.

### Setting Core Options per-ROM

You may prefer to apply Core Options to a specific ROM, and not for all ROMs within that core. To do so, follow the above instructions, but instead of exiting the RGUI at the end, select **Manage Core Options ▶ Save Game Options** at the top of the Options menu. This will create a Core Options `.opt` file specifically for that ROM within:

```
/opt/retropie/configs/all/retroarch/config/core
```
(where `core` is the name of the libretro Core)

The file will be `ROMname.opt`. To remove the configuration, delete the file or use the **Manage Core Options** submenu to delete it.

### Core Options File

The Core Options are stored in the following location
```
/opt/retropie/configs/all/retroarch-core-options.cfg
```

The file is populated with some defaults set by RetroPie during emulator installation, and the RetroArch cores will add the remaining Core Options with their own defaults. You should never need to add a new line to this file, as once a core is run, the Core Option's current setting will be added to the file. Example entries:

``` ini
snes9x_aspect = "4:3"
snes9x_audio_interpolation = "gaussian"
snes9x_blargg = "disabled"
snes9x_block_invalid_vram_access = "enabled"
snes9x_echo_buffer_hack = "disabled"
```

Options are in the format `emulatorname_option_name = "value"`
