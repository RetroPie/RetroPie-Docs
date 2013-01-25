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

* Are they in the right folders? *Remember, paths are case sensitive*. You can check what folders ES is using with: `nano ~/.emulationstation/es_systems.cfg`.
* Is ES looking for the right file extension? *Remember, the extension is case sensitive*. You can check what format ES is searching with: `nano ~/.emulationstation/es_systems.cfg`. 
* Are your ROMs in a compressed format? *EmulationStation does not search inside zip files*, though some emulators (like MAME) will expect a zip file.


### My emulator won't close through my gamepad!

This is normal. ES does not monitor input while an emulator is running. If you want to close your emulator, you will have to do it from within the emulator. RetroArch has a binding for this, just add it to your RetroArch config file: `input_exit_emulator_btn = “6″` would map it to button 6 on a gamepad. You should be able to figure out what button to use by running RetroArch's joystick configuration tool (check the `RetroPie/RetroArch-Rpi/tools/` directory).

[If you are using an "authentic" controller and don't have an extra button to use, try this.](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=250689#p250689)

### All I see is this weird white dot in the middle of the screen!

This dot is the "fake" SDL window ES uses to get input. Actual rendering is done through OpenGL ES. If all you see is this dot, then odds are something went wrong initializing the OpenGL ES surface. Are you sure you're running at least the 192/64mb memory split?

### These themes look wrong...

At the moment, themes are designed around the "detailed" game list - they're meant to look [like this](http://aloshi.com/emulationstation#themes). If you don't have a gamelist.xml for at least one system, the basic view is used, which looks incorrect. This will be rectified with the newest set of themes, once RetroPie-Setup is updated to include them.

### ES doesn't detect my controller when started at boot!

Your controller driver is likely being started after EmulationStation. An easy way around this is to add a "sleep" command in the EmulationStation start script in `/usr/bin/emulationstation`.  [More information here.](http://www.reddit.com/r/raspberry_pi/comments/16w9qn/emulationstation_and_a_logitech_dual_action/c816dz1)