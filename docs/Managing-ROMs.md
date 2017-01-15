# Getting Started

Working with arcade ROMs requires a different approach than ROMs for console systems. The overall process for using an arcade emulator in RetroPie:

1. Choose an arcade emulator listed in the table below that your system is powerful enough to run
2. **Either download or 'rebuild' a set of arcade ROMs with a version number that exactly matches the emulator you selected**

The recommended emulators are:

* Pi 2 and Pi 3: `lr-mame2003` and `lr-fbalpha`
* Pi 1 and Pi Zero: `mame4all`  (the native emulator, not the RetroArch core) and `pi-fba`

If the ROM you wish to play is only supported by other emulator versions in the table below, please be aware that earlier arcade emulator versions usually run faster than later versions but also that earlier versions support fewer games than later versions. Native emulators like mame4all and AdvMame may perform better than RetroArch cores but cannot take advantage of global RetroArch configurations so they must be configured individually. Generally most 2D games work well on the Pi 3, but most 3D and vector games do not run at playable speed or at all.

| Emulator | Required ROM Version | # of ROMs | [.DAT Files](https://github.com/HerbFargus/retropie-dat/archive/master.zip) | Compatibility List |
| :---: | :---: | :---: | :---: | :---: |
| [mame4all](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.37b5 | [2270](http://code.google.com/p/imame4all/wiki/GameList) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing) |
| [lr-imame4all](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.37b5 | [2270](http://code.google.com/p/imame4all/wiki/GameList) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing) |
| [lr-mame2003](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.78 | 4705 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing) |
| [lr-mame2010](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.139 | 8782 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHUFdCc04zZ3o4dnM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1IRSmFrSDvIc6gAw0gn12TcQ3HDOwmrETTor8wvvb7VI/edit?usp=sharing) |
| [advmame-.94](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.94 | 5563 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHa2E5Rzl4ZEdMdjQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1AEQ94buG0rvbW0xdnYKeuEhHeCbuZlRfRJQCb1Dt8fw/edit?usp=sharing) |
| [advmame-1.4](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.106 | 6166 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHMEZnb1RxQWNmdHM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1RapyxChe2BMOfbX-FsCup9SXGxvS1WmXAofwaTJtmxc/edit?usp=sharing) |
| [pifba](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | FB Alpha v0.2.96.71 | 684 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHaHUta2dQYk1HTGM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing) |
| [lr-fbalpha2012](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | FB Alpha v0.2.97.30 | [3369](https://raw.githubusercontent.com/libretro/fbalpha2012/master/svn-current/trunk/gamelist.txt) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHcF96YmdjaWlEdXM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1rWO7Lm0bTGNpak6J-CPzde0GNIDP0NHDoQdJ6iWosfA/edit?usp=sharing) |
| [lr-fbalpha](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | FB Alpha v0.2.97.39 | [4375](https://raw.githubusercontent.com/libretro/fbalpha/master/gamelist.txt) | [.DAT](https://github.com/libretro/fbalpha/blob/master/dats/FB%20Alpha%20v0.2.97.39%20(ClrMame%20Pro%20XML).dat.zip?raw=true)| [List](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing) |
| [gngeopi](https://github.com/RetroPie/RetroPie-Setup/wiki/Neo-Geo) | [Varies - read more](https://github.com/retropie/retropie-setup/wiki/neo-geo#roms) | 203 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHZVVCYmVtaUM1VlU/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1A_a_9t14uzDUMrrO0RgLDwiVUiycmclcPIs6cU6Iox8/edit?usp=sharing) |

## Crash Course in Arcade ROMs

Arcade ROMs usually distributed as ZIP files which should not be unzipped or renamed. The version of any given arcade ROM must match the specific version of the arcade emulator because ROMs change from version to version of the emulator. For example, MAME2003 is based off the MAME 0.78 source code, so you must use a MAME 0.78 ROM set with MAME2003. If you use ROMs which are from an earlier or later MAME version, such as 0.50 or 0.100 or 0.173, then those ROMs probably will not work with MAME2003.

In addition to having a version number, arcade ROMs can be formatted three ways:

* Non-merged: ROMs are standalone, each zip contain all the files needed to run the game, including any 'parent ROM'. This is the recommended format for RetroPie arcade emulators.
* Split: Some ROMS also require a 'parent ROM' to run.
* Merged: Clones are merged in the parent. You end up with more than one game in a single zip. Merged ROM sets are not supported.

For further details, see the system-specific wiki pages for [MAME](https://github.com/petrockblog/RetroPie-Setup/wiki/MAME) and [FBA](https://github.com/petrockblog/RetroPie-Setup/wiki/FinalBurn-Alpha). Recommended external resources for understanding more about MAME/FBA arcade ROMs and their usage are:

* [RetroPie Forum: How to use MAME with RetroPie Help Guide](https://retropie.org.uk/forum/topic/2859/how-to-use-mame-with-retropie-help-guide)
* [Demystifying MAME ROMs Tutorial by ChoccyHobNob](http://choccyhobnob.com/tutorials/demystifying-mame-roms/).

# Verifying and Rebuilding ROMs 
So how do you tell you have the right ROM if you aren't sure that your set matches the version required by the emulator you chose? What if you don't have the right version?

**Note: the process of verifying and rebuilding ROMs is complex and requires a substantial investment of time and effort in order to master. If your goal is to have working arcade ROMs, it is almost always simpler to download a full ROM set that has already been verified to match the arcade emulator you chose.**

In order to verify or rebuild a set, you need its DAT file and a software tool to process the DAT. DATs describe the ROM contents including filenames, file sizes, and checksums to verify contents are not incorrect or corrupt. The wiki pages for [MAME](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME), [FB Alpha](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha), and [Neo Geo](https://github.com/RetroPie/RetroPie-Setup/wiki/Neo-Geo) include DATs and detailed information about the ROM sets needed for the various arcade emulators.

Popular ROM verification tools include:

* [clrmamepro](http://mamedev.emulab.it/clrmamepro/) (Windows)
* [clrmamepro](http://www.emulab.it) (OSX)
* [romcenter](http://romcenter.com/) (Windows)
* [Romulus](http://romulus.net63.net/) (Windows)
* [RomVault](http://www.romvault.com/) (Windows)

All of the Windows tools can be run on Linux (x86) using [Wine](https://www.winehq.org/). **The remainder of this section will focus on clrmamepro for Windows, one of the most popular tools.**

## Video Tutorial

* [Easy ClrMamePro Tutorial](https://www.youtube.com/watch?v=_lssz2pAba8)

## Requirements

* The current version of RetroPie. Romsets and packaged MAME/FBA emulators occasionally change.
* A Windows PC for setting up RetroPie and running clrmamepro. This tutorial assumes you are running a 64 bit version of Windows, but the steps for 32 bit Windows will be the same once you get past downloading the clrmamepro software.

### Step 1 - Back up your ROMs
It is possible with clrmamepro to change one or two options and when it runs it will delete all your existing ROMs. OK, not really - using the default options it will make backups of any files it removes, but I have seen a lot of people when getting started mess up their ROMs beyond repair.

### Step 2 - Download [clrmamepro](http://mamedev.emulab.it/clrmamepro/#downloads)

### Step 3 - Acquire DAT files
You can download all .DAT files for all arcade emulators [**HERE**](https://github.com/HerbFargus/retropie-dat/archive/master.zip)
* For this tutorial, extract the zip file into `C:\` (but you can really put it anywhere you want)
* Open retropie-dat-master and you should see a list of folders. Each folder contains the .DAT files for the respective emulator. We will only be using `C:\retropie-dat-master\mame4all\MAME 0.37b5.dat` in this tutorial.
* Create a subdirectory `C:\retropie-dat-master\mame4allroms` (this will be used in the next step)
* Create a subdirectory `C:\retropie-dat-master\pifbaroms`

### Step 4 - Run clrmamepro for the first time
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

At this point, you could scan the ROMs folder you just selected, but we just created this folder and it is empty.  Instead, we will rebuild into this folder.

### Step 5- Rebuild a ROM set

* In the main clrmamepro window, select **"Rebuilder"**
* The destination should already be filled in for you - it is the same as the ROM path you defined above in the settings window: `C:\retropie-dat-master\mame4allroms`
* Use the browse button **"..."** to select your source path.  For example you might have a full set of MAME v0.156 ROMs - point clrmamepro to that directory as your source.
* When rebuilding there are three options: **Non-Merged, Merged, and Split**. (**NOTE**: Using Non-Merged ROMs is the most straightforward way to copy individual games to a RetroPie system.)

To understand what these options mean, we must first understand the MAME concept of **parents** and **clones**:

* **Parent:** This is _normally_ the most common variant of a ROM in the English language. In some cases it is not the best working version of the game, however.
* **Clone:** A variant of the Parent. Typically different language, or other small changes. Their .zips only contain the files that have been changed from the parent, meaning that the parent .zip must be present in the ROM directory for the clone to be ran.
* **Non-Merged Set:** parents and clones in their own stand-alone .zip files. This removes clone's dependencies on parents, meaning you can take ANY of these .zip files (even the clones), put them in the appropriate ROM directory, and they should work. However, since every .zip has every required file, they will use higher total disk space. If you only want certain MAME ROMs on your system, use this method to ensure each .zip is usable stand-alone.
* **Merged Set:** puts _all_ files of the parents and clones of the game into a single .zip file. The version that will be launched will be the version that which is the .zip's name.
* **Split Set:** parents are complete .zip files with everything needed, and clones are .zip files with _only_ their unique files, saving disk space. This means that you will have to transfer the appropriate parent .zip to your ROM directory for every clone .zip you wish to use. For example, pacman.zip (a clone), will not work without puckman.zip (its parent). This quickly gets confusing, so it's recommended to simply transfer the whole set to your ROM directory, to avoid missing file errors. **NOTE:** split sets are how most downloaded complete MAME romsets are presented.

* Click **"Rebuild..."**.  Depending on the size of the directory you chose as a source, this could take some time
* When clrmamepro is finished rebuilding, you will see a window with statistics showing how many matching files were found, how many files were created and how many were skipped.  Click "OK" 
* Repeat for any other source paths you might have.  You can rebuild from multiple sources, but leave the Destination path the same
* When finished, close the Rebuilder with the **"X"** in the upper right corner of the window

Time to find out how well your source ROMs matched up...

### Step 6 - Scan a ROM set
* In the main clrmamepro window, select **"Scanner"**
* Leave all settings at default and click **"New Scan..."**
* When clrmamepro finishes scanning, you will see a "Statistics" window with high level information and a "Scan Results" window with detailed information about your missing ROMs

### Repeat Steps 4 through 6 for the FBA ROM set#
* From clrmamepro "Profiler" window load the DAT file for PiFBA `C:\retropie-dat-master\pifba\fba_029671_od_release_10_working_roms.dat`
* From clrmamepro "Settings" windows set the ROM path to `C:\retropie-dat-master\pifbaroms`
* Use clrmamepro's "Rebuilder" to rebuild your existing ROMs to a new ROM set
* Scan the rebuilt ROMs using the "Scanner"

## Notes

That's the basics of using clrmamepro.  Some additional notes:

* Be careful with the "Fix" settings in the Scanner window and the "Remove Matched Sourcefiles" setting in the Rebuilder window. These settings will remove and rename your ROMs.
* If clrmamepro does delete any ROMs (because you told it to), you should be able to find backups in C:\clrmamepro\backup as long as you didn't change the default settings.
* clrmamepro is very stable.  It has been around for a long time, it is regularly updated and it is widely used.  If it reports problems reading your ROMs, you most likely have corrupt ROM archives (zip files) or a failing hard drive.

* If you feel the need to reset clrmamepro's settings, just delete your existing profile(s) and reload your DAT file, selecting **"Default"** settings for the new profile.  Almost all of clrmamepro's settings are per-profile.