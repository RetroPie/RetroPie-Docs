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
Stratagus runs games from properly configured game directories. For the Warcraft and Starcraft titles, extraction tools are required to extract the original game assets into a Stratagus-compatible game folder. You can get the extraction tools for linux here:
```
https://github.com/Wargus/war1gus
(Warcraft 1)
https://github.com/Wargus/wargus
(Warcraft 2)
https://github.com/Wargus/stargus
(Starcraft)
```

Or windows versions of the tools may be downloaded from here:
```
https://wargus.github.io/war1gus.html  
(Warcraft 1)
https://wargus.github.io/
(Warcraft 2)
https://wargus.github.io/stargus.html
(Starcraft)
```

The tools are designed to be used in conjunction with an official installation CD or installation directory. Run the extraction tools as shown in the detailed installation instructions section and once finished, copy the relevant folder(s) into the retropie roms directory, adding a ".data" to the folder name.

For example -
```
/home/pi/RetroPie/roms/stratagus/<GAME>.data
```

After you've added your files into the stratagus rom folder with the correct names and restarted emulationstation, the names should appear in the Emulationstation UI and you can start them directly from there. All graphics settings are configured in-game.

### Detailed instructions - Installing Warcraft / Warcraft II

**Note 1: this will not work with the Battle.net Edition of Warcraft II**

**Note 2: Windows XP users might have trouble extracting the data needed from the Warcraft II installation location** Please see http://wargus.github.io/faq.html#winxp for further details

Firstly, the installation will not work just by copying the contents of the Warcraft or Warcraft 2 CD over to the roms folder of the Raspberry Pi. You must run the Wargus and/or War1gus installer from either Windows, Mac OS X or Linux to correctly extract the game assets. Running the tools from windows is arguably the most straightforward option and can be carried out as follows: 

* Go to the official Wargus website (http://wargus.github.io/) and download the latest stable Windows version of Wargus and/or War1gus
* Install Wargus and/or War1gus. During installation, the installer will ask for the location of your Warcraft / Warcraft II data. You can point the installer to the official installation CD (or if you have the game already installed, the game installation directory should also work)
* (Optional) if you have the Expansion Pack "Beyond the Dark Portal" for Warcraft II, then point the installer to that data as well (this can be skipped if you don't have the Expansion Pack)
* At the end of the install you can go ahead and launch the game from Windows to make sure it works. If it does then we're ready to start copying data over to the Raspberry Pi
* In Windows navigate to "C:\Program Files (x86)\Wargus" or "C:\Program Files\Wargus" and copy only the sub-directories to 
```
/home/pi/RetroPie/roms/stratagus/<GAME>.data`
(e.g. /home/pi/RetroPie/roms/stratagus/warcraft2.data)
```
On your Raspberry Pi

The sub-directories that need to be copied are as followed:

* campaigns
* graphics
* maps
* music
* scripts
* sounds
* videos

#### Wargus/War1gus settings file Location for Stratagus

The settings files for stratagus are located here:
```
`/home/pi/.stratagus/
```
For example the warcraft II settings are located here:
```
`/home/pi/.stratagus/wc2/preferences.lua`
```

### Detailed Instructions - Installing Starcraft 

Stargus is a Starcraft Mod that allows you to play Starcraft with the Stratagus engine. It should be noted that this emulator is still in pre-alpha stage & development is far from complete. From the developer website "Terran and most Zerg units work, with Protoss being less complete. Many of the special features are not implemented, such as flying Terran buildings, Zerg creep, or Protoss shields. Many animations are also missing. The campaign is not being worked on at all."

#### Install Stargus

Install details for all platforms can be found here: https://github.com/Wargus/stargus

This guide shows the method for installing on windows:

Download and install the executable found [HERE](https://github.com/Wargus/stargus/releases/tag/master-builds) or download the extraction tool for Windows from https://wargus.github.io/stargus.html 

#### Extract Starcraft Assets

Make sure you have the original CD install files. Install StarCraft and take note of the path where it is installed. Copy the `INSTALL.EXE` from the CD to where the game was installed and rename it to `starcraft.mpq`.

Alternatively, you could download the StarCraft: Remastered installer from Blizzard and install the game from it, as it will provide the files you need, usually to "C:\Program Files (x86)\StarCraft". 

Start up Stargus and select `starcraft.mpq` and it will begin extracting the assets needed to run on Stratagus. They will be extracted to:

```
C:\Users\<USERNAME>\AppData\Roaming\Stratagus\data.Stargus
```

It should be ~500MB

There are also some assets in the the following folder - these should also be copied over.

```
C:\Program Files (x86)\Stargus
```

Copy the contents of both paths to

```
/home/pi/RetroPie/roms/stratagus/starcraft.data
```

Restart emulationstation and it should show up as an option in stratagus

### Stratagus Hotkeys

Hotkeys | Action
| :---: | :---: |
F1 | Help Menu
Ctrl + H | Help Menu
Alt + H | Help Menu
Shift + F2 | Save Map Location 1
Shift + F3 | Save Map Location 2
Shift + F4 | Save Map Location 3
F2 | Recall Map Location 1
F3 | Recall Map Location 2
F4 | Recall Map Location 3
F5 | Game Options Menu
F6 | Speed Options
F7 | Sound Options
F8 | Preferences
F9 | Diplomacy
F10 | Game Menu
F11 | Save
F12 | Load
Ctrl + X | Exit Stratagus
Alt + X | Exit Stratagus
Ctrl + Q | Quit to Menu
Alt + Q | Quit to Menu
Ctrl + R | Restart Scenario
Ctrl + M | Toggle Music
Ctrl + S | Toggle Sound
Alt + C | Center Map on Currently Selected Unit(s)
Tab | Toggle Terrain
+ | Increase Game speed
- | Decrease Game speed
