***
![scummvm](https://cloud.githubusercontent.com/assets/10035308/12214107/156e1d4a-b645-11e5-886c-a49712b1a312.png)
***
_ScummVM stands for Script Creation Utility for Maniac Mansion (VM stands for virtual machine). ScummVM is a program which allows you to run certain classic graphical point-and-click adventure games, provided you already have their data files_
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [ScummVM](http://scummvm.org/) | scummvm  | see below | none | hardcoded |

## Emulator: [ScummVM](http://scummvm.org/)

### ROMs

Accepted File Extensions: This is a tricky question as ScummVM has its own particular filesets and method of loading- but when all is said and done **.sh .svm** are the filetypes EmulationStation will read.

ScummVM is very different to most romsets in that there are a set of files for each game.

See the list here: http://wiki.scummvm.org/index.php/Datafiles

Place your folders of game files in:

```
/home/pi/RetroPie/roms/scummvm
```

### List ScummVM games in EmulationStation

Place an `.svm` file in the ROM folder for each game which you want to appear in EmulationStation.

The `.svm` file contains the short name of the game. This can be used to directly launch that game without starting the ScummVM GUI first.

The list of short names is at: https://www.scummvm.org/compatibility

The [Recalbox documentation](https://www.lakka.tv/doc/ScummVM/) uses `.scummvm` files instead of `.svm` files.

### Example

The game **Day of the Tentacle** has the shortname `tentacle` and requires files:

* `MONSTER.SOU`
* `TENTACLE.000`
* `TENTACLE.001`

Create a directory `/home/pi/RetroPie/roms/scummvm/Day of the Tentacle` and place the game files in it.

Create a launcher file with the same name as the directory: `/home/pi/RetroPie/roms/scummvm/Day of the Tentacle/Day of the Tentacle.svm`

This launcher file `Day of the Tentacle.svm` contains the shortname `tentacle`

You can create the launcher file like:

```
echo "tentacle" > "/home/pi/RetroPie/roms/scummvm/Day of the Tentacle/Day of the Tentacle.svm"
```

The final file layout is:

```
/home/pi/RetroPie/roms/scummvm/Day of the Tentacle/Day of the Tentacle.svm
/home/pi/RetroPie/roms/scummvm/Day of the Tentacle/MONSTER.SOU
/home/pi/RetroPie/roms/scummvm/Day of the Tentacle/TENTACLE.000
/home/pi/RetroPie/roms/scummvm/Day of the Tentacle/TENTACLE.001
```

Restarting EmulationStation will show the name **Day of the Tentacle** which is used to launch the game.

### Quick Start

- Quit running rom without saving : Alt + X or Alt + Q

- After you've added files to the scummvm rom folder, open up the +LAUNCH GUI

- then hold down _shift_ and click "Mass Add..."

- Navigate to the scummvm folder and select it to add all of your files

- quit out of the GUI

- Press F4 to get out of emulationstation

- Type `emulationstation` to re-launch emulationstation

- navigate to scummvm and your games will be there on the list and you'll have no need for a GUI


## Troubleshooting

#### FUZZY MENU?

You can open the **options** in the scummvm launcher and change the graphics mode to **opengl** and it will make the menu and your games clear and crisp! There are also other rendering modes as well that can be changed.


## Video Tutorial:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/txdiaZlDUEs" title="Setting Up RetroPie 2.6: Configuring Scummvm" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; allowfullscreen"></iframe>
