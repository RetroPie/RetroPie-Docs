This is WIP!! I'll finish it soon

Rather than running everything from an SD card, it can be desirable to store and run ROMs from an external USB drive. The benefits of this are as follows:
* **Reliability**: USB storage can be less sensitive to corruption than SD cards.
* **Separation of data**: In the event that a RetroPie installation becomes corrupted or a new image is required, any ROMs, saves, etc, are not lost. Simply remove the USB stick, re-image the SD card, re-apply these setup instructions, and all that data is retained.
* **Easy ROM transfer**: When the system is off, you can remove the stick and plug it into any other computer and easily copy-and-paste ROMs into the correct folders.
* **Speed**: USB transfer speeds can be faster than SD card transfer speeds (see http://www.roylongbottom.org.uk/Raspberry%20Pi%20Benchmarks.htm#anchor21).

There are a number of ways you can achieve this, but the following method is desirable as it fully integrates the USB drive with the existing directory structure, rather than requiring you to tweak configuration files so RetroPie is looking for ROMs in a different place.

## Format USB drive
_This step is often not required, as USB drives will almost always be formatted already, although you may need to delete any old files from them._

Either on linux, or on a PC, format the USB drive. FAT32 is recommended as it is the most compatible across different operating systems.
* [Instructions to format on Linux](https://ksearch.wordpress.com/2010/09/29/format-usb-in-linux/)
* [Instructions to format on Windows 10](http://answers.microsoft.com/en-us/windows/forum/windows_10-files/formatting-usb-drive-to-fat32-file-in-windows-10/5d50af44-9dc0-4024-bfec-2e095bb22caf)
* [Instructions to format on OSX](http://qsee.custhelp.com/app/answers/detail/a_id/2560/~/mac%3A-how-to-format-a-flash-drive-to-fat32-in-mac-os-x)

## Disable USB transfer daemon
WIP

## Plug in USB drive
This can be done when the system is powered on.

## Transfer the existing RetroPie file structure
This step is mandatory regardless of whether you have any roms on your system. RetroPie has a specific directory structure and a number of files required packaged with even empty installations.

Either via [SFTP](Transferring-Roms#sftp-needs-an-active-internet-connection), or using the terminal (via exiting emulationstation, pressing F4, or remotely using [[SSH]]), copy the contents of the `/home/pi/RetroPie` folder into your USB stick. The reason for copying the whole folder, and not just `/home/pi/RetroPie/roms` is that there are other folders, such as /home/pi/RetroPie/BIOS` that are worth keeping on the external drive also.

To do this via terminal, First enter the command `mount` to print a list of the mounted drives. Example output:
WIP
then enter the command `sudo cp -ar /home/pi/RetroPie/* /media/usb0/`

After this, the USB directory structure should look like:
WIP

## Remove old files from SD card
Now that we have copied the existing files, we can delete the duplicates. Enter this command: `sudo rm -rf home/pi/RetroPie/*`

## Configure fstab to automatically mount USB drive
Establish the drive's UUID number by entering the command `ls -l /dev/disk/by-uuid/`

`sudo nano /etc/fstab`
`/dev/sda1 /home/pi/RetroPie vfat defaults 0 0`
WIP

## Restart system
This must be a full restart, not just emulationstation. When it boots up you should see any ROMs you previously had show up in emulationstation.

## Transfer ROMs
Now transfer ROMs either directly to the USB drive, or via any of the usual methods (aside from using the automatic USB copy, obviously!). Now that the USB drive is mounted directly to `home/pi/RetroPie`, every time this directory is accessed, you're actually accessing the USB drive.

NOTE: does not save all configs.