# EmulationStation
This is the graphical front-end installed by RetroPie. It was developed by a guy named Aloshi, and is designed to allow you to use your Pi as if it were a retro console - with only a controller, not requiring a keyboard (after the initial setup). 

It was developed specifically for the Raspberry Pi, on the Raspberry Pi. However, it uses cross-platform libraries, so it can be run on pretty much any Linux machine. 

# Help
A great deal of information can be found in EmulationStation's README.md and THEMES.md, also viewable on GitHub. Some links:

[Building from source (if you're getting dependency errors, this might help).](https://github.com/Aloshi/EmulationStation#building)

[Configuring EmulationStation.](https://github.com/Aloshi/EmulationStation#configuring)

[Creating your own themes.](https://github.com/Aloshi/EmulationStation/blob/master/THEMES.md#themes)

# Common Problems
### When I start a game, I lose keyboard input and have to power off to reboot!

**DON'T START EMULATIONSTATION FROM X.** RetroArch expects keyboard input to be from the normal terminal, *not* a terminal window in X. To fix this, either:
* Close X
* Reboot and run ES before you start X
* Or open a terminal with Ctrl+Alt+F1 through F6. Press Ctrl+Alt+F7 to return to X (though remember X will still be running and take up some RAM).


### EmulationStation isn't detecting my ROMs!

* Are they in the right folders? You can check what folders ES is using with `nano ~/.emulationstation/es_systems.cfg`.
* Is ES looking for the right format? You can check what format ES is searching with `nano ~/.emulationstation/es_systems.cfg`.
* Are your ROMs in a compressed format? EmulationStation *does not* search inside zip files, though some emulators (like MAME) will expect a zip file.


### My emulator won't close through my gamepad!

This is normal. ES does not monitor input while an emulator is running. If you want to close your emulator, you will have to do it from within the emulator. RetroArch has a binding for this, just add it to your RetroArch config file: `input_exit_emulator_btn = “6″` would map it to button 6 on a gamepad. You should be able to figure out what button to use by running RetroArch's joystick configuration tool (check the `/tools/` directory).