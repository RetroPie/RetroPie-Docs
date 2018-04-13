# ROMS

ROMs stand for Read Only Memory. ROMs are essentially digital versions of old game cartridges which allow you to play games on emulators (software that mimics your old gaming consoles.) There are many issues involving Copyrights laws regarding the usage of ROMs, as a result in order to preserve the integrity and longevity of the RetroPie project, the locations of ROMs will not and cannot be added to the Wiki. That being said, in the search of your childhood - Google is your friend. You should only have ROMs of games that you own.

## Transferring Roms

There are three main methods of transferring roms: via USB stick, via SFTP, and via Windows (Samba) shares

### USB stick

1. (ensure that your USB is formatted to FAT32)
2. first create a folder called `retropie` on your USB stick
3. plug it into the pi and wait for it to finish blinking
4. pull the USB out and plug it into a computer
5. add the roms to their respective folders (in the `retropie/roms` folder)
6. plug it back into the raspberry pi
7. wait for it to finish blinking
8. you can now remove the USB stick.
9. refresh emulationstation by pressing F4, or choosing quit from the start menu

### SFTP

[SFTP](https://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol) or SSH File Transfer Protocol also called Secure File Transfer Protocol is a network protocol that allows you to securely transfer files over a network. Naturally both your PC and Pi will need to be connected to the same network via Ethernet or Wifi in order to successfully transfer your files. 

- Wired (needs ethernet cable)
- Wireless (needs Pi >= 3 or wifi dongle for Pi <= 2 )

To use SFTP, you must first [enable SSH](https://www.raspberrypi.org/documentation/remote-access/ssh/). As of the November 2016 release, Raspbian has the SSH server disabled by default.

To enable SSH from within RetroPie:

1. Navigate to the RetroPie configuration area.
1. Select `raspi-config`
1. Select `Interfacing Options`
1. Select `SSH`
1. Choose `Yes`
1. Select `Ok`
1. Choose `Finish`

There are many SFTP programs out there:

- Windows: [WinSCP](https://winscp.net/eng/download.php)
- Mac: [Cyberduck](https://cyberduck.io/?l=en)

![ftp](https://cloud.githubusercontent.com/assets/10035308/9144892/68994618-3d0d-11e5-8db0-2991f9068115.png)

**Connection settings:** 

- Protocol: `SFTP`
- IP address: To find the IP address of your RetroPie, go into RetroPie options from the main menu, and select the last option `Show IP address`. You can also find this information from the terminal on retropie in the bash info or with the command `ifconfig`
- Username: `pi` (default)
- Password: `raspberry` (default)

**Where to drop the files***

Simply drop the files in the ~/RetroPie/roms/$CONSOLE folder, where $CONSOLE is the name of the target console, e.g. `snes` or `arcade`.

You can also log in as root if you wish to change more files than just the roms, but you first need to enable the root password by typing `sudo passwd root` into the terminal and choosing a new root password.

### Samba-Shares

[Samba](https://www.samba.org/samba/what_is_samba.html) is a software suite that allows you to access file systems over the network. Naturally both your PC and Pi will need to be connected to the same network via Ethernet or Wifi in order to successfully transfer your files. 

- if on windows type `\\RETROPIE` into the computer folder. You can also replace RETROPIE with your Raspberry Pi's IP address

![samba](https://cloud.githubusercontent.com/assets/10035308/9141308/edee8b52-3cf4-11e5-8bf3-73f8c27f99fb.png)

- if on MAC OS X open finder, select "Go" menu and "Connect to Server". Type `smb://retropie` and hit "Connect".


### Manually copy files from USB-stick

From RetroPie version 3.0 a file manager is available, it allows you to manually transfer files between USB-stick and Raspberry Pi SD card. File manager can be run from 'RetroPie' Emulationstation menu. Quick file manager (MC) guide can be found [here](http://www.thegeekstuff.com/2008/10/midnight-commander-mc-guide-powerful-text-based-file-manager-for-unix/). Your USB-stick should be mounted in `/media/usb`. The directories for the ROM files are located in `~/RetroPie/roms/SYSTEMNAME`, where `SYSTEMNAME` is the short name of the corresponding system.

## Alternative Methods of Accessing Games

### [Running ROMs From a USB](Running-ROMs-from-a-USB-drive)
### [Running ROMs From a Network Share](Running-ROMs-from-a-Network-Share)
