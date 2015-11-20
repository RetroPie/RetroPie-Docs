# Updating RetroPie

The conventional way to update RetroPie is through the setup script. 

The setup script can be accessed from the **RetroPie menu** in emulationstation. 

It can also be accessed from the terminal with 
```
cd RetroPie-Setup
sudo ./retropie_setup.sh
```

**Before making any major updates it is important to make backups just in case (see backup options below).**

## Using the RetroPie Setup Script

![restropiesetupscript](https://cloud.githubusercontent.com/assets/10035308/10266202/c39fd7e0-6a10-11e5-80b1-74b642fe8441.png)

- **The very first thing** you'll want to do before you do anything is select **Update RetroPie-Setup Script** as this will update the latest changes to the setup script.

- **Binary Based Installation:** If you wish to do a full update of RetroPie, this is the option you should choose. a backup is highly recommended before choosing this option

- **Source-based installation:** very rarely if ever should you use this as it takes more than 24 hours to run and likely will end up with some broken non-working emulators due to unfixed bugs

- **Setup / Configuration:** this is where you can update configurations, install new themes, controller drivers, etc. many of these options are also on the retropie menu in emulationstation

- **Experimental Packages:** these are emulators and options that may be potentially unstable but are worth checking out if you are feeling ambitious

- **Install Individual Emulators from Binary or Source:** This is where you will update individual emulators- you will almost always update from binary as they are more frequently updated, have less bugs, and are much quicker to install. There will be rare occasions where you may need to update from source but when in doubt just choose binary and you should be fine. 

#### Latest SD image

If you are worried about conflicts during an update you can always just start with the latest fresh sd image and just copy all your files back over onto that instead of updating from an older image.

## Making a Backup (Option 1)

You can create an sd image of your current sd card with [win32diskimager](http://sourceforge.net/projects/win32diskimager/files/Archive/) (if you're on windows)

- Plug your sd card into your laptop (you will need a sd card reader for this)
- Open win32diskimager as an administrator (you can right click on it to run as an administrator)

![runasadministrator](https://cloud.githubusercontent.com/assets/10035308/10266141/babb3420-6a0c-11e5-9f20-c26297b9fbbf.png)

- make sure you have the correct drive letter for your SD card! 
- define the file path that you want to save your .img backup as

![win32diskimager](https://cloud.githubusercontent.com/assets/10035308/10266156/79baadf6-6a0d-11e5-9c98-62211328c68a.png)

- Click **read** to create your backup. (after you've backed this image up if you screw something up later and want to start from this image you can just click write and it will write this sd image back to your sd card.)
- note if you have a 64GB sd card it will create a 64GB backup file even if you don't have it completely filled up. If you don't want a file that large see the next option.   

## Making a Backup (Option 2)

if you don't want to create a sd image you can just back up your bios, roms, and configuration files from the samba shares

![configs](https://cloud.githubusercontent.com/assets/10035308/9141308/edee8b52-3cf4-11e5-8bf3-73f8c27f99fb.png)

## Making a Backup (OS X)

Open a terminal window and type `diskutil list`. A list of all hard disks and partitions shows up. Find a partition with the name `boot`. The related /dev/disk* is your retropie sd card. Type `sudo dd if=/dev/disk* of=backup.img bs=1m` to write a disk image to your home directory.

#### Writing the RetroPie SD image with DD on Linux

`lsblk` to list your drives (in the following example it is sdb)

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 698.7G  0 disk 
├─sda1   8:1    0   100M  0 part 
├─sda2   8:2    0 585.9G  0 part /media/seamus_linux/3456B9D456B996D8
├─sda3   8:3    0     1K  0 part 
├─sda5   8:5    0 108.8G  0 part /
└─sda6   8:6    0   3.9G  0 part [SWAP]
sdb      8:16   1   7.4G  0 disk 
├─sdb1   8:17   1    57M  0 part /media/seamus_linux/boot
└─sdb2   8:18   1   7.3G  0 part /media/seamus_linux/retropie
sr0     11:0    1  1024M  0 rom  
```
an example of the command you would use to write the image is: `sudo dd bs=1M if=/home/seamus_linux/Downloads/retropie-v3.2.1-rpi2.img of=/dev/sdb`

make sure records match

2288+1 records in

2288+1 records out

2400000000 bytes (2.4 GB) copied, 322.188 s, 7.4 MB/s

`sudo sync`


 