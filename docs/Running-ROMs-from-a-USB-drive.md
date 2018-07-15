Video Tutorial

<a href="https://www.youtube.com/watch?v=KBhDmGaTQG8
" target="_blank"><img src="https://img.youtube.com/vi/KBhDmGaTQG8/0.jpg" 
alt="Running Roms from USB" width="1280" height="400" border="10" /></a>

Rather than running everything from an SD card, it can be desirable to store and run ROMs from an external USB drive. The benefits of this are as follows:

-  **Reliability**: USB storage can be less sensitive to corruption than SD cards.
-  **Separation of data**: In the event that a RetroPie installation becomes corrupted or a new image is required, any ROMs, saves, etc, are not lost. Simply remove the USB stick, re-image the SD card, re-apply these setup instructions, and all that data is retained.
-  **Easy ROM transfer**: When the system is off, you can remove the stick and plug it into any other computer and easily copy-and-paste ROMs into the correct folders.
-  **Speed**: USB transfer speeds can be faster than SD card transfer speeds (see http://www.roylongbottom.org.uk/Raspberry%20Pi%20Benchmarks.htm#anchor21).
-  **Cost**: USB storage tends to be cheaper than the equivalent microSD card.
-  **Capacity**: USB storage can reach huge capacities, whereas microSD is limited.
-  **Compatibility**: microSD cards suffer from [compatibility issues](http://elinux.org/RPi_SD_cards) with Raspberry Pi systems. USB storage devices should mostly all work.

There are a number of ways you can achieve this, but the following method is desirable as it fully integrates the USB drive with the existing directory structure, rather than requiring you to tweak configuration files so RetroPie is looking for ROMs in a different place. Below there are two ways to accomplish this: an automated method, or a manual method.

### Format USB drive
Either on linux, or on a PC, format the USB drive to FAT32 (used in this guide as it is the most compatible across different operating systems).

-  [Instructions to format on Linux](https://ksearch.wordpress.com/2010/09/29/format-usb-in-linux/)
-  [Instructions to format on Windows (various)](http://www.makeuseof.com/tag/format-large-hard-drive-fat-fat32/)
-  [Instructions to format on OSX](http://qsee.custhelp.com/app/answers/detail/a_id/2560/~/mac%3A-how-to-format-a-flash-drive-to-fat32-in-mac-os-x)

## Automatic Mount (Easiest Method)

As of December 30, 2016 a simple automated method was added to run roms from a USB drive. 

1. Create a folder called `retropie-mount` on the USB drive
2. Plug into Raspberry Pi
3. It will proceed to automatically copy the `RetroPie` folder AND all of its contents (you may need to reboot to start the copying)

NOTE if you have a large ROM collection already on the SD card it will copy all of the ROMs too so make sure your USB is large enough. It is easiest if you haven't added any roms yet.

Once the folder structure is copied over the USB will be mounted over the RetroPie folder so any ROMs you add to your pi will be run off of the USB. 

## Manual Mount

After formatting your USB based on the above step:

### Disable USB transfer daemon

1. Enter the **RetroPie Setup** menu within the **RetroPie** menu in [EmulationStation](EmulationStation).
2. Select **Configuration / Tools**.
3. Select **usbromservice - USB ROM Service**
4. **Disable USB ROM Service scripts**.

### Plug in USB drive
This can be done when the system is powered on.

### Transfer the existing RetroPie file structure
This step is mandatory regardless of whether you have any roms on your system. RetroPie has a specific directory structure and a number of files required packaged with even empty installations.

Either via [SFTP](Transferring-Roms#sftp-needs-an-active-internet-connection), or using the terminal (via exiting emulationstation, pressing F4, or remotely using [[SSH]]), move the `/home/pi/RetroPie` folder into your USB stick. The reason for moving the whole folder, and not just `/home/pi/RetroPie/roms` is that there are other folders, such as /home/pi/RetroPie/BIOS` that are worth keeping on the external drive also.

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

### Configure fstab to automatically mount USB drive
Establish the drive's UUID number by entering the command `ls -l /dev/disk/by-uuid/`. Example output:
```
pi@retropie:~ $ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 15 Jun 19 21:59 7cc81461-50b9-45a8-a561-fd5c4aa71934 -> ../../mmcblk0p2
lrwxrwxrwx 1 root root 15 Jun 19 21:59 AE51-7D54 -> ../../mmcblk0p1
lrwxrwxrwx 1 root root 10 Jun 19 21:59 E44B-FC4E -> ../../sda1
```
`sda1` was our device tree position from earlier (the section above describes how to find this), so `E44B-FC4E` is our UUID.

Edit fstab with this command: `sudo nano /etc/fstab` and add a new line like the below:
```
proc            /proc           proc    defaults          0       0
/dev/mmcblk0p1  /boot           vfat    defaults          0       2
/dev/mmcblk0p2  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
UUID=E44B-FC4E  /home/pi/RetroPie      vfat    nofail,user,uid=pi,gid=pi 0       2
```
...where `UUID=` the UUID of your drive, and everything else is the same as the example. Note that each item is *tab delimited.* If you use spaces instead of tabs this will not work.

In the case of errors with ext4 file systems use
```
UUID="XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXX" /home/pi/RetroPie ext4 nofail,defaults 0    0
``` 

In the case you want to allow execution of file with fat32 file system (E.g : OpenBOR), use
```
UUID=E44B-FC4E  /home/pi/RetroPie      vfat    rw,exec,uid=pi,gid=pi,umask=022 0       2
``` 
### Restart system
This must be a full restart, not just emulationstation. When it boots up you should see any ROMs you previously had show up in emulationstation.

### Transfer ROMs
Now transfer ROMs either directly to the USB drive, or via any of the usual methods (aside from using the automatic USB copy, obviously!). Now that the USB drive is mounted directly to `home/pi/RetroPie`, every time this directory is accessed, you're actually accessing the USB drive.