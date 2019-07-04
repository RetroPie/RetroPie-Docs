**Please check the [MAME documentation](../wiki/MAME) for for basic information about controls and managing ROMs - this page is for specific information about the mame2003 emulator's features.**

lr-mame2003 is a popular choice for the Raspberry Pi 2 and up, as it combines a large romset (MAME 0.78) playing host to most 2D-era arcade games that people would be interested in, and a broad set of features. It also is still a relatively old MAME core, which is actually a good thing for lower-end hardware such as the Raspberry Pis, as later MAME cores feature increasingly accurate emulation which requires greater CPU power. Also, it is a libretro core, so enjoys all the benefits of that: centralised controller configurations, many customisation options, netplay, shader/overlay support, etc.

## MAME menu

To access the MAME internal menu, press the 'TAB' key or R2.

Whilst lr-mame2003 is a libretro emulator and benefits from automatic controller configuration, sometimes you may still want to rebind how it internally deals with inputs. For example, the default control setup might make sense in one game, but in another they don't. In which case, you can use the 'Input (this game)' option to rebind keys for a single game, generating a .cfg file in:
```
/home/pi/RetroPie/roms/mame-libretro/mame2003/cfg/
```
or, if you're using the arcade folder:
```
/home/pi/RetroPie/roms/arcade/mame2003/cfg/
```
If you rebind global inputs ('Input (general)'), it will update a file in the same directory called `default.cfg`.

These files are not human-readable, but can be safely deleted if you get into a mess and wish to return to the default configuration.

## Service menu

To access the MAME service, press the 'F2' key.

lr-mame2003 has the useful ability to access games' internal service menus to set permanent game options. This allows you to, for example, configure a game to be 'free play' (no need to insert coins). After changing options in the service mode, the game's internal memory will be stored to an .nv file in:
```
/home/pi/RetroPie/roms/mame-libretro/mame2003/nvram/
```
or, if you're using the arcade folder:
```
/home/pi/RetroPie/roms/arcade/mame2003/nvram/
```

## Dip-switches

