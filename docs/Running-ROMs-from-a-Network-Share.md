Storing your ROMs on a seperate computer all-together solves a number of problems and has equally as many benefits.

1. It's faster
2. It's more convenient
3. Negates the need to transfer ROMs
4. It has practically unlimited storage
5. You'll (almost) never corrupt your SD card

## Mirror the 'roms' folder to your server

This can be done a number of different ways. If you installed the RetroPie image to your SD card, the easiest thing is to go to your main computer, navigate to the hostname or ip address of your raspberry pi and copy the contents of the 'roms' folder to wherever you want on your share (preferably in a simple path)

If you installed Raspbian first or something like that, you may need to use sFTP or manually make the folders.

As a side note, I was unable to move some of the files in the 'ports' system. If you can move the ports or you don't care to keep them, you may want to empty the roms folder and mount your share there. It will save you at least one step in configuration.

## Mount your Share
Great! First things first, lets mount the share. We'll need to make the target folder and use your favorite editor to edit /etc/fstab

    cd ~/RetroPie
    mkdir smb
    sudo nano /etc/fstab

Add the line to mount your network share. Mine looks like this:

    //192.168.1.10/Storage/ROMs /home/pi/RetroPie/smb username=Username,password=Password,nounix,noserverino,defaults,users,auto 0 0

First, make sure it will mount:

    sudo mount -a

If you haven't already, now is a good time to tell your Pi to wait for network at boot

    sudo raspi-config

In there, select the 4th option and tell it Yes.
Restart and check the folder to make sure it didn't have any issues mounting at boot

    sudo reboot
    sudo ls ~/RetroPie/smb

With any luck, it will be fairly apparent that it was able to mount the share at boot.

## Changing the System Paths
_If you mounted to ~/RetroPie/roms or to ~/RetroPie/, you can skip this step_

We need to tell EmulationStation to look in the ~/RetroPie/smb folder instead of ~/RetroPie/roms/.
First, copy es_systems.cfg to ~/.emulationstation/es_systems.cfg so it doesn't get overwritten

    cp /etc/emulationstation/es_systems.cfg ~/.emulationstation/es_systems.cfg

Use your favorite editor to open es_systems.cfg

    sudo nano ~/.emulationstation/es_systems.cfg

Change the path for each emulator from /home/pi/RetroPie/roms to /home/pi/RetroPie/smb

## Saving Games
At this point, you should be able to restart the Pi and play some games. But you may not be able to save your progress at this moment. 

We need to edit retroarch.cfg by commenting out the savestate_directory and savefile_directory lines and put in the desired path. I'll be using ~/RetroPie/save

    cd ~/RetroPie
    mkdir save
    sudo vi /opt/retropie/configs/all/retroarch.cfg 

Mine looks like this:

    savestate_directory = /home/pi/RetroPie/save
    savefile_directory = /home/pi/RetroPie/save

If you already have some saved files, it would be a good idea to move them to the ~/RetroPie/save folder we created.

## Tips

At this point, everything should be good to go. You can play and save games from your childhood. If you want to make things pretty, you'll need to scrape. You'll may also find that scraping just doesn't work. Thank you [@sselph](https://retropie.org.uk/forum/user/sselph) for this tip:

> A simple solution if you just want things to work would be to run

    /opt/retropie/supplementary/scraper/scraper -scrape_all -thumb_only -workers 4`

> That will parse the config the same as EmulationStation does then it will check every listed folder and scrape it placing the gamelist.xml in the rom folder for that system and the images in a folder called images in each system's rom folder. If the system isn't supported you may see a bunch of errors about not finding hashes or it might just take a while to not do anything.

> The other option that is a little slower is to cd to each directory and run the scraper

    cd /home/pi/RetroPie/smb/nes
    /opt/retropie/supplementary/scraper/scraper -thumb_only -workers 4