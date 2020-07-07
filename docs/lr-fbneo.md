**Please check [FinalBurn-Neo](FinalBurn-Neo.md) for for basic information about controls and managing ROMs - this page is for specific information about the _lr-fbneo_ emulator's features.**

*lr-fbneo* is a popular choice for the Raspberry Pi 2 and up, as it supports the latest FBNeo romset (v0.2.97.44), and a broad set of features. FBNeo also should always outperform MAME in the games they both support, as it is tailored for speed, rather than accuracy. Also, it is a libretro core, so enjoys all the benefits of that: centralised controller configurations, many customisation options, netplay, shader/overlay support, etc.

## System menu

By default, if you hold the Start button for a few seconds, the ROM system menu appears. Here you can set various game options, typically including 'Free Play' modes, regional settings, etc. Settings are saved in `.fs` files in the ROMS directory for the system in use, and are loaded automatically on next use.

## Dipswitches

*lr-fbneo* exposes all the dipswitch options of any given game as **Core Options**. See [Setting Core Options](RetroArch-Core-Options#setting-core-options). The dipswitches available will vary from game-to-game.

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
For Neo Geo games, you may want to use the [UNIVERSE BIOS/UNIBIOS](http://unibios.free.fr/) - an advanced Neo Geo bios that allows region selection, cheats, dip-switch control, and more. To active, change the **Core Option** for **Neo Geo mode** to **UNIBIOS**. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

Note that this will automatically use the latest version of the UNIBIOS avaialble in your `neogeo.zip`. If you want to select a specific version, use the **BIOS** Core Option, however note that this setting applies per-game, rather than system-wide, like the **Neo Geo mode** setting.

Use the **B** button to go back to the **Quick Menu** and select **Restart Content** then **Resume Content**. You should see the Unibios boot screen before the usual "Max 330 Mega Pro-Gear Spec" screen.

Instructions on how to use the UNIBIOS can be found here: [Neo-Geo - Bios](Neo-Geo#bios).

## Neo Geo Overclocking

The Neo Geo system infamously has several games in its library that push the system beyond its original capabilities, causing slowdowns during busy moments. Metal Slug 2 is a particularly egregious example. With **lr-fbneo** you can - inauthentically - reduce and sometimes avoid such situations by 'overclocking' the emulated CPU.

> **Note:** This may have undesired effects such as increasing the music or game speed.

Change the **Core Option** for **CPU overclock**. See [Setting Core Options](RetroArch-Core-Options#setting-core-options). By raising the number beyond 100, you increase the CPU speed.

## Feature requests

Please use the [forum](https://retropie.org.uk/forum) for all support issues, but feature requests can be made on the [GitHub page](https://github.com/libretro/fbneo).