# ROMS

ROMs stand for Read Only Memory. ROMs are essentially digital versions of old game cartridges which allow you to play games on emulators (software that mimics your old gaming consoles.) There are many issues involving Copyrights laws regarding the usage of ROMs, as a result in order to preserve the integrity and longevity of the  RetroPie project, the locations of ROMs will not and cannot be added to the Wiki. That being said, in the search of your childhood- Google is your friend.

If you hate reading: watch this video instead, otherwise read on! 

<a href="http://www.dailymotion.com/video/x2i0nuk_retropie-copying-roms-to-your-raspberry-pi_videogames" target="_blank"><img src="http://petrockblog.files.wordpress.com/2012/10/retropieprojectlogofinish.jpg" 
alt="N64 Configuration Video" width="150" height="110" border="10" /></a> 



## Copying via SSH connection

One way for copying ROMs on the SD card is via an [SSH connection](http://en.wikipedia.org/wiki/Secure_Shell). It is enabled per default in Raspbian and allows, for example, to remotely log into the RPi with a Terminal or to copy files between two computers.

In order to connect to your Raspberry, you need to know the IP address of it. To get this you can either have a look at your router/switch logs, or you can exit Emulation Station on the RPi and type 

```shell
ifconfig
```
The IP address of the RPi is the one behind "eth0, inet addr". The default user name and password for the Raspbian distribution is "pi" and "raspberry", respectively.

To copy files, you can use the command line tool "scp" or a GUI like [WinSCP](http://winscp.net/eng/index.php) (for Windows) or [Cyberduck](http://cyberduck.ch/) (for MacOS).

The **directories for the ROM files** are located in ~/RetroPie/roms/SYSTEMNAME, where SYSTEMNAME is the short name of the corresponding system.

You can find additional information about remotely accessing the RPi in the [eLinux wiki](http://elinux.org/RPi_Remote_Access).

## Copying via Samba Shares

The RetroPie Setup allows to install and configure Samba shares for each installed emulator. You can access this function in the RetroPie Setup Script in the menu "Setup". After the installation it is possible to copy ROMs to the Raspberry by using the corresponding Samba shares.

easiest way to access is to go into "computer" folder on windows and in the top type:

```shell
\\your-pi-ip-address
```

## Using USB-Stick

### Auto copy files from USB-stick

You also have the possibility to use a service that automatically copies ROMs from an USB stick into the correct directories. You can enable this service with the RetroPie Setup Script from within the "Setup" menu. If you are using the SD-card image download of the RetroPie Project, this copy service is already enabled. 

The service works as following: The first time you plug the USB stick into the the RPi, a ROM directory structure is generated on the USB stick, which only takes a few seconds. You can unplug the stick, put it into your PC and copy your ROMs into the corresponding directories on the USB stick. When you put the USB stick back into the RPi, the ROMs are automatically **synchronized** with the ROM folder on the RPi. When the flashing on your USB sticks ends (which indicates that no writing or reading activities are going on) you can unplug your USB stick.

**Starting with RetroPie 3.0 you first need to create a folder called `retropie` on your USB stick and then follow the above steps.**

### Manually copy files from USB-stick

From RetroPie version 3.0 a file manager is available, it allows you to manually transfer files between USB-stick and Raspberry Pi SD card. File manager can be run from 'RetroPie' Emulationstation menu. Quick file manager (MC) guide can be found [here](http://www.thegeekstuff.com/2008/10/midnight-commander-mc-guide-powerful-text-based-file-manager-for-unix/). Your USB-stick should be mounted in /media/usb. The directories for the ROM files are located in ~/RetroPie/roms/SYSTEMNAME, where SYSTEMNAME is the short name of the corresponding system.