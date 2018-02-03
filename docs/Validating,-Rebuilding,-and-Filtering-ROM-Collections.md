**Note: If you're reading this doc because you're starting an arcade emulation project, begin by reading [[Getting Started with Arcade Emulation|Arcade]].**

---

## Table of Contents
* [DAT Files: The Cornerstone](#dat-files-the-cornerstone)
* [ROM management tools](#rom-management-tools)
* [Filtering ROM collections](#filtering-rom-collections)
* [Validating and Rebuilding ROMs](#validating-and-rebuilding-roms)
***

# DAT Files: The Cornerstone

**Correct ROM versions are essential.**

So how do you tell you have the right ROM if you aren't sure that your set matches the version required by the emulator you chose? What if you don't have the right version?

**Note: the process of verifying and rebuilding ROMs is complex and requires a substantial investment of time and effort in order to master. If your goal is to have working ROMs, it is almost always simpler to download a full ROM set that has already been verified to match the emulator you chose.**

Once you begin working with software tools to help validate, rebuild, or filter your ROM collection, you will quickly encounter the need for "DAT" files, so named because they usually (but not always!) have the file extension `.dat`.

DATs describe the ROM contents including filenames, file sizes, and checksums to verify contents are not incorrect or corrupt. DATs are usually maintained either by emulator developers (such as with MAME or Final Burn Alpha) or digital preservation organizations like TOSEC and No-Intro. Almost all DATs are volunteer efforts and represent one of the most important and impressive outcomes of the video game preservation community.

In order to verify or rebuild a set, you need its corresponding DAT file and a software tool to process the DAT. For example, the authors of RetroArch recommend that Super Nintendo Entertainment System ROM collections be validated against the No-Intro "Nintendo - Super Nintendo Entertainment System" DAT. ROM collections for use with the MAME 2003 emulator should be validated against a "MAME 0.78" DAT [(such as the one found in its metadata folder)](https://github.com/libretro/mame2003-libretro/tree/master/metadata). And so on.

***
# ROM management tools

**This doc assumes that the user is working with ClrMamePro, one of the most popular ROM management tools.** ClrMamePro is not the only option available, however. Popular ROM verification tools include:

* [clrmamepro](http://mamedev.emulab.it/clrmamepro/) (Windows)
* [clrmamepro](http://www.emulab.it) (OSX)
* [romcenter](http://romcenter.com/) (Windows)
* [Romulus](http://romulus.net63.net/) (Windows)
* [RomVault](http://www.romvault.com/) (Windows & Linux)

These Windows tools can be run on Linux (x86) using [Wine](https://www.winehq.org/). RomVault can be run natively on Linux using Mono. 

***

## Filtering ROM collections

### Filtering console collections

#### No-Intro 1 Game, 1 ROM DATs (aka Parent-Clone DATs)
1G1R DATs (aka Parent-Clone DATs) allow you to create a '1 game, 1 ROM' collection from a full No-Intro set. For example, you can set ClrMamePro to filter your set based on a preference of USA ROMs > then EUR > then JPN. 

The resulting set of ROMs will feature a USA version of a game whenever possible, then look for a EUR region ROM for that title, and finally use the JPN only if no USA or EUR ROMs are in the folder. All regions with releases in a given system are supported (in other words you could set a preference of Spain > Europe > USA > Italy > Japan > etc.)

No-Intro's DAT-o-MATIC (DoM) also allows you to download DATs for their currently supported systems, and DATs in latest Logiqx's XML format which contain Parent-Clone information for the system. Both of these DATs can be obtained, as available, from the DAT-o-MATIC on the No-Intro website.

### Filtering arcade collections

The [lr-mame2003](https://github.com/libretro/mame2003-libretro/tree/master/metadata) core and [lr-mame2010](https://github.com/libretro/mame2010-libretro/tree/master/metadata) core maintain a `catver.ini` file in their github repositories. `catver.ini` can be used with ROM management tools such as [ROMLister](https://www.waste.org/~winkles/ROMLister/) and [Simple Arcade Multifilter](https://retropie.org.uk/forum/topic/7606/simple-arcade-multifilter-app-for-mame-and-fb-alpha-sets-get-rid-of-adult-and-mahjong-games/) in order to sort and filter a MAME collection by genre or by other tags, such as whether it includes "Mature" content.

***

# Validating and Rebuilding ROMs

It is possible to 'rebuild' from one version of an ROM collection to another. If you also have access to ROMs from a newer or older ROM collection you can 'roll forward' or 'roll back' your ROM version.

The wiki pages for [MAME](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME), [FB Alpha](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha), and [Neo Geo](https://github.com/RetroPie/RetroPie-Setup/wiki/Neo-Geo) include DATs and detailed information about the ROM sets needed for the various arcade emulators.

The remainder of this section of the docs is devoted to a demonstration of using ClrMamePro to rebuild and validate arcade ROM sets. The tutorial uses a MAME 0.37b5 collection as well as a PiFBA collection (in the video version) to demonstrate the process.

* **[View the ClrMamePro video tutorial on YouTube](https://www.youtube.com/watch?v=_lssz2pAba8)**
* **[Read the written ClrMamePro tutorial below](#written-clrmamepro-tutorial)**

Before manipulating arcade ROMs, please be sure you are familiar with their unique terminology.

***

#### Crash Course in Arcade ROM terminology

- **ROM, ROM set, and romset**: Arcade games are packaged as zip files, most of which are composed of more than one individual 'ROM' files. That is why some resources refer to an individual arcade game as a ROM (like people use to describe a zipped game cartridge ROM) while other resources refer to an individual game as a ROM set or romset.
- **ROM version or ROM set version**: Each version of an arcade emulator must be used with ROMs that have the same exact version number. For example, MAME 0.37b5 ROMs are required by the MAME4ALL emulator, but will not work correctly with the lr-mame2010 emulator, which requires MAME 0.139 ROMs.
- **Sample**: Some games require an additional zip file with recorded sounds or music in order for audio to work correctly. The path where these samples should be copied varies from emulator to emulator.
- **CHD**: Some MAME games require data from an internal hard drive, CD-ROM, laserdisk, or other media in order to be emulated -- those forms of media are packaged as CHD files. CHD files should be copied to subfolders within the folder where the MAME ROM zips have been installed.

In addition to having a version number, arcade ROMs can be formatted four ways:

- **Non-merged ROM**: All ROMs can be used standalone because each zip contains all the files needed to run that game, including any files from 'parent ROMs'. The only exception are BIOS ROMs, which are formatted as 'Split' and must be kept in the same folder as the ROM set which uses it. **Non-Merged ROM sets are the recommended format for RetroPie arcade emulators.**
- **Full Non-merged**: All ROMs can be used standalone because each zip contains all the files needed to run that game, including any ROMs from 'parent' ROM sets and BIOS sets. (ClrMamePro users: access through the "Advanced" button in the Rebuild and Scanner menus.)
- **Split**: Some ROMS that are considered clones, translations, or bootlegs also require a "parent ROM" to run. The parent ROM is often the first or most common variant of a game. In some cases the parent is not the most popular or best working version of the game, however. For example, in a Split set pacman.zip (a clone), will not work without puckman.zip (its parent).
- **Merged**: Clones are merged into the parent ROM zip, meaning that more than one game is stored per file. Merged ROM sets are not recommended.

***

### Written ClrMamePro tutorial 

### Step 1 - Back up your ROMs
It is possible with ClrMamePro to change one or two options and when it runs it will delete all your existing ROMs. OK, not really - using the default options it will make backups of any files it removes, but it is still possible to mess up their ROMs beyond repair when getting started with ClrMamePro.

### Step 2 - Download [ClrMamePro](http://mamedev.emulab.it/clrmamepro/#downloads)

### Step 3 - Acquire DAT files
You can download all .DAT files for all arcade emulators [**HERE**](https://github.com/HerbFargus/retropie-dat/archive/master.zip)
* For this tutorial, extract the zip file into `C:\` (but you can put it anywhere you want)
* Open retropie-dat-master and you should see a list of folders. Each folder contains the .DAT files for the respective emulator. We will only be using `C:\retropie-dat-master\mame4all\MAME 0.37b5.dat` in this tutorial.
* Create a subdirectory `C:\retropie-dat-master\mame4allroms` (this will be used in the next step)
* Create a subdirectory `C:\retropie-dat-master\pifbaroms`

### Step 4 - Run ClrMamePro for the first time
* Run `C:\clrmamepro\cmpro64.exe`.  The welcome screen explains that common first steps are to 1) Create a Profile, 2) Set up your paths and 3) Scan your ROMs. We will be doing things slightly differently, in order to leave your source ROMs intact.  
* Click OK to the Welcome screen
* Click **"Add DatFile..."** and open the MAME4ALL DAT file at `C:\retropie-dat-master\mame4all\MAME 0.37b5.dat`
* Accept the default profile location of [PROFILES], click **"OK"**
* Select **"[NEW DATFILES]"** in the left-hand pane and select **"MAME 0.37b5"** in the right-hand pane
* Click **"Load / Update"**
* ClrMamePro will ask you how to generate the settings for this datfile, click **"Default"** (it is possible it will throw a warning but just select **"ok to all"** and continue on)
* You are now at the main window for clrmamepro.  We still need to set our paths, so click **"Settings"**
* Verify **"ROM-Paths"** is the selected option in the upper-left corner drop down menu
* Click the **"Add..."** button
* Select the folder you created in the last step called `C:\retropie-dat-master\mame4allroms` and click **"OK"**
* Close the settings window with the **"X"** button in the upper right

At this point, you could scan the ROMs folder you just selected, but we just created this folder and it is empty.  Instead, we will rebuild into this folder.

### Step 5- Rebuild a ROM set

* In the main ClrMamePro window, select **"Rebuilder"**
* The destination should already be filled in for you - it is the same as the ROM path you defined above in the settings window: `C:\retropie-dat-master\mame4allroms`
* Use the browse button **"..."** to select your source path. For example you might have a full set of MAME v0.156 ROMs - point ClrMamePro to that directory as your source.
* When rebuilding there are three options: **Non-Merged, Merged, and Split**. (**NOTE**: Using Non-Merged ROMs is the most straightforward way to copy individual games to a RetroPie system.
* Click **"Rebuild..."**.  Depending on the size of the directory you chose as a source, this could take some time
* When ClrMamePro is finished rebuilding, you will see a window with statistics showing how many matching files were found, how many files were created and how many were skipped.  Click "OK" 
* Repeat for any other source paths you might have.  You can rebuild from multiple sources, but leave the Destination path the same
* When finished, close the Rebuilder with the **"X"** in the upper right corner of the window

Time to find out how well your source ROMs matched up...

### Step 6 - Scan a ROM set
* In the main ClrMamePro window, select **"Scanner"**
* Leave all settings at default and click **"New Scan..."**
* When ClrMamePro finishes scanning, you will see a "Statistics" window with high level information and a "Scan Results" window with detailed information about your missing ROMs

### Notes

* Be careful with the "Fix" settings in the Scanner window and the "Remove Matched Sourcefiles" setting in the Rebuilder window. These settings will remove and rename your ROMs.
* If ClrMamePro does delete any ROMs (because you told it to), you should be able to find backups in C:\clrmamepro\backup as long as you didn't change the default settings.
* ClrMamePro is very stable.  It has been around for a long time, it is regularly updated and it is widely used.  If it reports problems reading your ROMs, you most likely have corrupt ROM archives (zip files) or a failing hard drive.

* If you feel the need to reset ClrMamePro's settings, just delete your existing profile(s) and reload your DAT file, selecting **"Default"** settings for the new profile.  Almost all of ClrMamePro's settings are per-profile.
