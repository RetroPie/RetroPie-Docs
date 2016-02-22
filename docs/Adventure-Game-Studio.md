***

![Adventure Game Studio](http://i.imgur.com/eBMyMvj.png)

***
_Adventure Game Studio is an open source development tool that is primarily used to create graphic adventure games._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [AGS](https://github.com/adventuregamestudio/ags/tree/master/debian) | ags | .exe | none | mouse |
## Emulator: [AGS](https://github.com/adventuregamestudio/ags/tree/master/debian) (EXPERIMENTAL)

Note that this is experimental. It can be installed from the experimental menu of the [RetroPie Setup Script](Updating RetroPie).

## ROMS
Accepted File Extensions: **.exe**

Place your AGS files in
```
/home/pi/RetroPie/roms/ags
```

## Config changes
In RetroPie 3.5, you need to install xinit
```
sudo apt-get install xinit
```

Also edit the following file
```
/opt/retropie/configs/ags/emulators.cfg
```
so that it reads
```
ags="sudo xinit /opt/retropie/emulators/ags/bin/ags --fullscreen %ROM%"
```

### Video Guide  

<a href="https://www.youtube.com/watch?v=cH_784XOsiM" target="_blank"><img src="https://i.ytimg.com/vi_webp/cH_784XOsiM/mqdefault.webp" 
alt="RetroPie Adventure Game Studio" width="300" height="190" border="10" /></a>  

## Controls

AGS requires a mouse attached to the Raspberry Pi

## Useful Links
http://www.adventuregamestudio.co.uk/  
https://github.com/adventuregamestudio/ags/tree/master/debian  
https://en.wikipedia.org/wiki/Adventure_Game_Studio  
https://wiki.ubuntuusers.de/Adventure_Game_Studio/
