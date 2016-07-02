RetroAchievements are a way to log your achievements on oldschool console games. It is integrated into RetroArch and is only supported by select cores ([see chart](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroAchievements/#supported-systems)).

You first need to create an account at http://retroachievements.org/ and then add your credentials to `/opt/retropie/configs/all/retroarch.cfg`

```
cheevos_username = yourusername
cheevos_password = yourpassword
cheevos_enable = true
```

Since RetroArch 1.3.2 (used in RetroPie 3.7), the Hardcore Mode is supported. It disables the savestates and is optional. If you want to enable it add this line too:

```
cheevos_hardcore_mode_enable = true
```


##Supported Systems:

* Game Boy / Color (lr-gambatte - installed by default)  
* Game Boy Advance (VBA-M - installed by default, mGBA - installed by default)
* NES (lr-fceumm - installed by default, lr-QuickNES - found in 'Experimental' menu)
* SNES (lr-Snes9x-next, lr-pocketsnes, lr-armsnes - installed by default)  
* Genesis/Mega Drive (lr-picodrive - installed by default)