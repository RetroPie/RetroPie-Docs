**Please check [FinalBurn-Neo](FinalBurn-Neo.md) for for basic information about controls and managing ROMs - this page is for specific information about the _lr-fbneo_ emulator's features.**

*lr-fbneo* is a popular choice for the Raspberry Pi 2 and up, as it supports the latest FBNeo romset (v0.2.97.44), and a broad set of features. FBNeo also should always outperform MAME in the games they both support, as it is tailored for speed, rather than accuracy. Also, it is a libretro core, so enjoys all the benefits of that: centralised controller configurations, many customisation options, netplay, shader/overlay support, etc.

## System menu

By default, if you hold the Start button for a few seconds, the ROM system menu appears. Here you can set various game options, typically including 'Free Play' modes, regional settings, etc. Settings are saved in `.fs` files in the ROMS directory for the system in use, and are loaded automatically on next use.

## Dipswitches

*lr-fbneo* exposes all the dipswitch options of any given game to libretro, allowing you to adjust them via the RetroArch GUI. Hold hotkey (by default, Select) & X (the top button) to access the GUI, and then **Quick Menu** > **Options**. You should be presented by a menu where you can enable/disable the various dipswitches.

The dipswitches available will vary from game-to-game. Any changes made will be stored in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```

## High scores

*lr-fbneo* will attempt to keep a permanent record of any high scores you set, but some games will not save these by default. There is a supplementary file that is automatically installed to your Pi that will enable high score saving for more games, called `hiscore.dat`. This file is the same as that from http://highscore.mameworld.info/ (labeled "**old format hiscore.dat (pre mame v0174)**"). It is located in:
```
/home/pi/RetroPie/BIOS/fbneo/
```
When high scores are saved, they are kept in the current rom directory as `gamename.hi` files.


## Arcade layouts

*lr-fbneo* has been configured to use the SNES layout in six-button fighting games. That is:
```
+---------+
| Y  X  L |
|         |
| B  A  R |
+---------+
```
So arcade stick should be setup accordingly.

## Samples

Some sound effects in a few older (typically pre-1986) arcade games are difficult/impossible to emulate. Instead, audio clips of these effects can be downloaded and automatically played at the appropriate times. FBNeo additionally supports the use of some higher quality samples such as the CD audio rips from the console version of [Donpachi](http://adb.arcadeitalia.net/dettaglio_mame.php?game_name=donpachi). Samples are often included in a romset, or you can find some at <http://www.progettosnaps.net/samples/>. Place them into:
```
/home/pi/RetroPie/BIOS/fbneo/samples/
```

## Neo Geo UNIBIOS
For Neo Geo games, you may want to use the [UNIVERSE BIOS/UNIBIOS](http://unibios.free.fr/) - an advanced Neo Geo bios that allows region selection, cheats, dip-switch control, and more. To activate, start a Neo Geo game, hold hotkey (by default, Select) & X (the top button) to access the GUI, and then **Quick Menu** > **Options** > Change **Neo Geo mode** to **UNIBIOS**.

Note that this will automatically use the latest version of the UNIBIOS avaialble in your `neogeo.zip`. If you want to select a specific version, use the **BIOS** core option, however note that this setting applies per-game, rather than system-wide, like the **Neo Geo mode** setting.

Use the **B** button to go back to the **Quick Menu** and select **Restart Content** then **Resume Content**. You should see the Unibios boot screen before the usual "Max 330 Mega Pro-Gear Spec" screen.

Instructions on how to use the UNIBIOS can be found here: [Neo-Geo - Bios](Neo-Geo#bios).

## Neo Geo Overclocking

The Neo Geo system infamously has several games in its library that push the system beyond its original capabilities, causing slowdowns during busy moments. Metal Slug 2 is a particularly egregious example. With **lr-fbneo** you can - inauthentically - reduce and sometimes avoid such situations by 'overclocking' the emulated CPU.

> **Note:** This may have undesired effects such as increasing the music or game speed.

To do this, adjust the `CPU overclock` core option via the RetroArch GUI (accessed be **Hotkey** + **X**). By raising the number beyond 100, you increase the CPU speed. Alternatively this can be adjusted via a setting in the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
fbneo-cpu-speed-adjust = 100
```
(raise it in increments of 10, with a maximum of 200)

## Feature requests

Please use the [forum](https://retropie.org.uk/forum) for all support issues, but feature requests can be made on the [GitHub page](https://github.com/libretro/fbneo).