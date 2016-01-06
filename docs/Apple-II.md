![Apple II](http://www.jeuxvideovintage.com/ressources/img/Apple_II_logo.jpg)
***
_The Apple II was a series of personal computers starting from 1977 to 1993._
***


## Emulator: [Linapple](http://sourceforge.net/projects/linapple/)

## ROMS
Accepted File Extensions: **.dsk**

Place your Apple II disk image files in
```shell
/home/pi/RetroPie/roms/apple2/
```
## Controls
Upon boot, press F1 to get an overview of the controls- they will vary by game. As the Apple II was a personal computer it would only make sense that you would be using a keyboard and mouse.

```shell
  F1 - Show help screen
     F2 - Cold reset
     Shift+F2 - Reload conf file and restart
     F3, F4 - Choose an image file name for floppy disk in Slot 6 drive 1 or 2 respectively
     Shift+F3, Shift+F4 - The same thing for Apple hard disks (in Slot 7)
	Alt+F3,Alt+F4 - same as F3,F4 using FTP (see linapple.conf about configuring FTP accounts)
	Alt+Shift+F3, Alt+Shift+F4 - same as Shift+F3, Shift+F4 but using FTP account (see above)

     F5 - Swap drives for Slot 6
     F6 - Toggle fullscreen mode
     F7 - Reserved for Debugger!
     F8 - Save current screen as a .bmp file
     Shift+F8 - Save settings changable in runtime in conf file
     
     F9 - Cycle through various video modes
     F10 - Quit emulator

     F11 - Save current state to file, Alt+F11 - quick save
     F12 - Reload it from file, Alt+F12 - quick load

     Ctrl+0..9	- fast load state snapshot with corresponding number, saved previously by
     Ctrl+Shift+0..9 - fast save snapshot to current snapshot directory with corresponding number 0..9

     Ctrl+F12 - Hot reset

      Pause - Pause emulator
      Scroll Lock - Toggle full speed
    Num pad keys:
     Grey + - Speed up emulator
     Grey - - Speed it down
     Grey * - Normal speed
```

**Getting Started**

* Press F3 to choose your disk drive- and navigate to where you placed your disk images in the apple2 roms folder

* Select your game by pressing Enter and then press F2 to reboot into the game you just selected- now you should be inside your game. Most games will have a splash screen with controls specific to that game. 

* To exit back to Emulationstation press F10 

## Running Disks From EmulationStation

http://blog.petrockblock.com/forums/topic/how-to-get-linapple-disk-images-running-from-emulation-station-in-retropie/