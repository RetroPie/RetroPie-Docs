## Installation

Follow the instructions from here: https://github.com/mcobit/retrosmc

1. Download and run install-retrosmc.sh
2. Select "install retrosmc", select "Basic installation"
3. Go outside, grab a drink, this will take ages.
4. Reboot, re-run `install-retrosmc.sh`.
5. Select "install launcher addon"
6. Reboot, go to kodi settings->addons, activate RetroPie addon.
7. Launch RetroPie in Programs menu. Done!

## Install RetroPie to USB drive:

If you're like me you have a tiny SDCard in your RPi running OSMC, but now you want to play some roms, if you try to install full RetroPie you will run out of space and OSMC will panic and die with no space left.
    
So I decided to do a few easy quick mods to make it install to a USB Drive plugged in to a connected power USB hub.
    
If you want to update an older installation, please uninstall the old version first via the script:
    
Plugin your USB Drive to the RPi, Format it EXT4
    
SSH into your OSMC installation.
    
You will lose all your data on your USB Drive if you do this!!!
    
Find your USB Drive with:
    lsblk
    
MMCBLK0 is normally your SDCard (Do not kill this one).
    
My USB Drive was SDA (8GB). 
    
    umount /dev/sda
    
    fdisk /dev/sda

Delete all partitions with:

    d

Press partition numbers until all removed.
    
Write partition table.

    w
    
Then quit

    q
    
Format our usb drive with EXT4 (Linux File System).

    mkfs.ext4 /dev/sda -L RETROPIE
    
Rename our drive label RETROPIE (If you forget to label your drive in the last step)

    e2label /dev/sda RETROPIE
    
Remove the USB Drive from the port and reinsert it. It should now be remounted under /media/RETROPIE/
    
Download the installation script to your OSMC home directory:
    
    cd /home/osmc
    wget https://raw.githubusercontent.com/mcobit/retrosmc/master/install-retrosmc.sh

Make it executable by running:
    
    chmod +x install-retrosmc.sh

Then run it:
    
    ./install-retrosmc.sh
    
Click install Retrosmc 
    
After it finishes downloading the setup scripts (ie you see the options menu) click cancel until you are back to the cli.
    
    cd ~/RetroPie-Setup
    
    nano retropie_packages.sh
    
    #main retropie install location
    rootdir="/opt/retropie"
    modify this line to:
    rootdir="/media/RETROPIE/retropie"
    
Save:
    Press ctrl x
    Press y
    Press <Enter>
    
    
    ../install-retrosmc.sh
    
    
Click install Retrosmc again.
    
Once you get to the second menu select "Binary-based installation (recommended)" when the RetroPie-Setup script pops up and press enter.

After the RetroPie-Setup script finished the installation, press Enter for all windows, mentioning DATA and BIOS files for the emulators. When back at the main RetroPie menu, choose "Cancel"!

Install the Launcher Addon, you will find your shortcut in the Programaddons in kodi.

You can exit the menu by choosing Cancel at the bottom after every task.

    nano /home/osmc/RetroPie/scripts/retropie.sh

Change:

    es_bin="/opt/retropie/supplementary/emulationstation/emulationstation"
To:
    es_bin="/media/RETROPIE/retropie/supplementary/emulationstation/emulationstation"

    Save:
    Press ctrl x
    Press y
    Press <Enter>

Let's move the roms folder to the Flash Drive as well now and make a soft system link to it.
    
    cd ../RetroPie
    mv roms roms2
    mkdir /media/RETROPIE/roms
       
    sudo apt-get install rsync
    rsync roms2 /media/RETROPIE/roms
    
    ln -s /media/RETROPIE/roms roms

Original install documentation see there for more help with issues: https://discourse.osmc.tv/t/howto-retrosmc-retrogaming-on-osmc/6671