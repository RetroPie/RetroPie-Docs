## Install Raspbian:

You can download a fresh Raspbian Image from [here](http://www.raspberrypi.org/downloads). The Raspbian image can be installed the same way as the RetroPie image as described [here](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation)). 

Once your Image has been installed you need to expand your file system.


## Expand File System

This allows your SD card to use all its storage rather than the small partition it was released with.

From the terminal type
```
sudo raspi-config
```
(as a first step you can optionally change the boot options in option 3 to console autologin so you don't have to keep going through the desktop software to get to the terminal.)

![raspi-config](https://cloud.githubusercontent.com/assets/10035308/9140867/856bb85a-3cf1-11e5-8697-04f60ecf8563.png)

You will get this message:

![raspi-config2](https://cloud.githubusercontent.com/assets/10035308/9140889/ad8879c2-3cf1-11e5-8d77-7c81af7dba16.png)

Select finish

![raspi-config3](https://cloud.githubusercontent.com/assets/10035308/9140900/dcfdf556-3cf1-11e5-978c-e5d620ab98fc.png)

And then reboot your raspberry pi

![raspi-config4](https://cloud.githubusercontent.com/assets/10035308/9140912/fc047e3e-3cf1-11e5-9463-f574e0efc38a.png)

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
    sudo apt-get install -y git dialog
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

![restropiesetupscript](https://cloud.githubusercontent.com/assets/10035308/10266202/c39fd7e0-6a10-11e5-80b1-74b642fe8441.png)

## Full Install

For the first installation, we choose the binaries-based installation, which takes 15-30 minutes. We start the installation simply by pressing ENTER.

When everything is finished you will see this screen:

![Tutorial_Installation2](https://github.com/petrockblog/RetroPie-Setup/raw/master/wiki/images/tutorial_installation2.png)

Now, you have to copy your rom files into the ROMs directory. If you followed the steps above the main directory for all ROMs is ~/RetroPie/roms (or /home/pi/RetroPie/roms, which is the same here). In this directory there is a subdirectory for every emulated system, e.g., nes, snes, megadrive. Attention has to be taken for the extensions of the ROM files. All the information needed for each system is detailed in this wiki (see wiki home page or sidebar for systems)

EmulationStation can be run from the terminal by typing `emulationstation` in the terminal 

## Partial Install

Say you don't want to bloat your system with all of RetroPie- you also have the option to only install the emulators you want.

### EmulationStation

First you you need to install EmulationStation from the retopie setup script from option 5. It will be near the bottom of the list

The you can auto-start emulationstation from option 3 of the retropie setup script (if you want your system to boot into emulationstation)

You'll then need to install a theme which can be installed from option 3 of the retropie setup script (carbon will work best as the default theme)

### RetroArch

You need to install Retroarch if you want most of the emulators to work. It can be installed from option 5 of the retropie setup script

### Emulators

You can install the emulators that you want from option 5 of the retropie setup script, you can also install other emulators from the experimental menu.

### Samba Roms

If you want to use samba shares you can set them up from option 3 of the retropie setup script. By default the username will be raspberrypi but that can also be changed from the raspi-config menu .