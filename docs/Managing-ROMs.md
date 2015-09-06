RetroPie uses forks of the [MAME](http://mamedev.org/) and [FinalBurn Alpha](http://www.barryharris.me.uk/) emulators that work well on the Raspberry Pi hardware, but are based on older versions of the original code.  Your ROMs may be for earlier or later versions of MAME/FBA and if they are, they most likely will not work. For a list of each emulator and the .dat file for the romsets they use see **[here](http://smartretro.co.uk/forums/viewtopic.php?f=3&t=68) or below**

See also: [MAME](https://github.com/petrockblog/RetroPie-Setup/wiki/MAME), [FBA](https://github.com/petrockblog/RetroPie-Setup/wiki/FinalBurn-Alpha)

This is where [clrmamepro](http://mamedev.emulab.it/clrmamepro/) comes in.  Clrmamepro is a Windows utility for verifying and managing your ROMs. It can also run on Linux, using [Wine](https://www.winehq.org/). Clrmamepro is very powerful, but also somewhat complex and not friendly to new users.

Here are the steps to getting started with clrmamepro.

##Requirements:#
* A Raspberry Pi running a RetroPie v2.4.x, v2.5.x or v2.6.x SD card image.  Other images may work, but they have not been tested with these instructions.  All you need from the RetroPie image are the DAT files (explained below).
* A Windows PC for setting up RetroPie and running clrmamepro. This tutorial assumes you are running a 64 bit version of Windows, but the steps for 32 bit Windows will be the same once you get past downloading the clrmamepro software.

## Step 1 - Back up your ROMs#
It is possible with clrmamepro to change one or two options and when it runs it will delete all your existing ROMs. OK, not really - using the default options it will make backups of any files it removes, but I have seen a lot of people when getting started mess up their ROMs beyond repair.

##Step 2 - Download [clrmamepro](http://mamedev.emulab.it/clrmamepro/download.htm)#
The version at the time of this article is 4.016.  I would recommend the 64 bit version if you are running a 64 bit OS, it will be significantly faster.  I would also recommend the zip version, just extract it to C:\clrmamepro.  There's no need to run the installer.

##Step 3 - Acquire DAT files#
DAT files are the [XML-based](http://en.wikipedia.org/wiki/XML) database definitions of the exact ROMs an emulator uses. Using the DAT files and [CRC](http://en.wikipedia.org/wiki/Cyclic_redundancy_check) checks, clrmamepro is able to identify which of your ROMs are valid for a given emulator.

The RetroPie SD card image install includes DAT files for MAME4ALL and PiFBA. You can use [WinSCP](http://winscp.net/eng/index.php) to connect to your RasPi and copy the DAT files back to your Windows PC.

* Create a new directory in Windows, `C:\RetroPieRoms`
* Create a sub directory, `C:\RetroPieRoms\MAME4ALL`
* Create a sub directory, `C:\RetroPieRoms\PiFBA`
* Download and install [WinSCP](http://winscp.net/eng/download.php)
* Launch WinSCP and connect to your Pi.  You can get the IP address of the Pi by typing `ifconfig` on the Pi.  It is also displayed on the Pi's screen at the end of the boot up sequence.
* If you haven't changed any settings on your RetroPie, the default username is `pi` and the default password is `raspberry`
* WinSCP is pretty straight forward, just navigate to your local Windows directory in the left-hand pane and navigate to the remote, Pi directory in the right-hand pane.   You can copy files by dragging them between the two panes.
* Copy the DAT from your Raspberry Pi `/opt/retropie/emulators/mame4all/clrmame.dat` to your Windows PC `C:\RetroPieRoms\clrmame.dat`
* Copy the ZIP from `/opt/retropie/emulators/pifba/fba_029671_clrmame_dat.zip` to `C:\RetroPieRoms\fba_029671_clrmame_dat.zip`
* Extract `C:\RetroPieRoms\fba_029671_clrmame_dat.zip` to `C:\RetroPieRoms\`.  You should have two new DAT files: `fba_029671_od_release_10_working_roms.dat` and `fba_029671_od_release_10_non_working_roms.dat`.  We will only be using `fba_029671_od_release_10_working_roms.dat` in this tutorial.

##Step 4 - Run clrmamepro for the first time#
* Run `C:\clrmamepro\cmpro64.exe`.  The welcome screen explains that common first steps are to 1) Create a Profile, 2) Set up your paths and 3) Scan your ROMs. We will be doing things slightly differently, in order to leave your source ROMs intact.  
* Click OK to the Welcome screen
* Click **"Add DatFile..."** and open the MAME4ALL DAT file at `C:\RetroPieRoms\clrmame.dat`
* Accept the default profile location of [PROFILES], click **"OK"**
* Select **"[NEW DATFILES]"** in the left-hand pane and select **"MAME4ALL ROMs Datfile"** in the right-hand pane
* Click **"Load / Update"**
* Clrmamepro will ask you how to generate the settings for this datfile, click **"Default"**
* You are now at the main window for clrmamepro.  We still need to set our paths, so click **"Settings"**
* Verify **"ROM-Paths"** is the selected option in the upper-left corner drop down menu
* Click the **"Add..."** button
* Select the folder `C:\RetroPieRoms\MAME4ALL` and click **"OK"**
* Close the settings window with the **"X"** button in the upper right

At this point, you could scan the ROMs folder you just selected, but we just created this folder and it is empty.  Instead, we will rebuild into this folder.  Clrmamepro can scan other locations for matching ROMs and build a new ROM set from them.

##Step 5- Rebuild a ROM set#
* In the main clrmamepro window, select **"Rebuilder"**
* The destination should already be filled in for you - it is the same as the ROM path you defined above in the settings window: `C:\RetroPieRoms\MAME4ALL`
* Use the browse button **"..."** to select your source path.  For example you might have a full set of MAME v0.156 ROMs - point clrmamepro to that directory as your source.
* Click **"Rebuild..."**.  Depending on the size of the directory your chose as a source, this could take some time
* When clrmamepro is finished rebuilding, you will see a window with statistics showing how many matching files were found, how many files were created and how many were skipped.  Click "OK" 
* Repeat for any other source paths you might have.  You can rebuild from multiple sources, but leave the Destination path the same
* When finished, close the Rebuilder with the **"X"** in the upper right corner of the window

Time to find out how well your source ROMs matched up...

##Step 6 - Scan a ROM set#
* In the main clrmamepro window, select **"Scanner"**
* Leave all settings at default and click **"New Scan..."**
* When clrmamepro finishes scanning, you will see a "Statistics" window with high level information and a "Scan Results" window with detailed information about your missing ROMs

##Repeat Steps 4 through 6 for the FBA ROM set#
* From clrmamepro "Profiler" window load the DAT file for PiFBA `C:\RetroPieRoms\fba_029671_od_release_10_working_roms.dat`
* From clrmamepro "Settings" windows set the ROM path to `C:\RetroPieRoms\PiFBA`
* Use clrmamepro's "Rebuilder" to rebuild your existing ROMs to a new ROM set
* Scan the rebuilt ROMs using the "Scanner"

##Notes#

That's the basics of using clrmamepro.  Some additional notes:

* Be careful with the "Fix" settings in the Scanner window and the "Remove Matched Sourcefiles" setting in the Rebuilder window. These settings will remove and rename your ROMs.
* If clrmamepro does delete any ROMs (because you told it to), you should be able to find backups in C:\clrmamepro\backup as long as you didn't change the default settings.
* clrmamepro is very stable.  It has been around for a long time, it is regularly updated and it is widely used.  If it reports problems reading your ROMs, you most likely have corrupt ROM archives (zip files) or a failing hard drive.

* If you feel the need to reset clrmamepro's settings, just delete your existing profile(s) and reload your DAT file, selecting **"Default"** settings for the new profile.  Almost all of clrmamepro's settings are per-profile.

## Video Tutorial:
<a href="https://www.youtube.com/watch?v=SuWl2GdEfDA" target="_blank"><img src="https://i.ytimg.com/vi_webp/SuWl2GdEfDA/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a>

# List of Emulators and Their Respective Romsets:

RetroPie 3.0.0 MAME Versions

These details are as per the default installed binaries on the RetroPie 3.0.0 image.

**Important**

In 3.0.0 some emulators share directories, so you need to choose which FBA, NeoGeo and mame4all version you want.
So you can have 1 romset for each of these (mame4all, FBA, NeoGeo, advmame)

See [here](http://smartretro.co.uk/forums/viewtopic.php?f=3&t=68) for RetroPie 2.6
### [PiFBA](http://sourceforge.net/projects/pifba/)
```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/emulators/pifba
Config Dir: /opt/retropie/configs/fba/fba2x.cfg
```
MAME Version: **FBA 0.2.96.71** which is based on MAME 0.114 (April 2007)

Size: 3.62 GB

Romsets emulated: 684 (no clones)

Dat File: [fba_0.2.96.71_clrmame_dat.zip](http://smartretro.co.uk/forums/download/file.php?id=17&sid=51593df3da1e20af98e425975a9e6f98)

Dat File (With merge data): [FB Alpha v0.2.96.71 (ClrMame Pro).dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHaXNtSWpzb3JlTjg/view?usp=sharing)

All clones (current tested) non-working\mahjong\quiz\adult\casino\rythm removed

Romsets emulated: 291

Dat File: [fba_029671_od_release_10_working_roms_filtered.zip] (https://www.dropbox.com/s/mooc4mzesl3r2og/fba_029671_od_release_10_working_roms_filtered.zip?dl=0)

[**PiFBA COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing)  feel free to contribute to the list.

### [lr-fba](https://github.com/libretro/fba-libretro) 
```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/libretrocores/fbalibretro
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

Dat File: [FB Alpha v0.2.97.30.dat.zip](http://smartretro.co.uk/forums/download/file.php?id=21&sid=51593df3da1e20af98e425975a9e6f98)

Neo Geo Only .Dat File: [fba-lr-neogeo](http://s000.tinyupload.com/download.php?file_id=05558959831361649927&t=0555895983136164992714492)

[**lr-fba COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1rWO7Lm0bTGNpak6J-CPzde0GNIDP0NHDoQdJ6iWosfA/edit?usp=sharing)  feel free to contribute to the list.

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

Dat File: [mame4all-037b5-RetroPie-260.zip](http://smartretro.co.uk/forums/download/file.php?id=20&sid=51593df3da1e20af98e425975a9e6f98)

Dat File (with merge data): [MAME 0.37b5.dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHNDNHcl8tcUNIcDA/view?usp=sharing)

Dat File (no clones, no neogeo): [mame4all-no-clones-no-neogeo](http://s000.tinyupload.com/index.php?file_id=07696766073490048881)

[**MAME4ALL-PI COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing)  feel free to contribute to the list.

### [lr-imame4all)](https://github.com/libretro/imame4all-libretro)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-mame4all
Binary Dir: /opt/retropie/libretrocores/mamelibretro/
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

Dat File: [mame4all-037b5-RetroPie-260.zip](http://smartretro.co.uk/forums/download/file.php?id=20&sid=51593df3da1e20af98e425975a9e6f98)

Dat File (with merge data): [MAME 0.37b5.dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHNDNHcl8tcUNIcDA/view?usp=sharing) 

Dat File (no clones, no neogeo): [mame4all-no-clones-no-neogeo](http://s000.tinyupload.com/index.php?file_id=07696766073490048881)

[**lr-IMAME4ALL COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing)  feel free to contribute to the list.

### [GnGeo 0.8](https://github.com/ymartel06/GnGeo-Pi)
```shell
Roms Dir: /home/pi/RetroPie/roms/neogeo
Binary Dir: /opt/retropie/emulators/gngeopi/bin
Config Dir: /opt/retropie/configs/neogeo
```
MAME Version: Based on **0.138** romsets (May 2010)

Romsets emulated: 203

Dat File: [pandora_gngeo_084_dat.zip](http://smartretro.co.uk/forums/download/file.php?id=22&sid=51593df3da1e20af98e425975a9e6f98)

All clones non-working\mahjong\quiz removed

Romsets emulated: 128

Dat File: [pandora_gngeo_084_filtered.zip](https://www.dropbox.com/s/3s1exbmb40yefgx/pandora_gngeo_084_filtered.zip?dl=0)

[**GnGeo-Pi COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1A_a_9t14uzDUMrrO0RgLDwiVUiycmclcPIs6cU6Iox8/edit?usp=sharing)  feel free to contribute to the list.

### [AdvanceMAME 0.94.0 and 1.2](http://sourceforge.net/projects/advancemame/files/advancemame/0.94.0/)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-advmame
Binary Dir: /opt/retropie/emulators/advmame/bin
Config Dir: /opt/retropie/configs/mame-advmame
```
MAME Version: Based on **MAME 0.94** (March 2005) or (for 1.2) Based on **MAME 0.106** (May 2006)

Size: 11.6GB (0.94.0) Size: 14.8GB (1.2)

Romsets Emulated: 5563 (0.94.0) 6166 (1.2) (includes clones etc..)

Active Sets (For 0.94.0) 5563/5563
* Parents 1236/1236
* Clones 2473/2473
* Others 1829/1829
* BIOS 25/25

Active Sets (For 1.2) 6166/6166
* Parents 1388/1388
* Clones 2824/2824
* Others 1928/1928
* BIOS 26/26

Dat File: [advmame-0.94-RetroPie-260.7z](http://smartretro.co.uk/forums/download/file.php?id=18&sid=51593df3da1e20af98e425975a9e6f98)

[**AdvMame .94 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1AEQ94buG0rvbW0xdnYKeuEhHeCbuZlRfRJQCb1Dt8fw/edit?usp=sharing)  feel free to contribute to the list.

Dat File: [advmame12-106.7z](http://smartretro.co.uk/forums/download/file.php?id=23&sid=51593df3da1e20af98e425975a9e6f98)

[**AdvMame 1.2 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1RapyxChe2BMOfbX-FsCup9SXGxvS1WmXAofwaTJtmxc/edit?usp=sharing)  feel free to contribute to the list.

**List courtesy of Floob** 