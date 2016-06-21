|Version|
|---|
|4.0|

# Updating RetroPie

The conventional way to update RetroPie and install new features is through the setup script. 

The setup script can be accessed from the **RetroPie menu** in emulationstation. 

It can also be accessed from the terminal with 
```
sudo /home/pi/RetroPie-Setup/retropie_setup.sh
```

**Before making any major updates it is important to make backups just in case [(see backup options below)](https://github.com/RetroPie/RetroPie-Setup/wiki/Updating-RetroPie/_edit#making-a-backup-option-1).**

## Using the RetroPie Setup Script

- **The very first thing** you'll want to do before you do anything is select **Update RetroPie-Setup Script** as this will update the latest changes to the setup script.

#### If updating from 3.x and earlier select: Manage Packages >> Quick Install and Update All Installed Packages

![4 0beta](https://cloud.githubusercontent.com/assets/10035308/16218285/f06f3ba8-3738-11e6-9ccc-be601172713b.png)

_Note that the **Script Version** only shows what version the RetroPie Setup Script is at, it is not necessarily the version of RetroPie that you currently have installed. The **Last Commit** shows the latest commit or change to the RetroPie Setup Script since your last update of the script._
- **Manage Packages:** This is where you will install/update all your emulators, install controller drivers (like the ps3 or xboxdrv) along with ports and other optional packages.
- **Setup / Tools:** Configure tools, splashscreens, themes, and other configurations here.
- **Uninstall RetroPie:** Pretty self explanatory, uninstalls retropie.
- **Updated Setup Script:** Updates your setup script to the latest version.
- **Reboot:** Reboots your system.

**Manage Packages**

![quick install](https://cloud.githubusercontent.com/assets/10035308/15950393/9dcccd3c-2e6b-11e6-9d42-065b3234edc1.png)
- **Quick Install: If wanting to update select this option - this is intended as a first install - ie on top of raspbian, or if coming from a 3.x retropie.**
- **Update All Installed Packages:** This will update all installed packages.
- **Core:** These are essential packages needed for RetroPie to run. Do not remove them.
- **Main:** These are the main emulators that come installed with the RetroPie SD image.
- **Optional:** These are optional packages that are working but aren't included with the RetroPie SD image.
- **Drivers:** Here you install gamepad drivers like the PS3 or Xboxdrv.
- **Experimental:** These packages have not been fully tested and may have bugs.
 
**Core Packages**

![core packages](https://cloud.githubusercontent.com/assets/10035308/15919781/a18d06ca-2dd1-11e6-9cec-136fc5f0e727.png)

Each section of the manage packages portion of the setup script have the option to install/update all packages and remove all installed packages. You can also update/install and remove packages individually.

The core components needed for RetroPie to function are:
- **RetroArch:** Frontend for the libretro api, necessary for most emulators to run.
- **EmulationStation:** Frontend for sorting and launching all of your games.
- **RetroPie Menu:** Menu in emulationstation for simpler configuration of your system.
- **Runcommand:** The runcommand launch menu that assists launching your games with proper configurations see related wiki page [HERE](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand).

### Updating/Installing individual packages

You can update/install and remove packages individually.

When selecting a package there is also a help guide with extra information specific to that package:

![individual](https://cloud.githubusercontent.com/assets/10035308/15987047/5414269a-2fd8-11e6-87ff-a0021e244054.png)

**Package Help:**

![package_help](https://cloud.githubusercontent.com/assets/10035308/15987048/542d760e-2fd8-11e6-909f-827b120dfc34.png)

The Package Help for each emulator should show you:
- The name of the package
- ROM extensions
- ROM folder
- BIOS filename and folder if applicable

#### Latest SD image

If you are worried about conflicts during an update you can always just start with the latest fresh sd image which can be downloaded [**here**](https://retropie.org.uk/download/) and just copy all your files back over onto that instead of updating from an older image.

## Making a Backup (Option 1)

You can create an sd image of your current sd card with [win32diskimager](http://sourceforge.net/projects/win32diskimager/files/Archive/) (if you're on windows)

- Plug your sd card into your laptop (you will need a sd card reader for this)
- Open win32diskimager as an administrator (you can right click on it to run as an administrator)

![runasadministrator](https://cloud.githubusercontent.com/assets/10035308/10266141/babb3420-6a0c-11e5-9f20-c26297b9fbbf.png)

- make sure you have the correct drive letter for your SD card! 
- define the file path that you want to save your .img backup as

![win32diskimager](https://cloud.githubusercontent.com/assets/10035308/10266156/79baadf6-6a0d-11e5-9c98-62211328c68a.png)

- Click **read** to create your backup. (after you've backed this image up if you screw something up later and want to start from this image you can just click write and it will write this sd image back to your sd card.)
- note if you have a 64GB sd card it will create a 64GB backup file even if you don't have it completely filled up. If you don't want a file that large see the next option.   

## Making a Backup (Option 2)

if you don't want to create a sd image you can just back up your bios, roms, and configuration files from the samba shares

![samba](https://cloud.githubusercontent.com/assets/10035308/12865893/d2eab264-cc77-11e5-9ec6-003e13322a5a.png)

## Making a Backup (OS X)

Open a terminal window and type `diskutil list`. A list of all hard disks and partitions shows up. Find a partition with the name `boot`. The related /dev/disk* is your retropie sd card. Type `sudo dd if=/dev/disk* of=backup.img bs=1m` to write a disk image to your home directory.