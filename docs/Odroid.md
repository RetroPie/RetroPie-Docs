# Odroid C1/C1+

This is a guide on how to build RetroPie on the Odroid C1/C1+. This is assuming you are starting with a prebuilt image of Ubuntu from HardKernel's Website:

## Download Ubuntu Image for Odroid:

http://odroid.com/dokuwiki/doku.php?id=en:c1_release_linux_ubuntu

Direct Link [Here](http://odroid.in/ubuntu_14.04lts/ubuntu-14.04.3lts-lubuntu-odroid-c1-20151020.img.xz)

Extract the .xz file with a program like [7zip](http://www.7-zip.org/download.html)

Write the .img file to your SD card or EMMC module with something like [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/)

Unlike the RetroPie SD Image, the Odroid image will autoexpand the filesystem so there is no need for that step here.

## Install RetroPie:

Optional preliminary steps:

```
sudo apt-get update && sudo apt-get upgrade

sudo apt-get install -y git dialog

```

Installing the RetroPie Setup Script:

```
cd
wget git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git
```

Run the Setup Script:

```
cd RetroPie-Setup
sudo ./retropie_setup.sh
```

**Note** if you have issues while compiling modules and it freezes up on you, then you need to tell it to only compile with one core by running the setup script with this:

```
sudo MAKEFLAGS="-j1" ./retropie_setup.sh

```

## Installing Modules

All modules can be installed from the RetroPie Setup Script. First and foremost the two main packages you need in order for the majority of your system to run are RetroArch and EmulationStation:

#### Installing EmulationStation:

- Option 5: Install EmulationStation

#### Installing RetroArch:

- Option 5: Install RetroArch

## Installing Emulators:

- Option 5: Choose your emulators

## Advanced Configuration

#### AutoStart EmulationStation

- Option 3: Autostart EmulationStation 

#### Rom Transfer

- Option 3: Enable USBRomService

#### Samba Shares

- Option 3: Enable Samba Shares

