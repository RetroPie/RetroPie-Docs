ROM stands for *Read Only Memory*. In a RetroPie context, ROMs are digital copies of games which can be run on emulators (software that mimics your old gaming consoles). There are many issues involving copyright laws regarding the usage of ROMs, so in order to preserve the integrity and longevity of the RetroPie project, the download locations of ROMs will not and cannot be added to the Wiki. That being said, in the search of your childhood - Google is your friend.

## Transferring ROMs

There are three main methods of transferring ROMs: via USB stick, via SFTP, and via Windows (Samba) shares.

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

SFTP/SSH connection instructions are available on the [SSH page](SSH.md). Once you've enabled SSH and connected to your chosen client, you can simply drop the files in the `~/RetroPie/roms/$CONSOLE` folder, where $CONSOLE is the name of the target console, e.g. `snes` or `arcade`.

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
