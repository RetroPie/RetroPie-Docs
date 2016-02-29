***
![scummvm](https://cloud.githubusercontent.com/assets/10035308/12214107/156e1d4a-b645-11e5-886c-a49712b1a312.png)
***
_ScummVM stands for Script Creation Utility for Maniac Mansion (VM stands for virtual machine). ScummVM is a program which allows you to run certain classic graphical point-and-click adventure games, provided you already have their data files_
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [ScummVM](http://scummvm.org/) | scummvm  | see below | none | hardcoded |

## Emulator: [ScummVM](http://scummvm.org/)

## ROMS
Accepted File Extensions: This is a tricky question as ScummVM has it's own particular filesets and method of loading- but when all is said and done **.sh .svm** are the filetypes EmulationStation will read.

ScummVM is much different than most romsets in that there are a set of files for each game. 

See the list here: http://wiki.scummvm.org/index.php/Datafiles

Place Your folders of game files in
```
/home/pi/RetroPie/roms/scummvm
```

**Quick Start**

-After you've added you files into the scummvm rom folder, open up the +LAUNCH GUI

-then hold down shift and click mass add

-Navigate to the scummvm folder and select it to add all of your files

-quit out of the GUI

-Press F4 to get out of emulationstation

-Type in emulationstation to open up emulationstation

-navigate to scummvm and your games will all be there on the list and you'll have no need of a GUI

## Video Tutorial:

<a href="https://www.youtube.com/watch?v=txdiaZlDUEs" target="_blank"><img src="https://i.ytimg.com/vi_webp/txdiaZlDUEs/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a>

```shell

**OUTDATED CONFIGURATIONS (these settings were integrated by default starting with image 2.5)**

The following guide is taken from [here](http://blog.petrockblock.com/forums/topic/guidescript-add-all-your-scummvm-games-to-emulationstation/#post-4814):

Here is a guide plus a script i made to get all your scummvm games to show in emulationstation (which is usually a pain).

Ok first unpack all you games to a location (lets say ```/home/pi/RetroPie/roms/scummvm```).
Now, go to the console and start scummvm (type ```scummvm``` ENTER).
OK, now browse to your game directory, probably ```/home/pi/RetroPie/roms/scummvm```.
You will see a bunch of directories with your games. Put the mouse over the “Add game” button and presh shift (keyboard). The button will change to “Mass Add”, just click it.
Your games are in ScummVM now, press "Quit".

Download [this script](http://blog.petrockblock.com/wp-content/uploads/2014/02/ES-scummvm11.rar) to your ```/home/pi```. Alternatively, you can create the script file on your own. This is the script content:
```python
#!/usr/bin/env python
import os
import sys
try:
    d = sys.argv[1]
except:
    sys.exit("Input scummvm game directory e.g.:python ES-scummvm.py /home/pi/RetroPie/roms/scummvm")
		
d = sys.argv[1]
f = open( "/home/pi/.scummvmrc", "r" )
array = []
for line in f:
    if line.startswith("["):
        x = line.replace("[","").split("]")[0]
        print "Adding " + x
        open(d +"/" + x + ".svm", 'w+').close()
f.close()

#Hint: If you want to add multiple games in one go, try pressing and
#holding the shift key before clicking 'Add game' -- its label will
#change to 'Mass Add' and if you press it, you are again asked to select
#a directory, only this time ScummVM will search through all
#subdirectories for supported games.
```
```
Run it with : ```python ES-scummvm.py /home/pi/RetroPie/roms/scummvm```.
The script will generate dummy .svm files so they can be read by EmulationStation.
Now, in ```/home/pi/.emulationstation/es_system.cfg``` make sure your scummvm section looks like this (notice the ```%BASENAME%``` instead of ```%ROM%``` and the .svm for the dummy files):

bash
DESCNAME=ScummVM
NAME=scummvm
PATH=/media/usb0/scummvm
EXTENSION=.svm
COMMAND=scummvm -f –joystick=0 %BASENAME%
PLATFORMID=99


Thats all
```


#### Compiling Tips

If you want to enable support for myst and other experimental games you have to compile those engines in manually with the `--enable-all-engines` flag when configuring.