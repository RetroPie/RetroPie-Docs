RetroAchievements are a way to log your achievements on oldschool console games. It is integrated into RetroArch and is only supported by select cores ([see list below](#supported-systems)).

You first need to create an account at http://retroachievements.org/ and then add your credentials to `/opt/retropie/configs/all/retroarch.cfg`

```
cheevos_username = "yourusername"
cheevos_password = "yourpassword"
cheevos_enable = true
```

The Hardcore Mode disables the savestates and is optional. If you want to enable it add this line too:

```
cheevos_hardcore_mode_enable = true
```

If you want to see some more RetroAchievements related message right after launching a game (such as successfull login and the number of cheevos you have unlocked) you can use the Achievements Verbose Mode:

```
cheevos_verbose_enable = true
```

Since RetroArch 1.6.8 the RetroAchievements Leaderboards feature is also supported. You can enable it with this config:

```
cheevos_leaderboards_enable = true
```

## Supported Systems:

* NES
* SNES
* Game Boy
* Game Boy Color
* Game Boy Advance
* Nintendo 64
* Nintendo Virtual Boy
* Mega Drive / Genesis
* Master System
* Game Gear
* Neo Geo Pocket
* Neo Geo Pocket Color
* Atari 2600
* Atari Lynx
* PC Engine
* Arcade (Neo Geo, CPS1, CPS2 and CPS3)

A libretro core compatibility list with RetroAchievements can be found in [libretro docs](https://docs.libretro.com/guides/retroachievements/).

## RetroAchievements Messages

A common user question is "How do I increase the size of the RetroAchievements messages on RetroArch?".

Actually this configuration is done by changing the font size of all the RetroArch messages, not only the RetroAchievements related ones. How to do it:

Open the file `/opt/retropie/configs/all/retroarch.cfg` and change the line with `video_font_size`. Values between 26-32 should be good on a 40" TV.

If you are used to configure RetroArch with RGUI (not the default on RetroPie), you can go to `Settings` -> `Onscreen Display` -> `OSD Message Size` and change it.