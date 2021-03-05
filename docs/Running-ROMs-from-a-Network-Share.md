Storing your ROMs on a separate computer (NAS) solves a number of problems and has equally as many benefits.

* It's more convenient
* It negates the need to transfer ROMs to your Raspberry PI MicroSD card
* Your storage is limited only by the size of your server
* By reducing the number of times you write to your MicroSD card you minimize the chance of corrupting it

> **Good to know**: If you are accessing your RetroPie installation over SSH the default Raspbian username is `pi` and the default password is `raspberry`.

## Copy the existing 'roms' folder structure to your server

For EmulationStation to be able to see your rom files the paths given to it within `/etc/emulationstation/es_systems.cfg` need to be recreated on your networked server. Connect to your RetroPie and browse to its roms folder for reference on how each system folder is named. Either copy these folders to your networked server or manually create the folders on your networked server using the same directory names.

If you prefer to not use the EmulationStation system directory names and keep the current folder structure you have on your networked server you'll need to edit `es_systems.cfg`. Use this command to copy the configuration file to the home directory wherein it will be editable through SMB (//RETROPIE/configs/all/emulationstation) or FTP.

    cp /etc/emulationstation/es_systems.cfg /home/pi/.emulationstation/es_systems.cfg

## Mount your Share

If you haven't already, now is a good time to tell Raspbian to wait for your network at boot.

    sudo raspi-config

In there, select "Boot Options" and tell it Yes.

### Option 1: Add to autostart.sh (Preferred if using v4.0+)

    sudo nano /opt/retropie/configs/all/autostart.sh

Add the following line to the top of that file, being sure to adjust it for your personal settings, paths and options. This will make the local roms folder use your remote server roms folder instead.

    sudo mount -t cifs -o username=something,password=something,nounix,noserverino //REMOTEHOST/path/to/roms /home/pi/RetroPie/roms

> **Good to know**: If you'd like to host the entire RetroPie folder remotely you can do so by removing the `/roms` directories from the mount command above. Make sure to have a copy of the RetroPie installation on your remote server or EmulationStation won't be able to start RetroPie!

Restart your Raspberry Pi with `sudo reboot`.

Alternatively, if you have a shared folder that allows guest access, you can use the following line in your `autostart.sh`:

    sudo mount -t cifs -o guest,uid=pi,nounix,noserverino //hostname/retropie /home/pi/RetroPie

This should also allow you to write save files to your NAS.

### Option 2: Add to fstab

Using your favorite editor, open up fstab:

    sudo nano /etc/fstab

Add the line to mount your network share. Mine looks like this:

    //192.168.1.10/Storage/ROMs /home/pi/RetroPie/roms cifs username=Username,password=Password,nounix,noserverino,defaults,users,auto 0 0

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
sudo apt update && sudo apt install cifs-utils
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



## Troubleshooting

### Games Won't Load

If you have a known working game that won't load after doing this setup, you may need to make sure the folder on your Windows system isn't marked as 'Read-Only'

Right click the folder that contains your roms and BIOS folders, select "Properties", clear the box labeled "Read Only".
Sometimes this box will have a check mark or it may just be filled with gray, either way, make sure the box is clear. Select "Apply" and tell it to "Apply to all subfolders and files". After that process completes, you should be able to load your games. You may need to restart the Raspberry

### Additional Help

I started a discussion on the forums for this article. I haven't written any guides for many years so this will be a good place to provide any feedback or ask any questions. If I'm not advanced enough to help, hopefully someone else can chime in or you may need to make your own thread depending on the nature of the issue.
[ROMs from a Network Share (Discussion)](https://retropie.org.uk/forum/topic/2870/running-roms-from-a-network-share)

### Permission Denied

If you are getting permission denied errors when you try to scrape or save states, try editing your autostart.sh and replacing:

    sudo mount -t cifs -o username=something,password=something //REMOTEHOST/path/to/roms /home/pi/RetroPie/roms

with

    sudo mount -t cifs -o sec=ntlmv2,username=something,rw,file_mode=0777,dir_mode=0777,password=something,nounix,noserverino //REMOTEHOST/path/to/roms /home/pi/RetroPie/roms

This will give you write access and should solve your problem.

> **Good to know**: Most problems with samba shares running on Windows are due to the fact that Windows 10 now no longer supports SMB1 by default. Ensure that you have a user setup on Windows with the credentials given, and that you have granted user access by right-clicking the shared folder and selecting the user from the 'Give Access To...' selection menu.

## Thank You
Thank you, everyone at the Raspberry Pi foundation, everyone involved in the development of EmulationStation and RetroPie, authors of several guides that I can't recall the names of, @sselph, @BuZz and probably a few other people.
