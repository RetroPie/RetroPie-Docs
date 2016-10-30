## Quick Reference

The following chart is a quick reference for all the arcade emulators in RetroPie:

| Emulator | Romset | # of ROMs | [.DAT Files](https://github.com/HerbFargus/retropie-dat/archive/master.zip) | Compatibility List |
| :---: | :---: | :---: | :---: | :---: |
| [mame4all](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | 0.37b5 | [2270](http://code.google.com/p/imame4all/wiki/GameList) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing) |
| [lr-imame4all](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | 0.37b5 | [2270](http://code.google.com/p/imame4all/wiki/GameList) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing) |
| [lr-mame2003](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | 0.78 | 4705 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing) |
| [lr-mame2010](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | 0.139 | 8782 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHUFdCc04zZ3o4dnM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1IRSmFrSDvIc6gAw0gn12TcQ3HDOwmrETTor8wvvb7VI/edit?usp=sharing) |
| [advmame-.94](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | 0.94 | 5563 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHa2E5Rzl4ZEdMdjQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1AEQ94buG0rvbW0xdnYKeuEhHeCbuZlRfRJQCb1Dt8fw/edit?usp=sharing) |
| [advmame-1.4](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | 0.106 | 6166 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHMEZnb1RxQWNmdHM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1RapyxChe2BMOfbX-FsCup9SXGxvS1WmXAofwaTJtmxc/edit?usp=sharing) |
| [pifba](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | 0.114 (fba 0.2.96.71) | 684 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHaHUta2dQYk1HTGM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing) |
| [lr-fba](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | 0.154 (fba 0.2.97.30) | [3369](https://raw.githubusercontent.com/libretro/fba-libretro/master/svn-current/trunk/gamelist.txt) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHcF96YmdjaWlEdXM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1rWO7Lm0bTGNpak6J-CPzde0GNIDP0NHDoQdJ6iWosfA/edit?usp=sharing) |
| [lr-fbalpha](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | 0.175 (fba 0.2.97.39) | [4150](https://raw.githubusercontent.com/libretro/fbalpha/b55216c1582313bb770a7d8d2032acd384537387/gamelist.txt) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHamozOVVZQkpUVHM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing) |
| [gngeopi](https://github.com/RetroPie/RetroPie-Setup/wiki/Neo-Geo) | 0.138 | 203 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHZVVCYmVtaUM1VlU/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1A_a_9t14uzDUMrrO0RgLDwiVUiycmclcPIs6cU6Iox8/edit?usp=sharing) |

For further details, see the system-specific wiki pages for [MAME](https://github.com/petrockblog/RetroPie-Setup/wiki/MAME) and [FBA](https://github.com/petrockblog/RetroPie-Setup/wiki/FinalBurn-Alpha).

## Crash Course in Arcade ROMs

Arcade ROMs are tied to the version of the arcade emulator, because the definition of what is the "correct" contents and usage of the ROM can change from version to version of the emulator.

For example, MAME2003 is based off the MAME 0.78 source code, so you must use the MAME 0.78 ROM set with MAME2003. If you use ROMs which are from an earlier or later MAME version, such as 0.50 or 0.100 or 0.173, then those ROMs probably will not work with MAME2003 because that other version's definition of the correct ROM is different from 0.78's definition of the correct ROM.

RetroPie includes forks of the [MAME](http://mamedev.org/) emulator that work well on the Raspberry Pi hardware, but are based on older versions of the emulator code. The [Final Burn Alpha](http://www.fbalpha.com/) emulator usually performs better than MAME but supports less games, a recent and earlier FBA are available in RetroPie.

The recommended emulators are:

* Pi 2 and Pi 3: `lr-mame2003` and `lr-fbalpha`
* Pi 1 and Pi Zero: `mame4all` (the native emulator, not the RetroArch core)

If the game you wish to play is supported by different emulator versions, try each version, as one may perform better than another. Earlier versions usually run faster than later versions (but not always). Earlier versions also support less games than later versions. Native emulators like mame4all and AdvMame may perform better than RetroArch cores but cannot take advantage of global RetroArch configurations so must be configured individually. Generally most 2D games work well on the Pi 3, but most 3D and vector games do not run at playable speed or at all.

Further good resources for understanding more about MAME/FBA arcade ROMs and their usage are:

* [RetroPie Forum: How to use MAME with RetroPie Help Guide](https://retropie.org.uk/forum/topic/2859/how-to-use-mame-with-retropie-help-guide)
* [Demystifying MAME ROMs Tutorial by ChoccyHobNob](http://choccyhobnob.com/tutorials/demystifying-mame-roms/).

So how do you tell you have the right ROM? The details of correct ROMs are stored in DAT files. A DAT file describes the correct ROM contents such filenames, file sizes, and checksums to verify contents are not wrong or corrupt. DAT files are just (extremely large) text files. You can open them in a text editor if you wish to see the contents.

You can use a ROM verification tool to check your ROMs against a given DAT file. Some popular ROM verification tools are:

* [clrmamepro](http://mamedev.emulab.it/clrmamepro/) (Windows)
* [clrmamepro](http://www.emulab.it) (OSX)
* [romcenter](http://romcenter.com/) (Windows)
* [Romulus](http://romulus.net63.net/) (Windows)
* [RomVault](http://www.romvault.com/) (Windows)

All of the Windows tools can be run on Linux (x86) using [Wine](https://www.winehq.org/).

# clrmamepro Tutorial

This section will focus on the clrmamepro Windows utility for verifying and converting romsets.

clrmamepro is very powerful, but also somewhat complex and not friendly to new users.

## Video Tutorial

* [Easy ClrMamePro Tutorial](https://www.youtube.com/watch?v=_lssz2pAba8)

## Requirements

* The current version of RetroPie. Romsets and packaged MAME/FBA emulators occasionally change.
* A Windows PC for setting up RetroPie and running clrmamepro. This tutorial assumes you are running a 64 bit version of Windows, but the steps for 32 bit Windows will be the same once you get past downloading the clrmamepro software.

**NOTE:** There are unsupported WINE versions available for OSX and Linux, if you Google.

## Step 1 - Back up your ROMs
It is possible with clrmamepro to change one or two options and when it runs it will delete all your existing ROMs. OK, not really - using the default options it will make backups of any files it removes, but I have seen a lot of people when getting started mess up their ROMs beyond repair.

##Step 2 - Download [clrmamepro](http://mamedev.emulab.it/clrmamepro/#downloads)
The version at the time of this article is 4.016.  I would recommend the 64 bit version if you are running a 64 bit OS, it will be significantly faster.  I would also recommend the zip version, just extract it to C:\clrmamepro.  There's no need to run the installer.

##Step 3 - Acquire DAT files
DAT files are the [XML-based](http://en.wikipedia.org/wiki/XML) database definitions of the exact ROMs an emulator uses. Using the DAT files and [CRC](http://en.wikipedia.org/wiki/Cyclic_redundancy_check) checks, clrmamepro is able to identify which of your ROMs are valid for a given emulator.

You can download all .DAT files for all arcade emulators [**HERE**](https://github.com/HerbFargus/retropie-dat/archive/master.zip)
* For this tutorial, extract the zip file into `C:\` (but you can really put it anywhere you want)
* Open retropie-dat-master and you should see a list of folders. Each folder contains the .DAT files for the respective emulator. We will only be using `C:\retropie-dat-master\mame4all\MAME 0.37b5.dat` in this tutorial.
* Create a subdirectory `C:\retropie-dat-master\mame4allroms` (this will be used in the next step)
* Create a subdirectory `C:\retropie-dat-master\pifbaroms`

**NOTE:** Use the appropriate .DAT from the zip file if you want to target a different MAME/FBA emulator. The table at the top of this page details the files needed.

##Step 4 - Run clrmamepro for the first time
* Run `C:\clrmamepro\cmpro64.exe`.  The welcome screen explains that common first steps are to 1) Create a Profile, 2) Set up your paths and 3) Scan your ROMs. We will be doing things slightly differently, in order to leave your source ROMs intact.  
* Click OK to the Welcome screen
* Click **"Add DatFile..."** and open the MAME4ALL DAT file at `C:\retropie-dat-master\mame4all\MAME 0.37b5.dat`
* Accept the default profile location of [PROFILES], click **"OK"**
* Select **"[NEW DATFILES]"** in the left-hand pane and select **"MAME 0.37b5"** in the right-hand pane
* Click **"Load / Update"**
* Clrmamepro will ask you how to generate the settings for this datfile, click **"Default"** (it is possible it will throw a warning but just select **"ok to all"** and continue on)
* You are now at the main window for clrmamepro.  We still need to set our paths, so click **"Settings"**
* Verify **"ROM-Paths"** is the selected option in the upper-left corner drop down menu
* Click the **"Add..."** button
* Select the folder you created in the last step called `C:\retropie-dat-master\mame4allroms` and click **"OK"**
* Close the settings window with the **"X"** button in the upper right

At this point, you could scan the ROMs folder you just selected, but we just created this folder and it is empty.  Instead, we will rebuild into this folder.  Clrmamepro can scan other locations for matching ROMs and build a new ROM set from them.

##Step 5- Rebuild a ROM set

* In the main clrmamepro window, select **"Rebuilder"**
* The destination should already be filled in for you - it is the same as the ROM path you defined above in the settings window: `C:\retropie-dat-master\mame4allroms`
* Use the browse button **"..."** to select your source path.  For example you might have a full set of MAME v0.156 ROMs - point clrmamepro to that directory as your source.
* When rebuilding there are three options: **Non-Merged, Merged, and Split**. (**NOTE**: This process requires a .dat file that contains merge data for the romset. Using Non-Merged ROMs is the most straightforward way to copy individual games to a RetroPie system rather than an entire MAME set.)

To understand what these options mean, we must first understand the MAME concept of **parents** and **clones**:

* **Parent:** The main version of the game. This is _normally_ the most common variant, in the English language. They have all the files needed to play them within the .zip file.
* **Clone:** A variant of the Parent. Typically different language, or other small changes. Their .zips only contain the files that have been changed from the parent, meaning that the parent .zip must be present in the ROM directory for the clone to be ran.
* **Non-Merged Set:** parents and clones in their own stand-alone .zip files. This removes clone's dependencies on parents, meaning you can take ANY of these .zip files (even the clones), put them in the appropriate ROM directory, and they should work! However, since every .zip has every required file, they will use higher total disk space. If you only want certain MAME ROMs on your system, use this method to ensure each .zip is usable stand-alone.
* **Merged Set:** puts _all_ files of the parents and clones of the game into a single .zip file. The version that will be launched will be the version that which is the .zip's name. To run a different version, rename the merged .zip to that of the version you want.
* **Split Set:** parents are complete .zip files with everything needed, and clones are .zip files with _only_ their unique files, saving disk space. This means that you will have to transfer the appropriate parent .zip to your ROM directory for every clone .zip you wish to use. For example, pacman.zip (a clone), will not work without puckman.zip (its parent). This quickly gets confusing, so it's recommended to simply transfer the whole set to your ROM directory, to avoid missing file errors. **NOTE:** split sets are how most downloaded complete MAME romsets are presented.

* Click **"Rebuild..."**.  Depending on the size of the directory you chose as a source, this could take some time
* When clrmamepro is finished rebuilding, you will see a window with statistics showing how many matching files were found, how many files were created and how many were skipped.  Click "OK" 
* Repeat for any other source paths you might have.  You can rebuild from multiple sources, but leave the Destination path the same
* When finished, close the Rebuilder with the **"X"** in the upper right corner of the window

Time to find out how well your source ROMs matched up...

##Step 6 - Scan a ROM set
* In the main clrmamepro window, select **"Scanner"**
* Leave all settings at default and click **"New Scan..."**
* When clrmamepro finishes scanning, you will see a "Statistics" window with high level information and a "Scan Results" window with detailed information about your missing ROMs

##Repeat Steps 4 through 6 for the FBA ROM set#
* From clrmamepro "Profiler" window load the DAT file for PiFBA `C:\retropie-dat-master\pifba\fba_029671_od_release_10_working_roms.dat`
* From clrmamepro "Settings" windows set the ROM path to `C:\retropie-dat-master\pifbaroms`
* Use clrmamepro's "Rebuilder" to rebuild your existing ROMs to a new ROM set
* Scan the rebuilt ROMs using the "Scanner"

##Notes

That's the basics of using clrmamepro.  Some additional notes:

* Be careful with the "Fix" settings in the Scanner window and the "Remove Matched Sourcefiles" setting in the Rebuilder window. These settings will remove and rename your ROMs.
* If clrmamepro does delete any ROMs (because you told it to), you should be able to find backups in C:\clrmamepro\backup as long as you didn't change the default settings.
* clrmamepro is very stable.  It has been around for a long time, it is regularly updated and it is widely used.  If it reports problems reading your ROMs, you most likely have corrupt ROM archives (zip files) or a failing hard drive.

* If you feel the need to reset clrmamepro's settings, just delete your existing profile(s) and reload your DAT file, selecting **"Default"** settings for the new profile.  Almost all of clrmamepro's settings are per-profile.

# List of Emulators and Their Respective Romsets:

RetroPie 3.0.0 MAME Versions

These details are as per the default installed binaries on the RetroPie 3.0.0 image.

**Important**

In 3.0.0 some emulators share directories, so you need to choose which FBA, NeoGeo and mame4all version you want.
So you can have 1 romset for each of these (mame4all, FBA, NeoGeo, advmame)

See [here](http://smartretro.co.uk/forums/viewtopic.php?f=3&t=68) for RetroPie 2.6

### [mame4all-pi](http://sourceforge.net/projects/mame4allpi/)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-mame4all
Binary Dir: /opt/retropie/emulators/mame4all
Config Dir: /opt/retropie/configs/mame-mame4all
```
MAME Version: Based on **0.37b5** (July 2000)

Size: 1.86 GB

Romsets emulated: 2270 (includes clones etc..)

Active Sets 2241/2241
* Parents 560/560
* Clones 990/990
* Others 690/690
* BIOS 1/1

Dat File: [mame4all-037b5-RetroPie-260.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHVUNfWHpUZk82bkk/view?usp=sharing)

Dat File (with merge data): [MAME 0.37b5.dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)

Dat File (no clones, no neogeo): [mame4all-no-clones-no-neogeo](https://drive.google.com/file/d/0B2TMeZ6iEFvHNm5OYndFUHM3djg/view?usp=sharing)

[**MAME4ALL-PI COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing)  feel free to contribute to the list.

### [lr-imame4all](https://github.com/libretro/imame4all-libretro)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-mame4all
Binary Dir: /opt/retropie/libretrocores/lr-imame4all
Config Dir: /opt/retropie/configs/mame-mame4all/retroarch.cfg
```
MAME Version: Based on **0.37b5** (July 2000)

Size: 1.86 GB

Romsets emulated: 2270 (includes clones etc..)

Active Sets 2241/2241
* Parents 560/560
* Clones 990/990
* Others 690/690
* BIOS 1/1

Dat File: [mame4all-037b5-RetroPie-260.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHVUNfWHpUZk82bkk/view?usp=sharing)

Dat File (with merge data): [MAME 0.37b5.dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)

Dat File (no clones, no neogeo): [mame4all-no-clones-no-neogeo](https://drive.google.com/file/d/0B2TMeZ6iEFvHNm5OYndFUHM3djg/view?usp=sharing)

[**lr-IMAME4ALL COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing)  feel free to contribute to the list.

### [lr-mame2003](https://github.com/libretro/mame2003-libretro)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-libretro
Binary Dir: /opt/retropie/libretrocores/lr-mame2003
Config Dir: /opt/retropie/configs/mame-libretro/retroarch.cfg
```
MAME Version: Based on **0.78** (December 2003)

Romsets emulated: 4705 (includes clones etc..)

Active Sets 4705/4705
* Parents 1042/1042
* Clones 2039/2039
* Others 1624/1624
* BIOS 1/1

Dat File (with merge data): [MAME 0.78.dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing) 

Dat File (working only, no clones): [mame2003-lr-working-no-clones](https://drive.google.com/file/d/0B2TMeZ6iEFvHV21wRVh6TF9uQ1U/view?usp=sharing) **Please note that this DAT file is intended for an 0.78u5 ROM set and may not be an exact match for a 0.78 set or the MAME 2003 core.**

Dat File ('lite' set: working, no clones, neogeo, PlayChoice (NES multiplay), no rotary/dial/trackball/lightgun controls, no casino/multiplay/quiz/mahjong/fruit_machines/rhythm/mature): [mame2003-lr-lite](https://drive.google.com/file/d/0B2TMeZ6iEFvHY1VzcXYyT09iRGs/view?usp=sharing) (No. roms: 1615) **Please note that this DAT file is intended for an 0.78u5 ROM set and may not be an exact match for a 0.78 set or the MAME 2003 core.**

Dat File: [MAME 078u5.dat](https://dl.dropboxusercontent.com/u/51705339/MAME%200.78u5%20Dats/MAME%20078u5.dat)

[**lr-mame2003 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing)  feel free to contribute to the list.

### [lr-mame2010](https://github.com/libretro/mame2010-libretro)

```shell
Roms Dir: /home/pi/RetroPie/roms/mame-libretro
Binary Dir: /opt/retropie/libretrocores/lr-mame2010
Config Dir: /opt/retropie/configs/mame-libretro/retroarch.cfg
```
MAME Version: Based on **0.139** (August 2010)

Romsets emulated: 8782 (includes clones etc..)

Active Sets 8782/8782
* Parents 1835/1835
* Clones 4265/4265
* Others 2683/2683
* BIOS 1/1

Dat File (with merge data): [MAME 0.139.dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHUFdCc04zZ3o4dnM/view?usp=sharing) 

[**lr-mame2010 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1IRSmFrSDvIc6gAw0gn12TcQ3HDOwmrETTor8wvvb7VI/edit?usp=sharing) feel free to contribute to the list.

### [AdvanceMAME 0.94.0 and 1.4](http://sourceforge.net/projects/advancemame/files/advancemame/0.94.0/)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-advmame
Binary Dir: /opt/retropie/emulators/advmame/bin
Config Dir: /opt/retropie/configs/mame-advmame
```
MAME Version: Based on **MAME 0.94** (March 2005) or (for 1.4) Based on **MAME 0.106** (May 2006)

Size: 11.6GB (0.94.0) Size: 14.8GB (1.4)

Romsets Emulated: 5563 (0.94.0) 6166 (1.4) (includes clones etc..)

Active Sets (For 0.94.0) 5563/5563
* Parents 1236/1236
* Clones 2473/2473
* Others 1829/1829
* BIOS 25/25

Active Sets (For 1.4) 6166/6166
* Parents 1388/1388
* Clones 2824/2824
* Others 1928/1928
* BIOS 26/26

Dat File: [advmame-0.94-RetroPie-260.7z](https://drive.google.com/file/d/0B2TMeZ6iEFvHa2E5Rzl4ZEdMdjQ/view?usp=sharing)

[**AdvMame .94 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1AEQ94buG0rvbW0xdnYKeuEhHeCbuZlRfRJQCb1Dt8fw/edit?usp=sharing)  feel free to contribute to the list.

Dat File: [advmame12-106.7z](https://drive.google.com/file/d/0B2TMeZ6iEFvHMEZnb1RxQWNmdHM/view?usp=sharing)

[**AdvMame 1.4 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1RapyxChe2BMOfbX-FsCup9SXGxvS1WmXAofwaTJtmxc/edit?usp=sharing)  feel free to contribute to the list.

### [PiFBA](http://sourceforge.net/projects/pifba/)
```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/emulators/pifba
Config Dir: /opt/retropie/configs/fba/fba2x.cfg
```
MAME Version: **FBA 0.2.96.71** which is based on MAME 0.114 (April 2007)

Size: 3.62 GB

Romsets emulated: 684 (no clones)

Dat File: [fba_0.2.96.71_clrmame_dat.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHaHUta2dQYk1HTGM/view?usp=sharing)

Dat File (With merge data): [FB Alpha v0.2.96.71 (ClrMame Pro).dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHZFJOckQyRVZ5OG8/view?usp=sharing)

All clones (current tested) non-working\mahjong\quiz\adult\casino\rythm removed

Romsets emulated: 291

Dat File: [fba_029671_od_release_10_working_roms_filtered.zip] (https://drive.google.com/file/d/0B2TMeZ6iEFvHMTV2TnlrZWwxRXc/view?usp=sharing)

[**PiFBA COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing)  feel free to contribute to the list.

### [lr-fba](https://github.com/libretro/fba-libretro) 
```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/libretrocores/lr-fba
Config Dir: /opt/retropie/configs/fba/retroarch.cfg
```
MAME Version: **FBA 0.2.97.30** which is based on MAME 0.154 (Jul 2014)

Size: 9.15 GB

Romsets emulated: 3369 (includes clones etc..)

Active Sets 3369/3369
* Parents 710/710
* Clones 2146/2146
* Others 508/508
* BIOS 5/5

Dat File: [FB Alpha v0.2.97.30.dat.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHcF96YmdjaWlEdXM/view?usp=sharing)

Neo Geo Only .Dat File: [fba-lr-neogeo](https://drive.google.com/file/d/0B2TMeZ6iEFvHVk1Ud1RoSHpfcFU/view?usp=sharing)

[**lr-fba COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1rWO7Lm0bTGNpak6J-CPzde0GNIDP0NHDoQdJ6iWosfA/edit?usp=sharing)  feel free to contribute to the list.

### [lr-fbalpha](https://github.com/libretro/fbalpha) 
```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/libretrocores/lr-fbalpha
Config Dir: /opt/retropie/configs/fba/retroarch.cfg
```
MAME Version: **FBA 0.2.97.39** which is based on MAME 0.175

Romsets emulated: 4150 (includes clones etc..)

Active Sets 4150/4150
* Parents 877/877
* Clones 2698/2698
* Others 569/569
* BIOS 6/6

Dat File: [FB Alpha v0.2.97.38.dat](https://drive.google.com/file/d/0B_51EcTfJiTqWHdtUmtBZ01JSTg/view)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, Arcade Only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20Arcade%20Only).dat)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, ColecoVision only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20ColecoVision%20only).dat)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, Game Gear only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20Game%20Gear%20only).dat)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, Master System only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20Master%20System%20only).dat)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, Megadrive only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20Megadrive%20only).dat)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, PC-Engine only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20PC-Engine%20only).dat)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, Sega SG-1000 only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20Sega%20SG-1000%20only).dat)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, SuprGrafx only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20SuprGrafx%20only).dat)

Dat File: [FB Alpha v0.2.97.38 (ClrMame Pro XML, TurboGrafx16 only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029738%20dats/FB%20Alpha%20v0.2.97.38%20(ClrMame%20Pro%20XML%2C%20TurboGrafx16%20only).dat)

[**lr-fbalpha COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing)  feel free to contribute to the list.

### [GnGeo 0.8](https://github.com/ymartel06/GnGeo-Pi)
```shell
Roms Dir: /home/pi/RetroPie/roms/neogeo
Binary Dir: /opt/retropie/emulators/gngeopi/bin
Config Dir: /opt/retropie/configs/neogeo
```
MAME Version: Based on **0.138** romsets (May 2010)

Romsets emulated: 203

Dat File: [pandora_gngeo_084_dat.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHZVVCYmVtaUM1VlU/view?usp=sharing)

All clones non-working\mahjong\quiz removed

Romsets emulated: 128

Dat File: [pandora_gngeo_084_filtered.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHb1RhaTF0NzJaRlU/view?usp=sharing)

[**GnGeo-Pi COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1A_a_9t14uzDUMrrO0RgLDwiVUiycmclcPIs6cU6Iox8/edit?usp=sharing)  feel free to contribute to the list.

**List courtesy of Floob** 