[NOOBS (New Out of Box Software)](https://github.com/raspberrypi/noobs) is an easy way to set up an SD card for a Raspberry Pi. It has the added benefit of making it easy to set up the Pi to boot multiple operating systems. Here's how to convert a RetroPie SD Card image to a NOOBS-compatible image.

_These instructions are largely based on the instructions for creating a custom OS image on [the NOOBS GitHub repository](https://github.com/raspberrypi/noobs#how-to-create-a-custom-os-version)_

You will need read access to all partitions of the flashed SD card. While RPi's instructions imply they can be followed directly from the Pi itself, you may be able to find plugins for your primary computer's operating system to allow read access to the ext-formatted partition of the SD card. This will allow you to use the full power of your computer to create the compressed disk image and probably save you hours.

For OS X users, [here is a tutorial for mounting the filesystem](http://osxdaily.com/2014/03/20/mount-ext-linux-file-system-mac/), and you can install the `tar` and `xz` commands using [Homebrew](http://brew.sh).

1. [Download the latest RetroPie image](https://retropie.org.uk/download) and [flash an SD card (or other volume) with it](First-Installation#installation)
2. [Download the latest NOOBS release](https://github.com/raspberrypi/noobs/releases). You will need the full NOOBS download (not NOOBS Lite) since we will be using the included Raspberry Pi OS image as a base.
3. While that downloads, write down the full sizes of the two partitions on the RetroPie SD card ('boot' and 'retropie' as of this writing). You will need them later. (OS X users: type `diskutil list` at the command line to get this easily, Linux users: type `df -h` in the terminal.)
4. Create the `.tar` file of the main RetroPie filesystem (the 'retropie' partition). From the command line on your primary computer, navigate to where the 'retropie' partition is mounted (on OS X, try `cd /Volumes/retropie`). The command is `sudo tar -cvpf ~/Desktop/retropie.tar ./*` and this will create the `retropie.tar` file on your desktop.
5. Write down the size of `retropie.tar` in megabytes.
6. Navigate to your desktop (or wherever you saved the tarball) with `cd ~/Desktop/` and compress the tarball with the command `xz -9 -e -v retropie.tar`. This will take some time.
7. Now we need to do the same thing to the 'boot' partition, but `tar` apparently doesn't like FAT-formatted volumes. So... Copy the contents of the 'boot' partition to a folder on your hard drive. I used `~/Desktop/rpi/boot`.
8. From the command line, navigate to the 'boot' folder you just created. The command is `sudo tar -cvpf ~/Desktop/boot.tar ./*` and this will create the `boot.tar` file on your desktop.
9. Write down the size of `boot.tar` in megabytes.
10. Navigate to your desktop (or wherever you saved the tarball) with `cd ~/Desktop/` and compress the tarball with the command `xz -9 -e -v boot.tar`. This won't take long, not nearly as long as the 'retropie' tarball.
11. Hopefully NOOBS has finished downloading by now. Unzip it, and open up the 'os' folder. Duplicate the 'Raspberry Pi OS full' folder and rename it 'RetroPie'.
12. Open up 'partitions.json' in your favorite (or second-favorite) text editor and make the following changes:
   * Change the `label` on the `root` partition to read `retropie`.
   * Change the value for `parition_size_nominal` for both `boot` and `retropie` to be the values from step 3 in megabytes. Since this is used by NOOBS to determine how much space will be on the SD card after install, it's better to round up than down. (Ex: a 59.8 MB partition would have a value of 60. A 1.9 GB partition would have a value of around 2000.) 
    * Change the value for `uncompressed_tarball_size` to be the values from step 5 and 9
13. If there is a 'flavours.json' file, throw it out. We don't need it.
14. Open 'os.json' in whatever text editor is handy and make the following changes:
    * Change `name` to `RetroPie`
    * Optional) Change whatever else you want. At the very least you should probably change `url` to `https://retropie.org.uk/` to provide proper credit to the awesome people who put this project together!
    * (Optional) Replace the 'Raspbian_Full.png' with 'RetroPie.png' from [this image](https://www.petrockblock.com/wp-content/uploads/2015/06/RetroPieLogo2015Download.png) as an appropriate icon.
    * (Optional) Replace any or all of the files in the 'slides_vga' folder with approporiate images. These will be shown during the install process.
    * Replace the 'boot.tar.xz' and 'root.tar.xz' with the 'retropie.tar.xz' and 'boot.tar.xz' files you created in steps 6 and 10.
    * Format and prepare an SD card as described in the [NOOBS Setup Guide](https://github.com/raspberrypi/noobs). RetroPie should be available as an option in the OS list next to Rasperry Pi OS.
15. _Profit!_

&&NOTE**: If the boot process is halting at the resizing of the ext4 partition, delete `/etc/profile.d/01-expand.sh` on the ext4 partition. NOOBS already resized the partition.

From the command line:
``` sh
sudo rm 01_expand.sh
```
If the 01-expand.sh file isn't yet in this directory, just delete `bash_completion.sh` by running:
``` sh
sudo rm bash_completion.sh
```
