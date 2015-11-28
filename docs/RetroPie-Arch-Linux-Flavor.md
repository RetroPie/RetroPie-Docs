# Retropie - Arch Linux Flavor

This tutorial was written by r4 (http://www.raspberrypi.org/phpBB3/viewtopic.php?f=78&t=46013) and is now adapted to work with AUR4 and [apacman](https://aur.archlinux.org/packages/apacman/) script.

## Description

A guide to build the retropie setup on Arch Linux. This guide is not all encompassing. It is merely a basic setup to build a similar environment offered on the official Retropie install script.

## Sections

  - [Section 1: AUR tools](#section-1-aur-tools)
  - [Section 2: Install retroarch:](#section-2-install-retroarch)
    - [Section 2.1. Configuration](#section-21-configuration)
  - [Section 3: Install Emulators](#section-3-install-emulators)
  - [Section 4: Install ROMs](#section-4-install-roms)
  - [Section 5: Install EmulationStation:](#section-5-install-emulationstation)
    - [5.1 Configuration](#51-configuration)
    - [5.2 Themes](#52-themes)
    - [5.3 Scraper](#53-scraper)
  - [Section 6: Launch EmulationStation at login](#section-6-launch-emulationstation-at-login)
  - [Section 7: Auto login at boot](#section-7-auto-login-at-boot)

***

## Section 1: AUR tools
    
Install [apacman](https://aur.archlinux.org/packages/apacman/)
```shell
wget https://aur.archlinux.org/cgit/aur.git/snapshot/apacman.tar.gz
tar xzf apacman
cd apacman
makepkg -s --asroot
pacman -U apacman[Press TAB key to autocomplete the filename then press ENTER to install]
```

## Section 2: Install retroarch:
    
First we need a special build of sdl2 to make Retroarch and EmulationStation work the best with RPi/RPi2. Then next we can proceed on installing retroarch.
        
```shell
apacman -S sdl2-rbp-git
apacman -S retroarch-rbp-git
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
apacman -Ss libretro
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
apacman -S emulationstation-git
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
apacman -S emulationstation-themes
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

The ES-Scraper project is no more compatible with Emulation Station since `es_systems.cfg` now is an XML file.

## Section 6: Launch EmulationStation at login

Issue the command below to ensure EmulationStation starts at login.
```shell
echo 'emulationstation' >> ~/.bash_profile
```
or if you're using ZSH
```shell
echo 'emulationstation' >> ~/.zlogin
```

Note: The single quotes around the string being echoed are important!

## Section 7: Auto login at boot
Taken from https://wiki.archlinux.org/index.php/Automatic_login_to_virtual_console.

```shell
systemctl edit getty@tty1
```
and then write/paste this inside
```shell
[Service]
Type=simple
ExecStart=
ExecStart=-/sbin/agetty --autologin <username> --noclear %I 38400 linux
```
save the file and reboot.
***

Now you should have a working environment similar to what retropie offers but in Arch Linux. Enjoy! :)