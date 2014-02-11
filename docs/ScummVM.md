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

Run it with : ```python ES-scummvm.py /home/pi/RetroPie/roms/scummvm```.
The script will generate dummy .svm files so they can be read by EmulationStation.
Now, in ```/home/pi/.emulationstation/es_system.cfg``` make sure your scummvm section looks like this (notice the ```%BASENAME%``` instead of ```%ROM%``` and the .svm for the dummy files):

```bash
DESCNAME=ScummVM
NAME=scummvm
PATH=/media/usb0/scummvm
EXTENSION=.svm
COMMAND=scummvm -f –joystick=0 %BASENAME%
PLATFORMID=20
```

Thats all