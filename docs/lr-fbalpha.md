**Please check [[FinalBurn-Alpha]] for for basic information about controls and managing ROMs - this page is for specific information about the lr-fbalpha emulator's features.**

lr-fbalpha is a popular choice for the Raspberry Pi 2 and up, as it supports the latest FBA romset (v0.2.97.38), and a broad set of features. FBA also should always outperform MAME in the games they both support, as it is tailored for speed, rather than accuracy. Also, it is a libretro core, so enjoys all the benefits of that: centralised controller configurations, many customisation options, netplay, shader/overlay support, etc.

## System menu

By default, if you hold the Start button for a few seconds, the system menu appears. Here you can set various game options, typically including 'Free Play' modes, regional settings, etc. Settings are saved in .fs files in the ROMS directory for the system in use, and are loaded automatically on next use.

## Dipswitches

lr-fbalpha exposes all the dipswitch options of any given game to libretro, allowing you to adjust them via the RetroArch GUI. Hold hotkey (by default, Select) & X (the top button) to access the GUI, and then **Quick Menu** > **Options**. You should be presented by a menu like: 

![](http://www.zimagez.com/full/aaa69d795c1a5e2d817defaa1cf6b75424d4e11b61c059d71a69dbf0077a5a4ba365eb42e08b34d8.php)

The dipswitches available will vary from game-to-game. Any changes made will be stored in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```

## Button rebinding

lr-fbalpha supports a useful feature where you can rebind the keys for individual games, without impacting the internal libretro hotkey macros (select & R = quicksave, etc). These rebinding options are accessed and saved in the same way as the dipswitches above.

## Samples

Some sound effects in a few older (typically pre-1986) arcade games are difficult/impossible to emulate. Instead, audio clips of these effects can be downloaded and automatically played at the appropriate times. FBA additionally supports the use of some higher quality samples such as the CD audio rips from the console version of Donpachi. Samples are often included in a romset, or you can find some at http://www.progettosnaps.net/samples/. Place them into:
```
/home/pi/RetroPie/BIOS/fba/samples/
```

## Neo Geo UNIBIOS
For Neo Geo games, you may want to use the [UNIVERSE BIOS/UNIBIOS](http://unibios.free.fr/) - an advanced Neo Geo bios that allows region selection, cheats, dip-switch control, and more. To activate, start a Neo Geo game, hold hotkey (by default, Select) & X (the top button) to access the GUI, and then **Quick Menu** > **Options** > Change **Neo Geo mode** to **UNIBIOS**.

Note that this will automatically use the latest version of the UNIBIOS avaialble in your `neogeo.zip`. If you want to select a specific version, use the **BIOS** core option, however note that this setting applies per-game, rather than system-wide, like the **Neo Geo mode** setting.

Use the **B** button to go back to the **Quick Menu** and select **Restart Content** then **Resume Content**. You should see the Unibios boot screen before the usual "Max 330 Mega Pro-Gear Spec" screen.

Instructions on how to use the UNIBIOS can be found here: [[Neo-Geo#using-the-universe-bios-unibios]]

## Feature requests

Please use the [forum](https://retropie.org.uk/forum) for all support issues, but feature requests can be made on the [GitHub page](https://github.com/libretro/libretro-fba).