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

First, you don't get it to work just by copying your Warcraft 2 CD over to your Raspberry Pi. You actually run the Wargus installer from either Windows, Mac OS X or Linux (not sure if it works on an ARM Linux). I did the Windows route and this is how I did it:

* Go to the [official Wargus website](http://wargus.github.io/) and download the Windows version of Wargus v2.4.1 or newer (there is also a YouTube video on that site showing you how to install this)
* Now install Wargus and the installation will ask for your Warcraft II data so point it to your CD (or if you have your data copied to your hard drive then point to there)
* (optional) next if you have the Expansion Pack "Beyond the Dark Portal" then point the installer to that data (I don't have this so I skipped this)
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

#### Warcraft II settings file Location for Wargus

`/home/pi/.stratagus/wc2/preferences.lua`
