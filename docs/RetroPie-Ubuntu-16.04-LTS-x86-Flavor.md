# Retropie - Ubuntu 16.04 LTS x86 Flavor

## Description

A guide to build the RetroPie setup on Ubuntu 16.04 LTS x86 and related distros.

Tested with an Intel NUC Kit NUC5CPYH

## Sections

  - [Section 1: Install Ubuntu 16.04 LTS](#section-1-install-ubuntu)
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
    - [Section 3.7: My NUC or Intel Baytrail/Braswell powered device hangs (Ubuntu 15.10)](##37-hang)
    - [Section 3.8: No HDMI audio (Ubuntu 16.04)](##38-nohdmiaudio)
    - [Section 3.9: Xbox360 Controller mappings not working correctly](##39-xbox360)
    - [Section 3.10: How do I map controls to Dolphin](##310-dolphincontrols)
    - [Section 3.11: Start+Select does not exit Dolphin](##311-dolphinexit)
    - [Section 3.12: SteamOS hack to allow installation](##312-steamosinstall)

***

## Section 1: Install Ubuntu 16.04 LTS or a related Debian based distro such as Linux Mint 17 and 18.
    
Download and install Ubuntu 16.04 LTS. ISO image can be used to create a bootable DVD or a USB stick.
http://www.ubuntu.com/download/desktop

To run RetroPie-Setup user must be a member of group root/admin.

## Section 2: Setup RetroPie

### Section 2.1: Download
    
Update and upgrade the existing APT packages:
```
    sudo apt-get update && sudo apt-get upgrade
```
Install the needed packages for the RetroPie setup script:
```
    sudo apt-get install -y git dialog
```
Download the latest RetroPie setup script:
```
    git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git
```
Enter the folder with the setup script:
```
    cd RetroPie-Setup
```
The script is executed with:
```
    sudo ./retropie_setup.sh
```
The screen should look like/similar this at this point:

![retropie-setup script 4-0-2](https://cloud.githubusercontent.com/assets/8606384/18487839/c4e3da42-79c4-11e6-82a8-026afa67801b.png)

### Section 2.2: Installation

**Basic Install**

This will install the main packages which are equivalent to what is provided with the RetroPie SD image. Note that this will be the 32 bit version of RetroPie. That means that some emulators such as Daphne (Dragon's Lair) will not work out of the box on this version. That is because Daphne and a few other emulators only have a 64 bit version released for use while this install is for the 32 bit cpu family.

Now, you have to copy your rom files into the correct associated rom directories. If you followed the steps above the main directory for all roms is ~/RetroPie/roms (or /home/pi/RetroPie/roms, which is the same here). In this directory there is a sub-directory for every supported emulated system, e.g., NES, SNES, Sega Megadrive, etc. 

Attention has to be taken for the extensions of the rom files. Some emulators use .zip while some use a custom file extension associated with the emulator in question. For example the Atari 2600 emulator may use .a26, .bin, and .rom.

All the information needed for each system is detailed in this wiki. See the wiki home page or sidebar for systems.

### Section 2.3: Configuration

EmulationStation can be run from the terminal by typing `emulationstation` in the terminal.

You can go into Setup / Configuration and enable autostart as you like.

## Section 3: FAQs

### Section 3.1: Emulationstation hangs if shutdown/restart was selected

It is not possible to restart/shutdown if a sudo requests an password. To disable sudo password request add the line `$user ALL=(ALL) NOPASSWD:ALL` at the end of `/etc/sudoers`. Replace `$user`with the name of your current user.

### Section 3.2: Cannot install PS3 driver

Ubuntu has an builtin PS3 bluetooth driver. There is no need to install sixad. Make your bluetooth dongle discoverable. Connect your controller over usb. Now open "bluetooth system settings/add device". Select PS3 controller and click ok. Your controller should pair now if you press PS button.

sidenote: https://retropie.org.uk/forum/topic/2736/ubuntu-16-04-install-genuine-ps3-controller-issue

### Section 3.3: Screen blanks after some minutes

Open Ubuntu system settings menu disable screensaver and screen lock timeouts.  

### Section 3.4: Ubuntu does not autologin

Open Ubuntu system settings menu and select user accounts. Enable autologin for current user.    

### Section 3.5: How to setup a splashscreen?

Use Plymouth to setup a splash screen:
https://wiki.ubuntu.com/Plymouth

### Section 3.6: No audio

Open Ubuntu system settings menu and select right audio output device.  

### Section 3.7: My NUC or Intel Baytrail/Braswell powered device hangs (Ubuntu 15.10)

The default kernel 4.1 of Ubuntu 15.10 tends to hang. It is a know bug:
https://bugs.freedesktop.org/show_bug.cgi?id=91629

Update to higher kernel version solves this problem:
http://sourcedigit.com/18333-how-to-install-linux-kernel-4-3-3-on-ubuntu-15-10-ubuntu-15-04/

### Section 3.8: No HDMI audio (Ubuntu 16.04)

Ubuntu 16.04 uses Pulseaudio 8 which has issues with HDMI if you suspend your device or change display resolutions at runtime. This problem will be solved with Ubuntu 16.10 and Pulseaudio 9. Mupen64plus runs a fullscreen resolution of 640x480. If your default resolution differs there will be a resolution switch and Pulseaudio will set another audio device. You can disable Pulseaudio auto output selection. Open /etc/pulse/default.pa and comment out the line:
```
#load-module module-switch-on-port-available
```
https://bugs.freedesktop.org/show_bug.cgi?id=93946#c36

### Section 3.9: Xbox360 Controller mappings not working correctly

The X86 version of Retropie install does nto have the xboxdrv installed correctly.  Please launch Retropie-Setup Manage Packacges - Drivers and install xbox drv and remap your inputs. 


### Section 3.10: How do I map controls to Dolphin

Dolphin controls must currently be mapped via the GUI. You will need to drop down into terminal mode press F4 on your keyboard if you are currently in emulation station, hit the unity button and search for terminal.  Click to launch. 
Change to the Dolphin directory
```
cd /opt/retropie/emulators/bin/dolphin-emu 
Launch dolphin emu
./dolphin-emu 
```
From there there graphical client will launch and you can bind your controller in the Dolphin Interface as well as change settings.

### Section 3.11: Start+Select does not exit Dolphin

Dolphin is not a libretro emulator. Currently exit for Dolphin is hard mapped to Alt + F4 
You can manually exit via your keyboard, and come back to emulation station.
To map a button on your controller to exit Dolphin you will need to launch via the gui method above. 
Once in the menu navigate to Hotkey Behavior.  
Switch the device indicator to your controller
select the exit function and map a button like select to this function.
You will also need to configure in the graphics window to always force window on top and to hide mouse/cursor

Now enter back into emulationstation mode and launch a dolphin game from the gamecube menu
press x when the game is starting
Select Dolphin-Gui instead of dolphin as the runcommand default emulator.
Launch game
You will now be able to exit back to emulationstation with that button you mapped. 

### Section 3.12: SteamOS hack to allow installation
While SteamOS is not based on Ubuntu 16.04 it is based on Debian 8 which is supported.
Currently you can install it and it will set everything up properly. EmulationStation has issues launching
roms just like through a manual installation. However the samba share setup and all other parts of RetroPie
appear to function normally.

To start follow the same instructions of doing a git clone of the RetroPie repo. Then you have to edit

      RetroPie-Setup/scriptmodules/system.sh

In the get_os_version() function the work-around is to change:

            error="Unsupported OS"
            ;;
    esac

To

            __os_debian_ver="8"
            ;;
    esac

This will obviously override any platform checking done by the script and is very hacky, but it will let the retropie setup continue properly until actual support exists