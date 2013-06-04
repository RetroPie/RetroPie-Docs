# Retropie - Arch Linux Flavor

This tutorial was written by r4 (http://www.raspberrypi.org/phpBB3/viewtopic.php?f=78&t=46013).

## Description

A guide to build the retropie setup on Arch Linux. This guide is not all encompassing. It is merely a basic setup to build a similar environment offered on the official Retropie install script.

## Sections

1. AUR tools
2. Install retroarch
   1. Configuration
3. Install Emulators
4. Install ROMs
5. Install EmulationStation
   1. Configuration
   2. Themes
   3. Scraper
      1. Configuration
      2. Downloading Boxart Images
6. Launch EmulationStation at login
7. Auto login at boot

***

## Section 1: AUR tools
    
This guide will make use of the AUR to ease the installation process. Several tools can be used, such as: packer, yaourt, cower, etc. Feel free to use the tool that you are most comfortable with.

## Section 2: Install retroarch:
    
Retroarch is found in the AUR.
        
```shell
packer -S retroarch-rbp-git
```

### Section 2.1. Configuration

Copy skeleton configuration file located at /etc/retroarch.cfg to ~/.retroarch.cfg
```shell
            cp /etc/retroarch.cfg ~/.retroarch.cfg
```

With your working joystick, configure your controller with the following command.
```shell
            retroarch-joyconfig >> ~/.retroarch.cfg
```

Note: Ensuring your joystick is working will not be covered in this guide as this falls out of scope and there are plenty of other resources to help with this.

Consult https://wiki.archlinux.org/index.php/RetroArch for more information.

## Section 3: Install Emulators

There are several emulators for retroarch. You can get a list of them by issuing the command below. Install whatever is necessary.
```shell
        packer -Ss libretro
```

Note: Some emulators may not work or may require manual building by downloading the associated tarball and issuing the command:
```shell
        makepkg -Acs --asroot
```
then...
```shell
        pacman -U /path/to/package
```

## Section 4: Install ROMs

Make directory and install ROMs to ~/roms/<system>.

Example:
```shell
        mkdir -p ~/roms/snes
        cp /path/to/roms/* ~/roms/snes/
```
    
## Section 5: Install EmulationStation:
    
EmulationStation is found in the AUR.
```shell
        packer -S emulationstation-git
```

### 5.1 Configuration

Taken from https://github.com/Aloshi/EmulationStation.

~/.emulationstation/es_systems.cfg: When first run, an example systems configuration file will be created at $HOME/.emulationstation/es_systems.cfg. This example has some comments explaining how to write the configuration file, and an example RetroArch launch command. See the "Writing an es_systems.cfg" section for more information.

~/.emulationstation/es_input.cfg: When you first start EmulationStation, you will be prompted to configure any input devices you wish to use. The process is thus:

Press a button on any device you wish to use. This includes the keyboard. If you are unable to configure a device, hold a button on the first device to continue to step 2.

Press the displayed input for each device in sequence. You will be prompted for Up, Down, Left, Right, A (Select), B (Back), Menu, Select (fast select), PageUp, and PageDown. If your controller doesn't have enough buttons to map PageUp/PageDown, it will be skipped.

Your config will be saved to ~/.emulationstation/es_input.cfg. If you wish to reconfigure, just delete this file.

NOTE: If ~/.emulationstation/es_input.cfg is present but does not contain any available joysticks or a keyboard, an emergency default keyboard mapping will be provided.

As long as ES hasn't frozen, you can always press F4 to close the application.
        
### 5.2 Themes

EmulationStation themes can be found in the AUR.
```shell
            packer -S emulationstation-themes
```

To get a list of all themes available..
```shell
            ls -l /usr/share/EmulationStation/themes/
```

Create the necessary symlinks to the themes of interest.
```shell
            ln -s /usr/share/EmulationStation/themes/snes ~/.emulationstation/
```

Consult http://aloshi.com/emulationstation for more information.

### 5.3 Scraper

The scraper tool can be found in the AUR.
```shell
            packer -S emulationstation-scraper
```

#### i) Configuration
Open your systems config file ($HOME/.emulationstation/es_systems.cfg) and append the corresponding platform ID to each system:

Example:
```shell
                   NAME=nes
                   DESCNAME=Nintendo Entertainment System
                   PATH=~/roms/nes/
                   EXTENSION=.nes
                   COMMAND=retroarch -L /path/to/core %ROM%
                   PLATFORMID=7
```
               
A list of supported platforms can be found here: https://github.com/elpendor/ES-scraper

#### ii) Downloading Boxart Images
Grab all boxart and descriptions by issuing the command below:
```shell
                    'scraper -m -w 275'
```

The -m flag will put the tool in manual mode and prompt the user on which image to download if more than one result shows. The -w flag will modify the size of an image with a width larger than 275 pixels.

Note: I highly suggest manual mode as to ensure it grabs the right images.

Consult https://github.com/elpendor/ES-scraper for more information.

## Section 6: Launch EmulationStation at login
Taken from https://wiki.archlinux.org/index.php/Start_X_at_Login and adapted.

Issue the command below to ensure EmulationStation starts at login.
```shell
        echo '[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && emulationstation' >> ~/.bash_profile
```

Note: The single quotes around the string being echoed are important!

## Section 7: Auto login at boot
Taken from https://wiki.archlinux.org/index.php/Automatic_login_to_virtual_console.

First create a new directory named getty@tty1.service.d under /etc/systemd/system:
```shell
        mkdir /etc/systemd/system/getty@tty1.service.d
```

Then create a new file named autologin.conf and add it into the directory /etc/systemd/system/getty@tty1.service.d/autologin.conf
```shell
        ---
        [Service]
        ExecStart=
        ExecStart=-/sbin/agetty --autologin <username> --noclear %I 38400 linux
```

***

Now you should have a working environment similar to what retropie offers but in Arch Linux. Enjoy! :)