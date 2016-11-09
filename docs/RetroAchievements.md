RetroAchievements are a way to log your achievements on oldschool console games. It is integrated into RetroArch and is only supported by select cores ([see chart](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroAchievements/#supported-systems)).

You first need to create an account at http://retroachievements.org/ and then add your credentials to `/opt/retropie/configs/all/retroarch.cfg`

```
cheevos_username = "yourusername"
cheevos_password = "yourpassword"
cheevos_enable = true
```

Since RetroArch 1.3.2 (used in RetroPie 3.7), the Hardcore Mode is supported. It disables the savestates and is optional. If you want to enable it add this line too:

```
cheevos_hardcore_mode_enable = true
```


##Supported Systems:

* NES (lr-fceumm - installed by default, lr-quicknes - found in 'Optional' menu, seems to have the best compatibility)
* SNES (lr-Snes9x-next, lr-pocketsnes, lr-armsnes - installed by default)  
* Genesis/Mega Drive (lr-picodrive - installed by default)
* Game Boy / Color (lr-gambatte - installed by default)  
* Game Boy Advance (lr-vba-next - installed by default, lr-mgba - installed by default, seems to have the best compatibility)

##RetroAchievements Messages

A commom user question is "How do I increase the size of the RetroAchievements messages on RetroArch?".

Actually this configuration is done by changing the font size of all the RetroArch messages, not only the RetroAchievements related ones. How to do it:

Open the file `/opt/retropie/configs/all/retroarch.cfg` and change the line with `video_font_size`. Values between 26-32 should be good on a 40" TV.

If you are used to configure RetroArch with RGUI (not the default on RetroPie), you can go to `Settings` -> `Onscreen Display` -> `OSD Message Size` and change it.