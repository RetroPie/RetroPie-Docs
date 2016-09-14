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
1. Enter the **RetroPie Setup** menu within the **RetroPie** menu in [[EmulationStation]].
2. Select **Setup / Tools**.
3. Select **usbromservice - USB ROM Service**
4. **Disable USB ROM Service**.

## Plug in USB drive
This can be done when the system is powered on.

## Transfer the existing RetroPie file structure
This step is mandatory regardless of whether you have any roms on your system. RetroPie has a specific directory structure and a number of files required packaged with even empty installations.

Either via [SFTP](Transferring-Roms#sftp-needs-an-active-internet-connection), or using the terminal (via exiting emulationstation, pressing F4, or remotely using [[SSH]]), copy the `/home/pi/RetroPie` folder into your USB stick. The reason for copying the whole folder, and not just `/home/pi/RetroPie/roms` is that there are other folders, such as /home/pi/RetroPie/BIOS` that are worth keeping on the external drive also.

To do this via terminal, First enter the command `df` to print a list of the file systems. Example output:
```
pi@retropie:~ $ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/root        7318456  3367852   3609928  49% /
devtmpfs          372100        0    372100   0% /dev
tmpfs             376436        0    376436   0% /dev/shm
tmpfs             376436     5424    371012   2% /run
tmpfs               5120        4      5116   1% /run/lock
tmpfs             376436        0    376436   0% /sys/fs/cgroup
/dev/mmcblk0p1     58234    20476     37758  36% /boot
/dev/sda1       30480256 26921632   3558624  89% /media/usb0
```

Look for an entry on /media/usb0, or similar. In our above example:
```
/dev/sda1       30480256 26921632   3558624  89% /media/usb0
```

The important things to note down are the mount point: `/media/usb0`, and the position on the device tree: `/dev/sda1`

Now we can move our existing RetroPie folder to our new USB drive. Enter the command:
```
sudo mv -v /home/pi/RetroPie/* /media/usb0/
```

After this, the USB directory structure should look something like:
```
pi@retropie:~ $ ls /media/usb0 -l
total 96
drwxrwxrwx  8 root root 16384 Jun 15 00:17 BIOS
drwxrwxrwx  3 root root 16384 Apr 22 17:05 retropiemenu
drwxrwxrwx 52 root root 16384 Jun  3 00:11 roms
drwxrwxrwx  2 root root 16384 Apr 13 16:14 splashscreens
```

## Configure fstab to automatically mount USB drive
Establish the drive's UUID number by entering the command `ls -l /dev/disk/by-uuid/`. Example output:
```
pi@retropie:~ $ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 15 Jun 19 21:59 7cc81461-50b9-45a8-a561-fd5c4aa71934 -> ../../mmcblk0p2
lrwxrwxrwx 1 root root 15 Jun 19 21:59 AE51-7D54 -> ../../mmcblk0p1
lrwxrwxrwx 1 root root 10 Jun 19 21:59 E44B-FC4E -> ../../sda1
```
`sda1` was our device tree position from earlier, so `E44B-FC4E` is our UUID.

Edit fstab with this command: `sudo nano /etc/fstab` and add a new line like the below:
```
proc            /proc           proc    defaults          0       0
/dev/mmcblk0p1  /boot           vfat    defaults          0       2
/dev/mmcblk0p2  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
UUID=E44B-FC4E  /home/pi/RetroPie      vfat    nofail,user,umask=0000  0       2
```
...where `UUID=` the UUID of your drive, and everything else is the same as the example.

## Restart system
This must be a full restart, not just emulationstation. When it boots up you should see any ROMs you previously had show up in emulationstation.

## Transfer ROMs
Now transfer ROMs either directly to the USB drive, or via any of the usual methods (aside from using the automatic USB copy, obviously!). Now that the USB drive is mounted directly to `home/pi/RetroPie`, every time this directory is accessed, you're actually accessing the USB drive.

## Edit command launcher for ports
You may start seeing permission denied errors when launching a .sh file, especially for FAT formatted drives/keys. In that case you need to prefix the command with bash.

Notably to get the 'Ports' launchers working:
 - edit es_systems.cfg with ```sudo nano /etc/emulationstation/es_systems.cfg``` and search for the PORTS Section
 - Find the < command > section and simply add bash so it looks ```<command>bash %ROM</command>```
