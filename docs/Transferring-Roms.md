# ROMS

ROM stands for *Read Only Memory*. In a RetroPie context, ROMs are digital copies of games which can be run on emulators (software that mimics your old gaming consoles). There are many issues involving copyright laws regarding the usage of ROMs, so in order to preserve the integrity and longevity of the RetroPie project, the download locations of ROMs will not and cannot be added to the Wiki. That being said, in the search of your childhood - Google is your friend.

## Transferring Roms

There are three main methods of transferring roms: via USB stick, via SFTP, and via Windows (Samba) shares.

### USB stick

1. Ensure that the USB stick is formatted to FAT32 or exFAT, and that the SD card has enough free space to hold all ROMs
2. Create a folder called `retropie` on the USB stick
3. Plug it into the RetroPie system. If the USB stick has an activity light, wait for it to finish blinking, else wait a few minutes
4. Remove the USB stick and plug it into the computer containing the ROMs
5. Add the ROMs to the USB stick inside their respective folders within the `retropie/roms/$CONSOLE` folder, where $CONSOLE is the name of the target console, e.g. `snes` or `arcade`.
6. Plug it back into the RetroPie system. If the USB stick has an activity light, wait for it to finish blinking, else wait (with many GBs of ROMs, wait several hours)
8. Remove the USB stick. The ROMs have now been transferred from the USB to the RetroPie system's SD card
9. Refresh the game listing in EmulationStation by pressing F4, or press **Start** on your controller > **Quit** > **Restart EmulationStation**
10. The transferred games should now be visible within EmulationStation. If any are missing, return to step 6

### SFTP

SFTP (Secure File Transfer Protocol) is a network protocol that allows you to securely transfer files over the internet or locally on the same network when both your PC and RetroPie system are connected to the same router via Ethernet or Wifi. 

- Wired (needs ethernet cable)
- Wireless (Raspberry Pi Zero W, 3 and 4 models have onboard Wifi, so Pi 1 and 2 will need a dongle)

To enable SSH from within RetroPie:

1. Within the 'RetroPie' EmulationStation options menu, select **raspi-config**
2. Select **Interface Options**
3. Select **SSH**
4. Choose **Yes**
5. Select **Ok**
6. Choose **Finish**

There are many SFTP programs out there:

- Windows: 
  - [WinSCP](https://winscp.net/eng/download.php) - For easy drag & drop file transfer
  - [MobaXTerm](https://mobaxterm.mobatek.net/) - Feature-rich command line access and drag & drop file transfer
- Mac: [Cyberduck](https://cyberduck.io/?l=en)

![ftp](https://cloud.githubusercontent.com/assets/10035308/9144892/68994618-3d0d-11e5-8db0-2991f9068115.png)

**Connection settings** 

- Protocol: `SFTP`
- IP address/Host Name: To find the IP address of your RetroPie, go into the 'RetroPie' EmulationStation options menu and select **Show IP**. You can also find this information from the terminal on RetroPie in the bash info or with the command `ifconfig`
- Username: `pi` (default)
- Password: `raspberry` (default)

**Where to drop the files**

Simply drop the files in the `~/RetroPie/roms/$CONSOLE` folder, where $CONSOLE is the name of the target console, e.g. `snes` or `arcade`.

You can also log in as root if you wish to change more files than just the roms, but you first need to enable the root password by typing `sudo passwd root` into the terminal and choosing a new root password.

For more information, check the [Raspberry Pi SSH documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/).

### Samba-Shares

[Samba](https://www.samba.org/samba/what_is_samba.html) is a software suite that allows you to access file systems over the network. Naturally both your PC and Pi will need to be connected to the same network via Ethernet or Wifi in order to successfully transfer your files. 

- On Windows, type `\\RETROPIE` into the computer folder. You can also replace RETROPIE with your Raspberry Pi's IP address

![samba](https://cloud.githubusercontent.com/assets/10035308/9141308/edee8b52-3cf4-11e5-8bf3-73f8c27f99fb.png)

- On Mac OS X/macOS, open Finder, select "Go" menu and "Connect to Server". Type `smb://retropie` and hit "Connect".

### Manually copy files from USB-stick

RetroPie version 3.0+ contains a file manager. It allows you to manually transfer files between USB-stick and Raspberry Pi SD card. The file manager can be run from 'RetroPie' EmulationStation menu > **File Manager**. A Midnight Commander file manager guide can be found [here](http://www.thegeekstuff.com/2008/10/midnight-commander-mc-guide-powerful-text-based-file-manager-for-unix/). Your USB-stick should be mounted in `/media/usb`. The directories for the ROM files are located in `retropie/roms/$CONSOLE` folder, where $CONSOLE is the name of the target console, e.g. `snes` or `arcade`.

## Alternative Methods of Accessing Games

- [Running ROMs From a USB](Running-ROMs-from-a-USB-drive)
- [Running ROMs From a Network Share](Running-ROMs-from-a-Network-Share)
