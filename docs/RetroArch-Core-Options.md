## RetroArch Core Options

RetroArch Cores (emulators) typically have options unique to them, known as Core Options. They are adjusted and stored in a different way to the general RetroArch configuration.

### Setting Core Options

Whilst a ROM for the Core in question is running, enter the RGUI via holding player 1's [Hotkey](Controller-Configuration#hotkey) combination **Hotkey+X**. This puts you in the **Quick Menu**. Navigate down to the **Core Options** sub-menu and press **RetroPad A** (typically the east action button) to confirm.

Within this sub-menu are all the options available to that Core. Navigate to the one you want and press left and right to select the desired value. To apply, exit the RGUI using the previous combo. Some options will require you to restart the ROM to take effect. Core Options are saved automatically when you exit the ROM.

### Setting Core Options per-ROM

You may prefer to apply Core Options to a specific ROM, and not for all ROMs within that core. To do so, follow the above instructions, but instead of exiting the RGUI at the end, select **Manage Core Options ▶ Save Game Options** at the top of the Options menu. This will create a Core Options `.opt` file specifically for that ROM within:

```
/opt/retropie/configs/all/retroarch/config/core
```
(where `core` is the name of the libretro Core)

The file will be `ROMname.opt`. To remove the configuration, delete the file or use the **Manage Core Options** submenu to delete it.

### retroarch-core-options.cfg

The Core Options are stored in the following location:
```
/opt/retropie/configs/all/retroarch-core-options.cfg
```

The file is populated with some defaults set by RetroPie during emulator installation, and the RetroArch cores will add the remaining Core Options with their own defaults. You should never need to add a new line to this file, as once a core is run, the Core Option's current setting will be added to the file. Example entries:

```
snes9x_aspect = "4:3"
snes9x_audio_interpolation = "gaussian"
snes9x_blargg = "disabled"
snes9x_block_invalid_vram_access = "enabled"
snes9x_echo_buffer_hack = "disabled"
```

Options are in the format `emulatorname_option_name = "value"`
