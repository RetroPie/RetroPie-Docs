## Retropie on Debian/Ubuntu/Mint

A guide to build the RetroPie setup on Ubuntu (16.04 LTS or later) x86 and Debian based distros.

- [Install Ubuntu](#installation)
- [Download RetroPie](#download-retropie)
- [Install RetroPie](#install-retropie)
- [Configure RetroPie](#configure-retropie)
- [FAQ](#faq)

***

## Installation

First, install Ubuntu (16.04 LTS or later) or a related Debian based distro such as Linux Mint 18 / 19. ISO images can be used to create a bootable DVD or a USB stick.
http://www.ubuntu.com/download/desktop

To run RetroPie-Setup, you must be a member of the group root/admin.

## Download RetroPie
    
Update and upgrade the existing APT packages:

    sudo apt update && sudo apt upgrade

Install the needed packages for the RetroPie setup script:

    sudo apt install -y git dialog unzip xmlstarlet

NOTE: if you get any errors about any package not being found and you're using Ubuntu, make sure the `universe` APT repository has been added and enabled on the system by running `sudo add-apt-repository universe` and then starting again with the previous step. 

Download the latest RetroPie setup script:

    git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git

Enter the folder with the setup script:

    cd RetroPie-Setup

The script is executed with:

    sudo ./retropie_setup.sh

The screen should then appear like this:

![retropie-setup script 4-0-2](https://cloud.githubusercontent.com/assets/8606384/18487839/c4e3da42-79c4-11e6-82a8-026afa67801b.png)

## Install RetroPie

**Basic Install**

This will install the main packages which are equivalent to what is provided with the RetroPie SD image. Note that this will be the 32-bit version of RetroPie. That means that some emulators such as Daphne (Dragon's Lair) will not work out of the box on this version. That is because Daphne and a few other emulators only have a 64-bit version released for use while this install is for the 32-bit CPU family.

Now, you have to copy your rom files into the correct associated rom directories. If you followed the steps above the main directory for all roms is `~/RetroPie/roms` (or `/home/pi/RetroPie/roms`, which is the same here). In this directory there is a sub-directory for every supported emulated system, e.g., NES, SNES, Sega Megadrive, etc. 

Attention has to be taken for the extensions of the rom files. Some emulators use .zip while some use a custom file extension associated with the emulator in question. For example the Atari 2600 emulator may use .a26, .bin, and .rom.

All the information needed for each system is detailed in this wiki. See the wiki home page or sidebar for systems.

## Configure RetroPie

EmulationStation can be run from the terminal by typing `emulationstation` in the terminal.

You can go into Setup / Configuration and enable autostart as you like.

## FAQ

- [Emulationstation hangs if shutdown/restart was selected](#emulationstation-hangs-if-shutdownrestart-was-selected)
- [Cannot Install PS3 driver](#cannot-install-ps3-driver)
- [Screen blanks after some minutes](#screen-blanks-after-some-minutes)
- [Ubuntu does not autologin](#ubuntu-does-not-autologin)
- [How to setup a splashscreen](#how-to-setup-a-splashscreen)
- [My NUC or Intel Baytrail/Braswell powered device hangs](#my-nuc-or-intel-baytrailbraswell-powered-device-hangs)
- [No audio](#no-audio)
- [No HDMI audio](#no-hdmi-audio)
- [No audio in Mupen64Plus](#no-audio-in-mupen64plus)
- [XBOX 360 Controller mappings not working](#xbox-360-controller-mappings-not-working)
- [SteamOS hack to allow installation](#steamos-hack-to-allow-installation)

### Emulationstation hangs if shutdown/restart was selected

It is not possible to restart/shutdown if a sudo requests a password. To disable sudo password request add the line
 
    <user> ALL=(ALL) NOPASSWD:ALL

at the end of `/etc/sudoers`. Replace **<user\>** with the name of your current user.

### Cannot Install PS3 driver

Ubuntu has an builtin PS3 bluetooth driver. There is no need to install sixad. Make your bluetooth dongle discoverable. Connect your controller over usb. Now open "bluetooth system settings/add device". Select PS3 controller and click ok. Your controller should pair now if you press PS button.

sidenote: https://retropie.org.uk/forum/topic/2736/ubuntu-16-04-install-genuine-ps3-controller-issue

### Screen blanks after some minutes

Open Ubuntu system settings menu disable screensaver and screen lock timeouts.  

### Ubuntu does not autologin

Open Ubuntu system settings menu and select user accounts. Enable autologin for current user.    

### How to setup a splashscreen

Use Plymouth to setup a splash screen. See the [Plymouth Ubuntu wiki](https://wiki.ubuntu.com/Plymouth) or use this [simple ES theme](https://github.com/raelgc/es-logo).

### My NUC or Intel Baytrail/Braswell powered device hangs

The default kernel 4.1 of Ubuntu 15.10 tends to hang. It is a know bug:
https://bugs.freedesktop.org/show_bug.cgi?id=91629

Update to higher kernel version solves this problem:
http://sourcedigit.com/18333-how-to-install-linux-kernel-4-3-3-on-ubuntu-15-10-ubuntu-15-04/

### No audio

Open Ubuntu System Settings menu and select correct audio output device.  

### No HDMI audio

Ubuntu 16.04 uses PulseAudio 8 which has issues with HDMI if you suspend your device or change display resolutions at runtime. This problem will be solved with Ubuntu 16.10 and PulseAudio 9. You can disable PulseAudio auto output selection. Open `/etc/pulse/default.pa` and comment out the line:

    #load-module module-switch-on-port-available

https://bugs.freedesktop.org/show_bug.cgi?id=93946#c36

### No audio in Mupen64Plus

EmulationStation's use of PulseAudio will conflict with the SDL driver in Mupen64Plus, disabling sound in N64 games. If you are using lr-Mupen64plus, you will not have this conflict.

From a terminal:

    aplay -l

Example output:

    **** List of PLAYBACK Hardware Devices ****
    card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
      Subdevices: 0/1
      Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
      Subdevices: 1/1
      Subdevice #0: subdevice #0

Make a note of which card and device you use for audio. For example, for HDMI audio, consider the line `card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]`. In this case, we would want **card 0** and **device 3**.

Create the file `/etc/asound.conf` with the contents:

    ctl.!default {
            type hw
            card 0
            device 3
    }
    
    pcm.!default {
            type hw
            card 0
            device 3
    }

Make sure to change the values of **card** and **device** to the values found by running `aplay -l` above.

The SDL driver in Mupen64Plus will now use the proper audio device, but it will still conflict with PulseAudio in EmulationStation. Open `/opt/retropie/emulators/mupen64plus/bin/mupen64plus.sh` in your favorite editor. Find the following lines at the bottom of the file:

    else
        "$rootdir/emulators/mupen64plus/bin/mupen64plus" --noosd --fullscreen --rsp ${RSP_PLUGIN}.so --gfx ${VIDEO_PLUGIN}.so --audio mupen64plus-audio-sdl.so --configdir "$configdir/n64" --datadir "$configdir/n64" "$ROM"
    fi

Change them to:

    else
        mv $HOME/.config/pulse/client.conf $HOME/.config/pulse/client.conf.bak
        echo autospawn = no > $HOME/.config/pulse/client.conf
        /usr/bin/pulseaudio --kill
        "$rootdir/emulators/mupen64plus/bin/mupen64plus" --noosd --fullscreen --rsp ${RSP_PLUGIN}.so --gfx ${VIDEO_PLUGIN}.so --audio mupen64plus-audio-sdl.so --configdir "$configdir/n64" --datadir "$configdir/n64" "$ROM"
        mv $HOME/.config/pulse/client.conf.bak $HOME/.config/pulse/client.conf
        /usr/bin/pulseaudio --start
    fi

This will stop PulseAudio from running while Mupen64Plus is running, but turn it back on when you quit it.

### XBOX 360 Controller mappings not working

The X86 version of Retropie install does not have the xboxdrv installed correctly.  Please launch Retropie-Setup Manage Packages - Drivers and install xboxdrv and remap your inputs. 

### SteamOS hack to allow installation

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

This will obviously override any platform checking done by the script and is very hacky, but it will let the retropie setup continue properly until actual support exists.
