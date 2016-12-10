***
![stratagus](https://wargus.github.io/img/stratagus.svg)
***
_Stratagus is a free cross-platform real-time strategy gaming engine. Besides many open source strategy games, it supports extracted datafiles from Warcraft 1, Warcraft 2, and Starcraft 1._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Stratagus](https://wargus.github.io/) | stratagus  | .data | none | mouse+keyboard only |

## Emulator: [Stratagus](https://wargus.github.io/)

## ROMS
Stratagus runs games from properly configured game directories. For the Warcraft and Starcraft titles, run the appropriate extraction tools to extract the original data into a Stratagus game folder. You can get the extraction tools from https://github.com/Wargus/wargus for Warcraft 2, https://github.com/Wargus/war1gus for Warcraft 1, https://github.com/Wargus/stargus for Starcraft. Copy the extracted folder to the roms directory, adding a ".data" to the folder name.

Place your folders of game files in
```
/home/pi/RetroPie/roms/stratagus
```

After you've added you files into the stratagus rom folder, the folder names appear in the selection UI and you can start them from there directly. All graphics settings are done in-game.

### How to install Warcraft II using Wargus for Stratagus

Wargus is a Warcraft II Mod that allows you to play Warcraft II with the Stratagus engine. The game looks and sounds exactly like Warcraft II.

**Note: this will not work with the Battle.net Edition of Warcraft II**

Windows XP users might have trouble extracting the data needed from the Warcraft II installation location.
http://wargus.github.io/faq.html#winxp

First, you don't get it to work just by copying your Warcraft II CD over to your Raspberry Pi. You actually run the Wargus installer from either Windows, Mac OS X or Linux (not sure if it works on an ARM Linux). I did the Windows route and this is how I did it:

* Go to the [official Wargus website](http://wargus.github.io/) and download the Windows version of Wargus v2.4.1 or newer (there is also a [YouTube video](https://www.youtube.com/watch?v=fnY13i105LE) showing you how to install this)
* Now install Wargus and the installation will ask for your Warcraft II data so point it to your CD (or if you have your data copied to your hard drive then point to that directory)
* (Optional) if you have the Expansion Pack "Beyond the Dark Portal" then point the installer to that data (this can be skipped if you don't have the Expansion Pack)
* At the end of the install you can go ahead and launch Warcraft II to make sure it works and if it does then we're ready to start copying data over to your Raspberry Pi
* In Windows navigate to "C:\Program Files (x86)\Wargus" or "C:\Program Files\Wargus" and only copy the sub-directories to `/home/pi/RetroPie/roms/stratagus/warcraft2.data` on your Raspberry Pi

The sub-directories that need to be copied are as followed:

* campaigns
* graphics
* maps
* music
* scripts
* sounds
* videos

#### Wargus/Warcraft II settings file Location for Stratagus

`/home/pi/.stratagus/wc2/preferences.lua`

#### Stratagus Hotkeys

F1 = Help Menu
Ctrl + H = Help Menu
Alt + H = Help Menu
Shift + F2 = save map location 1
Shift + F3 = save map location 2
Shift + F4 = save map location 3
F2 = Recall map location 1
F3 = Recall map location 2
F4 = Recall map location 3
F5 = Game Options Menu
F6 = Speed Options
F7 = Sound Options
F8 = Preferences
F9 = Diplomacy
F10 = Game Menu
F11 = Save
F12 = Load
Ctrl + X = Exit Stratagus
Alt + X = Exit Stratagus
Ctrl + Q = Quit to Menu
Alt + Q = Quit to Menu
Ctrl + R = Restart Scenario
Ctrl + M = Toggle Music
Ctrl + S = Toggle Sound
Alt + C = Center map on currently selected unit(s)
Tab = Toggle Terrain
+ = Increase game speed
- = Decrease Game speed
