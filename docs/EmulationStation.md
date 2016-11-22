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
A great deal of information can be found in EmulationStation's [README.md](https://github.com/Aloshi/EmulationStation/blob/master/README.md) and [THEMES.md](https://github.com/Aloshi/EmulationStation/blob/master/THEMES.md), also viewable on GitHub. Some links:

[Building from source (if you're getting dependency errors, this might help).](https://github.com/Aloshi/EmulationStation#building)

[Configuring EmulationStation.](https://github.com/Aloshi/EmulationStation#configuring)

[Creating your own themes.](https://github.com/Aloshi/EmulationStation/blob/master/THEMES.md#themes)

## Common Problems


### My ES_Sytems.cfg is being overwritten on updates!

When you install themes from the retropie setup script they are installed to `/etc/emulationstation` and are overwritten when new themes are installed or RetroPie is updated.

If you want to customise your es_systems.cfg or add themes without them being overwritten on updates you can add them to `/home/pi/.emulationstation` EmulationStation first checks in `/home/pi/.emulationstation` and then checks `/etc/emulationstation`.

For customising themes you'll place them in `/home/pi/.emulationstation/themes` 


### EmulationStation isn't detecting my ROMs!

* Are they in the right folders? *Remember, paths are case sensitive*. You can check what folders ES is using with: `nano /etc/emulationstation/es_systems.cfg` or better yet look at the documentation here on the wiki.
* Is ES looking for the right file extension? *Remember, the extension is case sensitive*. You can check what format ES is searching with: `nano /etc/emulationstation/es_systems.cfg` and again see the pages here on the wiki
* Are your ROMs in a compressed format? *EmulationStation does not search inside zip files*, though some emulators (like MAME) will expect a zip file.


### All I see is the Amiga screen! Where are the rest of the emulators?

You've gone one screen too far ;) Press `B` to get back to the system screen and use the left and right arrows to navigate between the emulators. If you are wondering why some systems aren't there you need to add roms to their respective folders first before that system will show up.

### How do I hide unused/unwanted systems?

You can delete the rom folders for the systems you don't want or you can move the rom folders you dont want into a folder you create called unused.

### How do I change the order of the systems in EmulationStation?

The systems will appear in EmulationStation in the same order as they appear in the file `es_systems.cfg`. The order can be changed by editing this file so, first of all before you make any edits exit emulationstation by pressing f4 or exiting from the start menu. copy `/etc/emulationstation/es_systems.cfg` to the `/home/pi/.emulationstation` folder.

Now edit es_systems.cfg, moving systems, everything from `<system>...</system>`, to the order you are looking for. To keep things tidy, you can delete systems that you are not using.

Bear in mind that, if you update any systems, this will be reflected in `/etc/emulationstation/es_systems.cfg` and you will need to manually update your copy in `/home/pi/.emulationstation`.

### My emulator won't close through my gamepad!

This sometimes happens. ES does not monitor input while an emulator is running. If you want to close your emulator, you will have to do it from within the emulator. RetroArch has a binding for this and should automatically be generated when you first configure your controller in emulationstation. default to exit is `select+start`, see [Here](https://github.com/retropie/retropie-setup/wiki/RetroArch-Configuration) for more info.

### All I see is this weird white dot in the middle of the screen!

This dot is the "fake" SDL window ES uses to get input. Actual rendering is done through OpenGL ES. If all you see is this dot, then odds are something went wrong initializing the OpenGL ES surface. Are you sure you're running at least the 192/64mb memory split?

### ES doesn't detect my controller when started at boot!

Your controller driver is likely being started after EmulationStation. An easy way around this is to add a "sleep" command in the EmulationStation start script in `/usr/bin/emulationstation`.  [More information here.](http://www.reddit.com/r/raspberry_pi/comments/16w9qn/emulationstation_and_a_logitech_dual_action/c816dz1)

### How do I add another controller to navigate and control ES?

Open the Main Menu by pressing ```Start``` on the original controller that you have already setup. Then navigate to Configure Input and press ```A``` to start. Now on the other controller press and hold down any button. This should bring up the option to setup this controller. Just follow the on-screen directions. When finished, navigate to the OK button on screen, then press the button that you set as ```A``` on your recently configured controller to exit.

### I don't have enough buttons to finish the Configure Input screen?!

Just hold down a button to skip each unused button until you get to the end of the configuration

### I messed up on the initial prompt that appears when Emulation Station starts for the first time. My controls are completely messed up and out of order. Is there a way to redo this prompt?

You need to delete the configurations you've made in `/home/pi/.emulationstation/es_input.cfg` but IMPORTANT: YOU NEED TO KEEP IN THE FOLLOWING LINES IF YOU WANT AUTOCONFIGURATIONS TO WORK:

```
  <inputAction type="onfinish">
    <command>/opt/retropie/supplementary/emulationstation/scripts/inputconfiguration.sh</command>
  </inputAction>
```

If you lose the config you can re-install Emulation Station from Retropie-Setup. Note that you exit Emulation Station by pressing ```F4```. When you (re-)start Emulation Station, the configuration prompt will appear again.

### Page-Up and Page-Down
When configuring the inputs in EmulationStation, take into account that the Left Shoulder button will be used for Page-Up and the Right shoulder button will be used for Page-Down in the EmulationStation user interface. This in particular applies to using the keyboard with EmulationStation, you should map Left Shoulder and Right Shoulder to Page-Up and Page-Down respectively.

# Alternative Frontends
Because of the development hiatus, there has been some attention towards other front-ends.
* Attract-Mode ([site](http://attractmode.org/), [forum thread](https://retropie.org.uk/forum/topic/93/attract-mode-with-retropie-alternative-to-emulationstation))
* mehstation ([site](https://remy.io/mehstation))