Similarly to the [Service menu](#service-menu), many arcade games had hardware switches for arcade owners to modify certain parameters. These can be adjust by pressing the 'TAB' key to access the [MAME menu](#mame-menu), and select the '**Dip Switches**' option. Here you can turn them on/off.

## High scores

lr-mame2003 will attempt to keep a permanent record of any high scores you set. A supplementary file called `hiscore.dat` used to be required for these ROMs to save scores. This file can be [downloaded from the MAME 2003 'metadata' repository](https://raw.githubusercontent.com/libretro/mame2003-libretro/master/metadata/). Today this file is built into mame2003 and the only reason to use the standalone `hiscore.dat` file is for development and experimentation.

When high scores are saved by the mame2003 hiscore engine, they are kept in:
```
/home/pi/RetroPie/roms/mame-libretro/mame2003/hi/
```
or, if you're using the arcade folder:
```
/home/pi/RetroPie/roms/arcade/mame2003/hi/
```

## Cheats

lr-mame2003 supports the MAME cheat engine, allowing you to use cheats via the MAME menu by pressing `Tab`. To active these, there is a supplementary file that you need to transfer to your Pi, called `cheat.dat`. The RetroPie Setup script copies this file automatically to the correct location for you:
```
/home/pi/RetroPie/BIOS/mame2003/
```


## Samples

Some sound effects in a few older (typically pre-1986) arcade games are difficult/impossible to emulate. Instead, audio clips of these effects can be downloaded and automatically played at the appropriate times. To do this, download the sample files you require and place the .zip files into:
```
/home/pi/RetroPie/BIOS/mame2003/samples/
```
## Sample rate

You can adjust the sample rate for _all_ audio. Lowering it from the default of 48000 KHz may increase performance, at the cost of audio fidelity. It can be controlled via a setting in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
mame2003_sample_rate = "48000"
```
The valid possibilities are 8000, 11025, 22050, 44100 and 48000.

## Nag-screen

The copyright warning should be hidden by default, but can be controlled via a setting in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
mame2003_skip_disclaimer = "enabled"
```

## Skip warnings screen

Games that feature incomplete emulation, or other side-effects will have a warning screen detailing these flaws similar to the 'nag screen' mentioned above. It is recommended to leave this screen visible to understand why a game may have such issues, but it can be controlled via a setting in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
mame2003_skip_warnings = "enabled"
```

## Mouse/Trackball/Analog Controller support

By default, mice/trackballs and analog sticks (the left one, for controllers with 2) are supported in games that would have them, or equivalents. For example, Centipede supports the mouse/trackball, and Afterburner supports the stick. Lightgun games are supported by either. The left and right mouse buttons can be bound to fire/etc using the [MAME menu](#mame-menu).

## Pointer/Trackpad/Touchscreen support

Absolute pointer devices are supported, but need to be turned on via a setting in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
mame2003_mouse_device = "pointer"
```
**NOTE:** This will disable [Mouse support](#mousetrackballanalog-controller-support).

## 2 player dial/spinner devices

Some (all?) 2 player spinner/dial devices are represented as 1 device with 2 axes. lr-mame2003 can be configured to share this device across both players: Player 1 = X axis, Player 2 = Y axis. This can be enabled via a setting in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
mame2003_dialsharexy = "enabled"
```

## Dual stick games

The right analog stick can now be used a second joystick. This is enabled by default, via a setting in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
mame2003_rstick_to_btns = "enabled"
```

## TATE mode

For users who have a rotatable display, this mode shows vertical games (e.g. Pac-Man, Centipede, Galaga, etc) at their original aspect ratio, and will display along the length of the screen with the right configuration. This is disabled by default, but can be enabled via a setting in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
mame2003_tate_mode = "enabled"
```
In addition to this, you will want to stop rotating the games and instead show them in along the length of the screen, `video_allow_rotate` in mame-libretro/arcade to false via the [Configuration Editor](Configuration-Editor.md).

## Save states
Beyond [High scores](#high-scores), lr-mame2003 supports save states through the [usual Retroarch hotkeys](https://github.com/retropie/retropie-setup/wiki/retroarch-configuration#default-joypad-hotkeys). However, save state support has to be implemented per-driver, so they won't work with all games.

## Backdrops and bezels

Backdrops (and bezels too!) will work if you have the artwork in ```~/RetroPie/BIOS/mame2003/artwork```. It doesn't work if they are in the `/roms` folder, which is where you usually put them if you are using AdvMame or mame4all.

They need to be in the old MAME format (a `.zip` file containing images and an `.art` file) and *not* the new MAME format (a `.zip` containing a `.lay` file and images). Artwork in the old format can be downloaded from Mr Do's discontinued artwork page at lowish resolution, but there are higher-quality sources out there for individual games. Don't confuse artwork intended for a 1080p Retroarch *overlay* with MAME artwork files.

Once you have copied the files to the right location, you can go into RGUI -> Quick Menu -> Options -> Display artwork and set it to enabled. You will have to exit the emulator altogether and launch the game, but it will save the preference for artwork for all games.

This setting and the artwork resolution setting are saved in ```/opt/retropie/configs/all/retroarch-core-options.cfg``` as 
```
mame2003_display_artwork = "enabled"
mame2003_art_resolution = "1"
```
In lr-mame you cannot use ```-nobezel``` on a command line to selectively show only the backdrop and not the bezel, in case you wanted to use overlays for bezels, cf https://retropie.org.uk/forum/topic/21495/passing-rom-specific-command-line-options-to-mame-through-retroarch.

Unlike Retroarch overlays, MAME backdrops and bezels *are* affected by custom settings (RGUI -> Settings -> Video) because they are drawn within the core, not on top of it like overlays are.

## Feature requests

Please use the [forum](https://retropie.org.uk/forum) for all support issues, but feature requests can be made on the [GitHub page](https://github.com/libretro/mame2003-libretro).