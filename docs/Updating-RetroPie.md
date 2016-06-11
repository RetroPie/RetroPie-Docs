|Version|
|---|
|3.8.1|

# Updating RetroPie

The conventional way to update RetroPie and install new features is through the setup script. 

The setup script can be accessed from the **RetroPie menu** in emulationstation. 

It can also be accessed from the terminal with 
```
cd RetroPie-Setup
sudo ./retropie_setup.sh
```

**Before making any major updates it is important to make backups just in case (see backup options below).**

## Using the RetroPie Setup Script

![setupscript](https://cloud.githubusercontent.com/assets/10035308/13228202/e3f20a02-d957-11e5-9b10-3e3dc7da2bac.png)

- **The very first thing** you'll want to do before you do anything is select **Update RetroPie-Setup Script** as this will update the latest changes to the setup script.

- Note that the **Script Version** only shows what version the RetroPie Setup Script is at, it is not necessarily the version of RetroPie that you currently have installed. The **Last Commit** shows the latest commit or change to the RetroPie Setup Script since your last update of the script.

- **Binary Based Installation:** If you wish to do a full update of RetroPie, this is the option you should choose. a backup is highly recommended before choosing this option

- **Source-based installation:** very rarely if ever should you use this as it takes more than 24 hours to run and likely will end up with some broken non-working emulators due to unfixed bugs

- **Setup / Configuration:** this is where you can update configurations, install new themes, controller drivers, etc. many of these options are also on the retropie menu in emulationstation

- **Experimental Packages:** these are emulators and options that may be potentially unstable but are worth checking out if you are feeling ambitious

- **Install Individual Emulators from Binary or Source:** This is where you will update individual emulators- you will almost always update from binary as they are more frequently updated, have less bugs, and are much quicker to install. There will be rare occasions where you may need to update from source but when in doubt just choose binary and you should be fine. 

- **Uninstall RetroPie:** This will uninstall all of RetroPie. You are also given the option to remove all the dependencies that were needed for RetroPie. Note that this option is still being tested so there may be some things that will still need to be manually removed like symlinks.

- **Perform Reboot:** This will reboot your system.

#### Latest SD image

If you are worried about conflicts during an update you can always just start with the latest fresh sd image which can be downloaded [**here**](https://github.com/RetroPie/RetroPie-Setup/releases) and just copy all your files back over onto that instead of updating from an older image.

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

# 4.0 DEV setup script

If you update your setup script and realise it doesn't match the format above, the following explains the new layout which makes it easier to add/remove/update your packages.

![menu](https://cloud.githubusercontent.com/assets/10035308/15919783/a1a676f0-2dd1-11e6-8deb-34f3fed7fa08.png)
- **Manage Packages:** This is where you will install/update all your emulators, install controller drivers (like the ps3 or xboxdrv) along with ports and other optional packages.
- **Setup / Tools:** Configure tools, splashscreens, themes, and other configurations here.
- **Uninstall RetroPie:** Pretty self explanatory, uninstalls retropie.
- **Updated Setup Script:** Updates your setup script to the latest version.
- **Reboot:** Reboots your system.

**Manage Packages**

![quick install](https://cloud.githubusercontent.com/assets/10035308/15950393/9dcccd3c-2e6b-11e6-9d42-065b3234edc1.png)
- **Quick Install:** **If wanting to update select this option**: This will install core and main packages which is equivalent to the basic retropie sd image.
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