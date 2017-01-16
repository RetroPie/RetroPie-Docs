Storing your ROMs on a seperate computer all-together solves a number of problems and has equally as many benefits.

* It's faster
* It's more convenient
* Negates the need to transfer ROMs
* It has practically unlimited storage
* You'll (almost) never corrupt your SD card

## Mirror the 'RetroPie' or 'roms' folder to your server

This can be done a number of different ways. If you installed the RetroPie image to your SD card, the easiest thing is to go to your main computer, navigate to the hostname or ip address of your raspberry pi and copy the contents to wherever you want on your share (preferably in a simple path). If you're unable to move/copy all of the contents or you haven't setup smb shares for RetroPie, I found FTP to be favorable. Grab a copy of WinSCP or whatever you prefer to use.

## Mount your Share

If you haven't already, now is a good time to tell your Pi to wait for network at boot

    sudo raspi-config

In there, select the 4th option and tell it Yes.

### Option 1: Add to autostart.sh (Preferred if using v4.0+)

    sudo nano /opt/retropie/configs/all/autostart.sh

Add the following line to the top of that file, being sure to adjust it for your personal settings, paths and options.

    sudo mount -t cifs -o username=something,password=something //hostname/retropie /home/pi/RetroPie

Restart and make sure it mounted the folder

    sudo reboot
    ls RetroPie

Alternatively, if you have a shard folder that allows guest access, you can use the following line in your `autostart.sh`:

    sudo mount -t cifs -o guest,uid=pi //hostname/retropie /home/pi/RetroPie

This should also allow you to write save files to your NAS.

### Option 2: Add to fstab

Using your favorite editor, open up fstab:

    sudo nano /etc/fstab

Add the line to mount your network share. Mine looks like this:

    //192.168.1.10/Storage/ROMs /home/pi/RetroPie cifs username=Username,password=Password,nounix,noserverino,defaults,users,auto 0 0

First, make sure it will mount:

    sudo mount -a

Restart and check the folder to make sure it didn't have any issues mounting at boot

    sudo reboot
    sudo ls RetroPie/roms/snes

With any luck (and if you have a ton of SNES ROMs like myself), it will be fairly apparent that it was able to mount the share at boot.

## Apple Time Capsule

This will give you read/write access, so you could keep your saves there as well (i.e. no need to create separate saves folder and editing save paths).  
First [create an account on your Time Capsule](https://discussions.apple.com/message/6801520#message6801520) with the same credentials as your Pi (default: pi/raspberry).

Install `cifs-utils` if it's not already installed  
```
sudo apt-get update && sudo apt-get install cifs-utils
```  
Edit your `autostart.sh` file  
```
sudo nano /opt/retropie/configs/all/autostart.sh
```
And instead of 
```
sudo mount -t cifs -o username=something,password=something //hostname/retropie /home/pi/RetroPie
```
you enter 
```
sudo mount -t cifs //hostname/retropie -o username=USERNAME,password=PASSWORD,sec=ntlm,file_mode=0777,dir_mode=0777 /home/pi/RetroPie
```

## Saving Games

Go ahead and make sure everything works. Don't get to far into a game though, you might not be able to save. If you hit 'Select + R' (default save command) and it gives you an error, the easiest solution I've found is as follows.

We need to edit retroarch.cfg by deleting the # infront of the savestate_directory and savefile_directory lines and put in the desired path. I'll be using ~/RetroPie-Save. First, make the target folder:

    cd
    mkdir RetroPie-Save
    sudo nano /opt/retropie/configs/all/retroarch.cfg 

Mine looks like this:

    savestate_directory = /home/pi/RetroPie-Save
    savefile_directory = /home/pi/RetroPie-Save

If you already have some save files, it would be a good idea to move them to the ~/RetroPie-Save folder we created.

## Scraping

At this point, everything should be good to go. You can play and save games from your childhood. If you want to make things pretty, you'll need to scrape. You may also find that scraping just doesn't work. Thank you [@sselph](https://retropie.org.uk/forum/user/sselph) for this tip:

> A simple solution if you just want things to work would be to run

    sudo /opt/retropie/supplementary/scraper/scraper -scrape_all -thumb_only -workers 4

> That will parse the config the same as EmulationStation does then it will check every listed folder and scrape it placing the gamelist.xml in the rom folder for that system and the images in a folder called images in each system's rom folder. If the system isn't supported you may see a bunch of errors about not finding hashes or it might just take a while to not do anything.

> The other option that is a little slower is to cd to each directory and run the scraper

    cd /home/pi/RetroPie/roms/nes
    sudo /opt/retropie/supplementary/scraper/scraper -thumb_only -workers 4

## Troubleshooting

### Games Won't Load

If you have a known working game that won't load after doing this setup, you may need to make sure the folder on your Windows system isn't marked as 'Read-Only'

Right click the folder that contains your roms and BIOS folders, select "Properties", clear the box labeled "Read Only".
Sometimes this box will have a check mark or it may just be filled with gray, either way, make sure the box is clear. Select "Apply" and tell it to "Apply to all subfolders and files". After that process completes, you should be able to load your games. You may need to restart the Raspberry

### Additional Help

I started a discussion on the forums for this article. I haven't written any guides for many years so this will be a good place to provide any feedback or ask any questions. If I'm not advanced enough to help, hopefully someone else can chime in or you may need to make your own thread depending on the nature of the issue.
[ROMs from a Network Share (Discussion)](https://retropie.org.uk/forum/topic/2870/running-roms-from-a-network-share)

## Thank You
Thank you, everyone at the Raspberry Pi foundation, everyone involved in the development of EmulationStation and RetroPie, authors of several guides that I can't recall the names of, @sselph, @BuZz and probably a few other people.