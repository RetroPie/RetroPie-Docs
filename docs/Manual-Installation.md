## Install Raspbian/Raspberry Pi OS

This guide is a manual process to recreate the stock SD image RetroPie released on the [RetroPie Website](https://retropie.org.uk/download/) for the Raspberry Pi. If you aren't comfortable with the terminal you would be wise to just use the RetroPie SD image provided. 

If you are trying to follow this guide because you want the PIXEL desktop environment, you can already install it on the stock RetroPie SD image by following the guide [here](FAQ#where-did-the-desktop-go)

RetroPie can also be installed on most debian based distros, a guide for installing RetroPie on Ubuntu on a PC can be found [here](Debian)

The RetroPie SD image is built on top of Raspberry Pi OS Lite (without the PIXEL desktop environment), RetroPie can also be installed on top of the full Raspberry Pi OS but you can't run Retropie and PIXEL at the same time, you will need to logout of the PIXEL desktop environment in order to run emulationstation and the emulators RetroPie installs. 

You can download a fresh Raspberry Pi OS image from [here](http://www.raspberrypi.org/downloads). The image can be installed the same way as the RetroPie image as described [here](First-Installation)). 

You can check your free disk space with
```
df -h
```

/dev/root is your main partition. Then, I would recommend to update and upgrade the existing APT packages with
```
sudo apt update && sudo apt upgrade
```

### Verify Locale Settings
Most of the install scripts will attempt to install a variety of packages and libraries that each emulator requires. These installations will fail if your system locale settings are invalid. You can easily verify this by executing `locale` command. A valid locale will return values set for all options, such as in the example below.

```
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8
```

If any of the above configuration lines are unset (particularly LANG, LANGUAGE, and LC_ALL), you should set them before installing RetroPie. The easiest way to set each item is to use the `update-locale` command, such as `sudo update-locale LC_ALL="en_US.UTF-8"`.

Users can also set the locale through the `raspi-config` tool.

A reboot is required before these changes will be reflected by the `locale` command.

### Verify the allocated video memory (memory split)

**NOTE:** The below configurations are not needed when installing on a Raspberry Pi4 model.

Running EmulationStation requires a larger than default GPU memory split. Make sure you reserve enough memory for EmulationStation by modifying the _/boot/config.txt_ configuration file or by using `raspi-config` as described in the [Memory Split](Memory-Split) page.

A reboot is required after any modifications to the video memory allocation.

## Install RetroPie

Install the needed packages for the RetroPie setup script:
```
sudo apt install git lsb-release
```
Download the latest RetroPie setup script with
```
cd
git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git
```
The script is executed with
```
cd RetroPie-Setup
chmod +x retropie_setup.sh
sudo ./retropie_setup.sh
```
The screen should look like this:

![4 0beta](https://cloud.githubusercontent.com/assets/10035308/16218285/f06f3ba8-3738-11e6-9ccc-be601172713b.png)

### Full Install

**Basic Install >> Quick Install**

This will install the core and main packages which are equivalent to what is provided with the RetroPie SD image.

Now, you have to copy your rom files into the ROMs directory. If you followed the steps above the main directory for all ROMs is ~/RetroPie/roms (or /home/pi/RetroPie/roms, which is the same here). In this directory there is a subdirectory for every emulated system, e.g., nes, snes, megadrive. Attention has to be taken for the extensions of the ROM files. All the information needed for each system is detailed in this wiki (see wiki home page or sidebar for systems)

EmulationStation can be run from the terminal by typing `emulationstation` in the terminal.

### Partial Install

**Managed Packages**

Say you don't want to bloat your system with all of RetroPie - you also have the option to only install the emulators you want.

When you select Manage Packages, you will first want to start by installing the core packages.

### Core Packages

The core components needed for RetroPie to function are:

- **RetroArch:** Frontend for the libretro api, necessary for most emulators to run.
- **EmulationStation:** Frontend for sorting and launching all of your games.
- **RetroPie Menu:** Menu in emulationstation for simpler configuration of your system.
- **Runcommand:** The runcommand launch menu that assists launching your games with proper configurations, see the related [Runcommand documentation page](Runcommand.md).

### Main / Optional / Experimental

Emulators can be installed and updated individually from the Main, Optional, and Experimental packages.

**NOTE**: If you intend to [run ROMs from a USB drive](Running-ROMs-from-a-USB-drive.md) or use an [USB drive for transferring ROMs](Transferring-Roms.md#run-your-roms-from-a-usb-stick), don't forget to install and enable the `usbromservice`, located in the Optional packages section.

### Samba Roms

If you want to use Samba shares you can set them up from the setup/tools option of the RetroPie setup script.

## Boot to EmulationStation

Follow the steps in the [FAQ](FAQ#how-do-i-boot-to-the-desktop-or-kodi).  
If you're booting to the desktop you'll want to disable the retropie splashscreen from the setup script first.

## Further Optimizations:
On Debian Jessie add `consoleblank=0` to the existing line in `/boot/cmdline.txt` (with a space before it so it's an additional parameter). This prevents the screenblanker kicking in. With it, runcommand dialog is always displayed.  
There is also a gui option in RetroPie-Setup -> Configuration / Tools -> Raspbian Tools to disable the blanker, but it doesn't work in Jessie due to a Debian bug.
