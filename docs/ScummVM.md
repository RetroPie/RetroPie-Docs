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
Accepted File Extensions: This is a tricky question as ScummVM has its own particular filesets and method of loading- but when all is said and done **.sh .svm** are the filetypes EmulationStation will read.

ScummVM is very different to most romsets in that there are a set of files for each game. 

See the list here: http://wiki.scummvm.org/index.php/Datafiles

Place your folders of game files in
```
/home/pi/RetroPie/roms/scummvm
```

**List ScummVM games in EmulationStation**

Place an empty .svm file in scummvm's rom folder for each game which you want to appear in EmulationStation. This can be used to directly launch that game without starting the GUI first. Recalbox uses .scummvm files instead of .svm files.

**Quick Start**

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

<a href="https://www.youtube.com/watch?v=txdiaZlDUEs" target="_blank"><img src="https://i.ytimg.com/vi_webp/txdiaZlDUEs/mqdefault.webp" 
alt="ScummVM Configuration" width="300" height="180" border="10" /></a>

