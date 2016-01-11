# Retropie - Ubuntu 15.10 x86 Flavor

## Description

A guide to build the retropie setup on Ubuntu 15.10 x86. 

Tested with an Intel NUC Kit NUC5CPYH.

Intel NUC Kit NUC5CPYH:
*2.16 GHz dual core Intel Celeron N3050
*4x USB3.0 Ports
*1x SD-Card Slot
*1x 2.5" SATA Slot
*1x HDMI 1.4a
*builtin power button

## Sections

  - [Section 1: Install Ubuntu 15.10](#section-1-install-ubuntu)
  - [Section 2: Setup Retropie](#section-2-install-retropie)
    - [Section 2.1: Download](#21-download)
    - [Section 2.2: Installation](#22-installation)
    - [Section 2.3: Configuration](#23-configuration)
  - [Section 3: FAQs](#section-3-faq)
    - [Section 3.1: Emulationstation hangs if shutdown/restart was selected](#31-hang)
    - [Section 3.2: Cannot install PS3 driver](#32-ps3)  
    - [Section 3.3: Screen blanks after some minutes](#33-configuration)
    - [Section 3.4: Ubuntu does not autologin](#34-autologin)
    - [Section 3.5: How to setup a splashscreen?](#35-splashscreen)
    - [Section 3.6: No audio](##36-noaudio)

***

## Section 1: Install Ubuntu 15.10
    
Download and install Ubuntu 15.10. Iso image can be used to create a bootable DVD or a USB stick.
http://www.ubuntu.com/download/desktop

To run RetroPie-Setup user must be a member of group root/admin.

## Section 2: Setup Retropie

### Section 2.1: Download
    
I would recommend to update and upgrade the existing APT packages with
```
    sudo apt-get update && sudo apt-get upgrade
```
After that, we install the needed packages for the RetroPie setup script:
```
    sudo apt-get install -y git dialog
```
Then we download the latest RetroPie setup script with
```
    git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git
```
The script is executed with
```
    cd RetroPie-Setup
    sudo ./retropie_setup.sh
```
The screen should look like this then:

![restropiesetupscript](https://cloud.githubusercontent.com/assets/10035308/10266202/c39fd7e0-6a10-11e5-80b1-74b642fe8441.png)

### Section 2.2: Installation

For the first installation, we choose the source-based installation, which takes 1 hour. We start the installation simply by pressing ENTER.

Now, you have to copy your rom files into the ROMs directory. If you followed the steps above the main directory for all ROMs is ~/RetroPie/roms (or /home/pi/RetroPie/roms, which is the same here). In this directory there is a subdirectory for every emulated system, e.g., nes, snes, megadrive. Attention has to be taken for the extensions of the ROM files. All the information needed for each system is detailed in this wiki (see wiki home page or sidebar for systems)

EmulationStation can be run from the terminal by typing emulationstation in the terminal

### Section 2.3: Configuration

After a source based installation themes and retropie menu are missing and autorun is not setup. Enter RetroPie-Setup again and select option `3 Setup / Configuration (to be used post install`. Select a emulationstation theme, install retropie menu and enable autostart as you like.

## Section 3: FAQs

### Section 3.1: Emulationstation hangs if shutdown/restart was selected

It is not possible to restart/shutdown if an sudo requests an password. To disable sudo password request add the line `$user ALL=(ALL) NOPASSWD:ALL` at the end of `/etc/sudoers`. Replace `$user`with the name of your current user.

### Section 3.2: Cannot install PS3 driver

Ubuntu has an builtin PS3 bluetooth driver. Make your bluetooth dongle discoverable. Connect your controller over usb and allow it to connect. There is no need to install sixad. 

### Section 3.3: Screen blanks after some minutes

Open Ubuntu system settings menu disable screensaver and screen lock timeouts.  

### Section 3.4: Ubuntu does not autologin

Open Ubuntu system settings menu and select user accounts. Enable autologin for current user.    

### Section 3.5: How to setup a splashscreen?

Use Plymouth to setup a splash screen:
https://wiki.ubuntu.com/Plymouth

### Section 3.6: No audio

Open Ubuntu system settings menu and select right audio output device.  