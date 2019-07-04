***

![Adventure Game Studio](http://i.imgur.com/eBMyMvj.png)

***
_Adventure Game Studio is an open source development tool that is primarily used to create graphic adventure games._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [AGS](https://github.com/adventuregamestudio/ags/tree/master/debian) | ags | .exe | none | mouse |
## Emulator: [AGS](https://github.com/adventuregamestudio/ags/tree/master/debian) 



## ROMS
Accepted File Extensions: **.exe**

Place your AGS files in
```
/home/pi/RetroPie/roms/ags
```

## Troubleshooting
Ensure that you have RetroPie-Setup script version 4.3.8 or later before installing AGS, as several issues (such as content not appearing in EmulationStation and MIDI music playback) have been fixed.

## Video issues - window manager and graphics driver
More recent Retropie images have not included a desktop or window manager as part of the image (including many Xorg libraries).  It also does not automatically enable OpenGL drivers (which are still experimental).  In contrast, when installing the AGS package it relies on Xorg as it uses xinit for display and it also defaults to using an OpenGL graphics driver (at least the last time I installed AGS this was the case).  As a result the resolution was incorrect and performance was poor, both to the point where it was unusable.

In order to rectify this I followed these steps:
### Install Pixel desktop environment
After opening the Retropie setup script (either from the command line or via ES): Configuration / Tools -> Raspbian tools -> Install pixel desktop environment
### Modify AGS emulators.cfg file
Edit the contents of /opt/retropie/configs/ags/emulators.cfg to contain:

`ags = "sudo xinit /opt/retropie/emulators/ags/bin/ags --fullscreen --gfxdriver software --gfxfilter hqx 1 %ROM%"`

`default = "ags"`

Note that the "--gfxfilter hqx 1" is not required and can be omitted if you prefer to have the non-filtered graphics.

I elected to change the driver AGS was using rather than enable the OpenGL driver in Retropie as it is still experimental and is known to still cause issues for other emulators.  I haven't actually tested AGS using the driver though so not sure if that works or not.

## Controls

AGS requires a mouse attached to the Raspberry Pi

## Useful Links
http://www.adventuregamestudio.co.uk/  
https://github.com/adventuregamestudio/ags/tree/master/debian  
https://en.wikipedia.org/wiki/Adventure_Game_Studio  
https://wiki.ubuntuusers.de/Adventure_Game_Studio/
