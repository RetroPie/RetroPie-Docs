## Install Raspbian:

You can download a fresh Raspbian Image from [here](http://www.raspberrypi.org/downloads). The Raspbian image can be installed the same way as the RetroPie image as described [here](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation)). 

Raspbian now automatically expands the filesystem so that step is no longer necessary.

You can check your free disk space with
```
    df -h
```

/dev/root is your main partition. Then, I would recommend to update and upgrade the existing APT packages with
```
    sudo apt-get update && sudo apt-get upgrade
```
After that, we install the needed packages for the RetroPie setup script:
```
    sudo apt-get install git lsb-release
```
Then we download the latest RetroPie setup script with
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
The screen should look like this then:

![4 0beta](https://cloud.githubusercontent.com/assets/10035308/16218285/f06f3ba8-3738-11e6-9ccc-be601172713b.png)

## Verify Locale Settings
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

If any of the above configuration lines are unset (particularly LANG, LANGUAGE, and LC_ALL), you should set them before installing RetroPie. The easiest way to set each item is to use the `update-locale` command, such as `$ sudo update-locale LC_ALL="en_US.UTF-8"`.

Users can also set the local through the `raspi-config` tool.

## Full Install

**Manage Packages >> Quick Install**

This will install the core and main packages which are equivalent to what is provided with the RetroPie SD image.

Now, you have to copy your rom files into the ROMs directory. If you followed the steps above the main directory for all ROMs is ~/RetroPie/roms (or /home/pi/RetroPie/roms, which is the same here). In this directory there is a subdirectory for every emulated system, e.g., nes, snes, megadrive. Attention has to be taken for the extensions of the ROM files. All the information needed for each system is detailed in this wiki (see wiki home page or sidebar for systems)

EmulationStation can be run from the terminal by typing `emulationstation` in the terminal 

## Partial Install

Say you don't want to bloat your system with all of RetroPie- you also have the option to only install the emulators you want. 

You will want to start by installing the core packages.

### Core Packages:

The core components needed for RetroPie to function are:
- **RetroArch:** Frontend for the libretro api, necessary for most emulators to run.
- **EmulationStation:** Frontend for sorting and launching all of your games.
- **RetroPie Menu:** Menu in emulationstation for simpler configuration of your system.
- **Runcommand:** The runcommand launch menu that assists launching your games with proper configurations see related wiki page [HERE](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand).

### Main / Optional / Experimental

Emulators can be installed and updated individually from the Main, Optional, and Experimental packages.

### Samba Roms

If you want to use samba shares you can set them up from the setup/tools option of the retropie setup script.

## Boot to emulationstation

Follow the steps here: https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-do-i-boot-to-the-desktop-or-kodi

## Further Optimizations:
On Debian Jessie add `consoleblank=0` to the existing line in `/boot/cmdline.txt` (with a space before it so it's an additional parameter). This prevents the screenblanker kicking in. With it, runcommand dialog is always displayed.  
There is also a gui option in RetroPie-Setup -> Configuration / Tools -> Raspbian Tools to disable the blanker, but it doesn't work in Jessie due to a Debian bug.