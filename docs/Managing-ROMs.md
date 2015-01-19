RetroPie uses forks of the [MAME](http://mamedev.org/) and [FinalBurn Alpha](http://www.barryharris.me.uk/) emulators that work well on the Raspberry Pi hardware, but are based on older versions of the original code.  Your ROMs may be for earlier or later versions of MAME/FBA and if they are, they most likely will not work.

This is where [clrmamepro](http://mamedev.emulab.it/clrmamepro/) comes in.  Clrmamepro is a Windows utility for verifying and managing your ROMs. It can also run on Linux, using [Wine](https://www.winehq.org/). Clrmamepro is very powerful, but also somewhat complex and not friendly to new users.

Here is a step to getting started with clrmamepro.

##Requirements:#
* A Raspberry Pi with RetroPie v2.4.2 Beta SD card image
* A Windows PC for setting up RetroPie and running clrmamepro. This tutorial assumes you are running a 64 bit version of Windows.

## Step 1 - Back up your ROMs#
It is possible with clrmamepro to change one or two options and when it runs it will delete all your existing ROMs. OK, not really - using the default options it will make backups of any files it removes, but I have seen a lot of people when getting started mess up their ROMs beyond repair.

##Step 2 - Download [clrmamepro](http://mamedev.emulab.it/clrmamepro/download.htm)#
The version at the time of this article is 4.016.  I would recommend the 64 bit version if you are running a 64 bit OS, it will be significantly faster.  I would also recommend the zip version, just extract it to C:\clrmamepro.  There's no need to run the installer.

##Step 3 - Acquire DAT files#
DAT files are the [XML-based](http://en.wikipedia.org/wiki/XML) database definitions of the exact ROMs an emulator uses. Using the DAT files and [CRC](http://en.wikipedia.org/wiki/Cyclic_redundancy_check) checks, clrmamepro is able to identify which of your ROMs are valid for a given emulator.

The RetroPie SD card image install includes DAT files for MAME4ALL and PiFBA. Use [WinSCP](http://winscp.net/eng/index.php) to connect to your RasPi and copy the DAT files back to your Windows PC.

* Create a new directory in Windows, C:\RetroPieRoms
* Create a sub directory, C:\RetroPieRoms\MAME4ALL
* Create a sub directory, C:\RetroPieRoms\PiFBA
* Copy the DAT from /opt/retropie/emulators/mame4all/clrmame.dat to C:\RetroPieRoms\clrmame.dat
* Copy the DAT from /opt/retropie/emulators/pifba/xxx.zip to C:\RetroPieRoms\xxx.zip
* Extract C:\RetroPieRoms\xxx.xip to C:\RetroPieRoms.  You should have two new DAT files: fba_029671_od_release_10_working_roms.dat and xxx.dat

##Step 4 - Run clrmamepro for the first time#
* Run C:\clrmamepro\cmpro64.exe.  The welcome screen explains that common first steps are to 1) Create a Profile, 2) Set up your paths and 3) Scan your ROMs. We will be doing things slightly differently, in order to leave your source ROMs intact.  
* Click OK to the Welcome screen
* Click "Add DatFile..." and open the MAME4ALL DAT file at C:\RetroPieRoms\clrmame.dat
* Accept the default profile location of [PROFILES], click OK
* Select "[NEW DATFILES]" in the left-hand pane and select "MAME4ALL ROMs Datfile" in the right-hand pane
* Click "Load / Update"
* clrmamepro will ask you how to generate the settings for this datfile, select "Default"
* You are now at the main window for clrmamepro.  We still need to set our paths, so click "Settings"
* "ROM-Paths" should be selected in the drop down in the upper left, click the "Add..." button
* Select the folder C:\RetroPieRoms\MAME4ALL and click "OK"
* Close the settings window with the X button in the upper right

At this point, you could scan the ROMs folder you just selected, but we just created this folder and it is empty.  Instead, we will rebuild into this folder.  clrmamepro can scan other locations for matching ROMs and build a new ROM set from them.

##Step 5- Rebuild a ROM set#
* In the main clrmamepro window, select "Rebuilder"
* The destination should already be filled in for you - it is the same as the ROM path you defined above: C:\RetroPieRoms\MAME4ALL
* Use the browse button "..." to select your source path.  For example you might have a full set of MAME v0.156 ROMs - point clrmamepro to that directory as your source.
* Click "Rebuild...".  Depending on the size of the directory your chose as a source, this could take some time
* When clrmamepro is finished, you will see a window with statistics showing how many matching files were found, how many files were created and how many were skipped.  Click "OK" 
* Repeat for any other source paths you might have. When finished, close the Rebuilder with the "X" in the upper right corner of the window

Time to find out how well the clrmamepro rebuild went...

##Step 6 - Scan a ROM set#
* In the main clrmamepro window, select "Scanner"
* Leave all settings at default and click "New Scan..."
* When clrmamepro finishes scanning, you will see a "Statistics" window with high level information and a "Scan Results" window with detailed information about your missing ROMs

That's the basics of using clrmamepro.  Some additional notes:

* Be careful with the "Fix" settings in the Scanner window and the "Remove Matched Sourcefiles" setting in the Rebuilder window. These settings will remove and rename your ROMs.
* If clrmamepro does delete any ROMs (because you told it to), you should be able to find backups in C:\clrmamepro\backup as long as you didn't change the default settings.
* clrmamepro is very stable.  It has been around for a long time, it is regularly updated and it is widely used.  If it reports problems reading your ROMs, you most likely have corrupt archives (zip files) or a failing hard drive.

