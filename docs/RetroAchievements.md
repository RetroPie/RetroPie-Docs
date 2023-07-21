-----------------------
![https://retroachievements.org](https://retroachievements.org/Images/RA_Logo10.png)
-----------------------
RetroAchievements are a way to log your achievements on oldschool console games. It is integrated into RetroArch and is only supported by select cores ([see list below](#supported-systems)).

**IMPORTANT NOTE**: The RetroAchievements feature is continuously being worked and improved. Then if you downloaded (or even worse: bought) a custom RetroPie image, there's a chance you have an outdated RetroArch version and face compatibility issues with the achievements feature. For a better experience, it's recommended to use the [official RetroPie image](https://retropie.org.uk/download/) and keep RetroArch and libretro cores [up to date](https://retropie.org.uk/docs/Updating-RetroPie/#updatinginstalling-individual-packages).

You first need to create an account at [retroachievements.org](https://retroachievements.org/) and then add your credentials to `/opt/retropie/configs/all/retroarch.cfg`

```
cheevos_username = "yourusername"
cheevos_password = "yourpassword"
cheevos_enable = true
```

Below you can see all the RetroAchievements related options that you can use in the `retroarch.cfg` and the explanation in the comments:

```
## RetroAchievements configs

# Enable the retroachievements feature.
cheevos_enable = "true"

# RetroAchievements.org credentials
cheevos_username = "YourUsername"
cheevos_password = "YourPassword"

# The hardcore mode makes your achievements points worth double the points.
# But it disables the savestates and other cheating features.
# It is optional and if you want to enable it, set it to true.
cheevos_hardcore_mode_enable = "true"

# If you want to see some RetroAchievements related message right after
# launching a game (such as successful login and the number of cheevos you
# have unlocked for that game), set the Achievements Verbose Mode to true.
cheevos_verbose_enable = "true"

# While playing you can see the Achievements List by calling the
# RetroArch Quick Menu. If you want to see the achievements' badges on
# that list, set this option to true (note: it has no effect if you're
# using menu_driver = rgui).
cheevos_badges_enable = "true"

# The auto screenshot feature makes RetroArch take an screenshot when
# an achievement is triggered.
cheevos_auto_screenshot = "true"

# Besides achievements, some games also have leaderboards, where you can
# compete for high-scores, speedruns, etc. To enable such feature, set 
# it to true.
cheevos_leaderboards_enable = "false"

# Sends some messages to the RetroAchievements.org saying, for example,
# where you are in the game, how many lives you have, your score, etc.
cheevos_richpresence_enable = "true"

# Unnoficial achievements are usually used only for achievement creators
# and testers. Regular users don't need this.
cheevos_test_unofficial = "false"
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
* SG-1000
* Master System
* MSX
* Game Gear
* Neo Geo Pocket
* Neo Geo Pocket Color
* Atari 2600
* Atari 7800
* Atari Lynx
* PC Engine
* PlayStation
* PlayStation Portable (PSP)
* Nintendo DS
* ColecoVision
* Arcade (Neo Geo, CPS1, CPS2 and CPS3) - *only with the fbneo core*.
* PC-8800
* and some others (check on [their page](https://retroachievements.org))

A libretro core compatibility list with RetroAchievements can be found in [libretro docs](https://docs.libretro.com/guides/retroachievements/).


## RetroAchievements Messages

A common user question is "How do I increase the size of the RetroAchievements messages on RetroArch?".

Actually this configuration is done by changing the font size of all the RetroArch widgets, not only the RetroAchievements related ones. How to do it:

Open the file `/opt/retropie/configs/all/retroarch.cfg` and add the following lines:
```
# Change Widget Size
menu_widget_scale_auto = "false"
menu_widget_scale_factor = "2.000000"
menu_widget_scale_factor_windowed = "2.000000"
```

If you prefer to configure RetroArch with RGUI (per core), you can go to `Settings` -> `On-screen Display` -> `On-screen Notifications`:
* Set `Auto Scale Graphics Widgets` to `OFF`
* Set `Graphics Widgets Scale Override` to what you like.

If you have disabled RetroArch widgets and are using old style [OSD] notifications, open the file `/opt/retropie/configs/all/retroarch.cfg` and change the line with `video_font_size`. Values between 26-32 should be good on a 40" TV.
