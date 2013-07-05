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

## Using USB-Sticks

You also have the possibility to use a service that automatically copies ROMs from an USB stick into the correct directories. You can enable this service with the RetroPie Setup Script from within the "Setup" menu. If you are using the SD-card image download of the RetroPie Project, this copy service is already enabled. 

The service works as following: The first time you plug the USB stick into the the RPi, a ROM directory structure is generated on the USB stick, which only takes a few seconds. You can unplug the stick, put it into your PC and copy your ROMs into the corresponding directories on the USB stick. When you put the USB stick back into the RPi, the ROMs are automatically **synchronized** with the ROM folder on the RPi. When the flashing on your USB sticks ends (which indicates that no writing or reading activities are going on) you can unplug your USB stick.