# EmulationStation
# Introduction

This is the graphical front-end installed by RetroPie. EmulationStation is designed to allow you to use your Pi as if it were a retro console - with only a controller, not requiring a keyboard. 

It was developed specifically for the Raspberry Pi, on the Raspberry Pi. However, it uses cross-platform libraries, so it can be run on pretty much any Linux machine. If you try, you can also build it on Windows.

From the dictionary:
> # front end
>1. the front of a car or other vehicle.
>2. the part of a radio or television receiver to which the aerial signal goes first.
>3. **COMPUTING - a part of a computer or program that allows access to other parts.**

EmulationStation is used to provide a polished user interface to present and interact with all the different aspects of the RetroPie distribution. It allows the user to use a UI that is controllable using a joypad or arcade controllers to navigate through the different emulators, and make (simple) edits to the systems configuration.

As it is the first thing that many users see, EmulationStation is often conflated with RetroPie as a whole, while ES is only a part of the RetroPie distribution.

EmulationStation was developed by Alec Lofquist (programming) and Nils Bonenberger (design & UI), see the [official EmulationStation page](http://www.emulationstation.org/). For the code and more info, see also the [Github Repository](https://github.com/Aloshi/EmulationStation).

# Features
EmulationStation offers the following features:
* Listing of emulated systems (systemlist), and their respective games (gamelist)
* Keyboard-less navigation
* Controller configuration which is propagated to RetroArch emulators
* Theming of certain elements (background, position/size of text elements)
* Scraping of game information (see [here for more info](https://github.com/retropie/retropie-setup/wiki/scraper))

# Development status
Since spring 2015, there has been little or no activity from the original ES developer, Aloshi. Recently, there has been some activities to get the project moving again (see the [discussion here](https://github.com/Aloshi/EmulationStation/issues/563#issuecomment-198787794)). It remains to be seen if this will gather enough momentum to become a viable alternative for RetroPie or not.
Until that time, further developments are done by 'unofficial' forks, which are not necessarily maintained/updated often. One example is [this extension of ES](https://github.com/retropie/retropie-setup/wiki/Child-friendly-EmulationStation), which is currently under experimental features.

# Help
A great deal of information can be found in EmulationStation's README.md and THEMES.md, also viewable on GitHub. Some links:

[Building from source (if you're getting dependency errors, this might help).](https://github.com/Aloshi/EmulationStation#building)

[Configuring EmulationStation.](https://github.com/Aloshi/EmulationStation#configuring)

[Creating your own themes.](https://github.com/Aloshi/EmulationStation/blob/master/THEMES.md#themes)

## Common Problems
### When I start a game, I lose keyboard input and have to power off to reboot!

**DON'T START EMULATIONSTATION FROM X.** RetroArch expects keyboard input to be from the normal terminal, *not* a terminal window in X. To fix this, either:
* Close X
* Reboot and run ES before you start X
* Or open a terminal with Ctrl+Alt+F1 through F6. Press Ctrl+Alt+F7 to return to X (though remember X will still be running and take up some RAM).


### My ES_Sytems.cfg is being overwritten on updates!

When you install themes from the retropie setup script they are installed to `/etc/emulationstation` and are overwritten when new themes are installed or RetroPie is updated.

If you want to customise your es_systems.cfg or add themes without them being overwritten on udates you can add them to `/home/pi/.emulationstation` EmulationStation first checks in `/home/pi/.emulationstation` and then checks `/etc/emulationstation`. 


### EmulationStation isn't detecting my ROMs!

* Are they in the right folders? *Remember, paths are case sensitive*. You can check what folders ES is using with: `nano /etc/emulationstation/es_systems.cfg`.
* Is ES looking for the right file extension? *Remember, the extension is case sensitive*. You can check what format ES is searching with: `nano /etc/emulationstation/es_systems.cfg`. 
* Are your ROMs in a compressed format? *EmulationStation does not search inside zip files*, though some emulators (like MAME) will expect a zip file.


### All I see is the Linapple 2 screen! Where are the rest of the emulators?

You've gone one screen too far ;) Press `F10` to get back to the Apple II start screen and use the left and right arrows to navigate between the emulators.


### How do I hide unused/unwanted systems?

You can hide unused systems by either removing the relevant roms in the system folder or navigating to ```/etc/emulationstation``` and opening the ```es_systems.cfg``` file. Using ```<!--``` and ```-->``` on a systems entry will hide it from the frontend GUI.

You can also just move the rom folders for the systems you don't want into a folder you create called unused.

### My emulator won't close through my gamepad!

This is normal. ES does not monitor input while an emulator is running. If you want to close your emulator, you will have to do it from within the emulator. RetroArch has a binding for this, just add it to your RetroArch config file: `input_exit_emulator_btn = “6″` would map it to button 6 on a gamepad. You should be able to figure out what button to use by running RetroArch's joystick configuration tool (check the `RetroPie/RetroArch-Rpi/tools/` directory).

[If you are using an "authentic" controller and don't have an extra button to use, try this.](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=250689#p250689)

### All I see is this weird white dot in the middle of the screen!

This dot is the "fake" SDL window ES uses to get input. Actual rendering is done through OpenGL ES. If all you see is this dot, then odds are something went wrong initializing the OpenGL ES surface. Are you sure you're running at least the 192/64mb memory split?

### ES doesn't detect my controller when started at boot!

Your controller driver is likely being started after EmulationStation. An easy way around this is to add a "sleep" command in the EmulationStation start script in `/usr/bin/emulationstation`.  [More information here.](http://www.reddit.com/r/raspberry_pi/comments/16w9qn/emulationstation_and_a_logitech_dual_action/c816dz1)

### I don't have enough buttons to finish the Input Config screen?!

[Work-around here.](https://github.com/Aloshi/EmulationStation/issues/67#issuecomment-16715011)

### I messed up on the initial prompt that appears when Emulation Station starts for the first time. My controls are completely messed up and out of order. Is there a way to redo this prompt?

You need to delete the configuration file that Emulation Station uses by invoking ```rm /home/pi/.emulationstation/es_input.cfg```, and then re-install Emulation Station from Retropie-Setup. Note that you exit Emulation Station by pressing ```F4```. When you (re-)start Emulation Station, the configuration prompt will appear again.

# Alternative Frontends
Because of the development hiatus, there has been some attention towards other front-ends.
* Attract-Mode ([site](http://attractmode.org/), [forum thread](https://retropie.org.uk/forum/topic/93/attract-mode-with-retropie-alternative-to-emulationstation))
* mehstation ([site](https://remy.io/mehstation))
