# ROMS

ROMs stand for Read Only Memory. ROMs are essentially digital versions of old game cartridges which allow you to play games on emulators (software that mimics your old gaming consoles.) There are many issues involving Copyrights laws regarding the usage of ROMs, as a result in order to preserve the integrity and longevity of the  RetroPie project, the locations of ROMs will not and cannot be added to the Wiki. That being said, in the search of your childhood - Google is your friend. You should only have ROMs of games that you own. 

## Transferring Roms

There are three main methods of transferring roms: via USB stick, via SFTP, and via Windows (Samba) shares

### USB stick
 * (ensure that your USB is formatted to FAT32)
 * first create a folder called `retropie` on your USB stick
 * plug it into the pi and wait for it to finish blinking
 * pull the USB out and plug it into a computer
 * add the roms to their respective folders (in the `retropie/roms` folder)
 * plug it back into the raspberry pi
 * wait for it to finish blinking
 * refresh emulationstation by pressing F4, or choosing quit from the start menu

see this video for reference:

<a href="https://www.youtube.com/watch?v=OYMoxvbkYD4
" target="_blank"><img src="https://i.ytimg.com/vi_webp/OYMoxvbkYD4/mqdefault.webp" 
alt="Configuration Video" width="300" height="190" border="10" /></a>

### FTP (needs an active internet connection)

* Wired (needs ethernet cable)
* Wireless (needs Pi >= 3 or wifi dongle for Pi <= 2 )

There are many FTP programs out there, for windows many people use [WinSCP](https://winscp.net/eng/download.php) for mac you can use something like [Cyberduck](https://cyberduck.io/?l=en)

![ftp](https://cloud.githubusercontent.com/assets/10035308/9144892/68994618-3d0d-11e5-8db0-2991f9068115.png)

#### Connection settings:

  * Protocol: `SFTP`
  * IP address: To find the IP address of your RetroPie, go into RetroPie options from the main menu, and select    the last option `Show IP address`.
  * Username: `pi` (default)
  * Password: `raspberry` (default)

#### Where to drop the files

Simply drop the files in the ~/RetroPie/roms/$CONSOLE folder, where $CONSOLE is the name of the target console, e.g. `snes` or `arcade`.

You can also log in as root if you wish to change more files than just the roms, but you first need to enable the root password by typing `sudo passwd root` into the terminal and choosing a new root password.

### Samba-Shares (needs an active internet connection)

- if on windows type `\\RETROPIE` into the computer folder. You can also replace RETROPIE with your Raspberry Pi's IP address

![samba](https://cloud.githubusercontent.com/assets/10035308/9141308/edee8b52-3cf4-11e5-8bf3-73f8c27f99fb.png)

- if on MAC OS X open finder, select "Go" menu and "Connect to Server". Type `smb://retropie` and hit "Connect".


### Manually copy files from USB-stick

From RetroPie version 3.0 a file manager is available, it allows you to manually transfer files between USB-stick and Raspberry Pi SD card. File manager can be run from 'RetroPie' Emulationstation menu. Quick file manager (MC) guide can be found [here](http://www.thegeekstuff.com/2008/10/midnight-commander-mc-guide-powerful-text-based-file-manager-for-unix/). Your USB-stick should be mounted in `/media/usb`. The directories for the ROM files are located in `~/RetroPie/roms/SYSTEMNAME`, where `SYSTEMNAME` is the short name of the corresponding system.