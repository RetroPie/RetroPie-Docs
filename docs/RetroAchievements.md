RetroAchievements are a way to log your achievements on oldschool console games. It is integrated into RetroArch and is only supported by select cores ([see chart](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroAchievements/_edit#supported-systems)).

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

[As at 27/05/2016 achievement support is broken in the latest version of Retroarch.](https://github.com/libretro/RetroArch/issues/3032)


##Supported Systems:

* Game Boy / Color (lr-gambatte - installed by default)  
* Game Boy Advance (VBA-M, mGBA)  
* NES (lr-QuickNES - found in 'Experimental' menu, lr-fceumm - installed by default, but you have to [re]install it)
* SNES (lr-Snes9x - installed by default, lr-pocketsnes - installed by default)  
* Genesis/Mega Drive (lr-picodrive - installed by default)  
* Sega 32x (lr-picodrive - installed by default)

To enable lr-fceumm for achievements you have to follow the instructions [here](https://github.com/retropie/RetroPie-Setup/wiki/Updating-RetroPie) to install it. Summing up:

Access the terminal and
```
cd RetroPie-Setup
sudo ./retropie_setup.sh
```
Go to **Install Individual Emulators from Binary or Source**, choose lr-fceumm and install it from binary. After that the lr-fceumm is able to register your achievements.