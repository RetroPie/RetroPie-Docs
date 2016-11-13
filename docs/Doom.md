![](http://1.bp.blogspot.com/-q1BVHMrTq7M/UT9Y6D_tCLI/AAAAAAAAD40/fM2ZUTzEIqE/s1600/risen3d+3d+models+doom+title.png)

***
_Doom was one the game the popularised First Person Shooting as a genre. It was developed by Id Software in 1993._

***
## Emulator: [libretro-prboom](https://github.com/petrockblog/RetroPie-Setup/blob/master/scriptmodules/libretrocores/lr-prboom.sh), [ZDOOM](https://github.com/rheit/zdoom)

## Controls
libretro-prboom utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/doom/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

### How to Launch Doom IWADs and Mods (PWADs) from Emulationstation using lr-prboom

#### To Launch Doom, Ultimate Doom, Doom 2, TNT, Plutonia, Final Doom (IWADS)

Place your WADs in the doom rom folder, `/home/pi/RetroPie/roms/ports/doom`.

Create a script to launch your WAD. For example, for The Plutonia Expriment, create a script, `/home/pi/RetroPie/roms/ports/The Plutonia Experiment.sh`, which contains the following:

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/ports/doom/Plutonia.wad" "lr-prboom"
```
Create a copy of the script for each WAD, replacing the name of the WAD for each one.

#### To Launch Doom Mods (PWADS)

In the doom rom folder, you will need prboom.wad and the Doom IWADs (doom.wad and/or doom2.wad).

Create a folder for the custom PWAD and extract your custom PWAD(s) there. For example, for the Batman Doom mod, create a folder called batman.

Create symlinks to prboom.wad and Doom2 WAD in the batman folder with the following commands. If you have problems creating these links, you can also just copy these files.

```shell
ln -s /home/pi/RetroPie/roms/ports/doom/prboom.wad /home/pi/RetroPie/roms/ports/batman/prboom.wad
```
```shell
ln -s /home/pi/RetroPie/roms/ports/doom/doom2.wad /home/pi/RetroPie/roms/ports/batman/doom2.wad
```

Copy prboom.cfg from the Doom folder to the custom WAD folder. Add the name(s) of the custom WADs to #Files section (line 15/16).

Create a shell script, Batman Doom.sh to launch the custom WAD as below. It's the same as Doom 2 script but it points to the Doom 2 IWAD in the batman folder instead.

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/doom/batman/doom2.wad" "lr-prboom"
```

Repeat for each mod (PWAD), creating a new folder for each one and a copy of the script above replacing the folder name as required.

#### Permission Denied Errors

A permission denied error after launching a script from EmulationStation means the script is not executable. This can be fixed with the following command (using Batman Doom as an example):

    sudo chmod +x "/home/pi/RetroPie/roms/ports/Batman Doom.sh"

### How to Launch Doom IWADs and Mods (PWADs) from Emulationstation using ZDOOM.

First off, you will want to go into RetroPie-Setup, and install ZDOOM from Experimental Packages. 

Once installed, we will employ [Rex Claussen's, The Darkest Hour](http://doomnexus.drdteam.org/DH_Pix.html).

Go ahead and [Download The Darkest Hour](ftp://ftp.fu-berlin.de/pc/msdos/games/idgames/levels/doom2/Ports/d-f/darkhour.zip). Once downloaded, go ahead and extract it's contents to somewhere on your hard drive so that you know where to find it as we will come back to it here shortly.

Next you will either want to SSH into your Pi, or drop out of EmulationStation using F4 on your keyboard. 
At the command line, type the following to navigate to your `ports` directory.

`cd /home/pi/RetroPie/roms/ports/`

 Next, let's create a directory called `zdoom`. To do so, type the following:

`mkdir zdoom`

 Now type the following in order to enter the "zdoom" directory.

`cd zdoom`

Once inside of "zdoom", type the following command to create a folder where The Darkest Hour's files will reside. 

`mkdir DarkestHour`

 Next you will want navigate back to the ports directory by typing the following:

`cd ~/RetroPie/roms/ports/`

 From here you will want to create a new script that we will use to launch The Darkest Hour from EmulationStation.

To do this, type the following to open into the Nano text editor.

`sudo nano Darkest Hour.sh`

 Next we will want type out the following so that it appears exactly as you see it here:

`#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _SYS_ darkesthour`

 In order to save your work, hold Down `CONTROL + X`. Type `Y` to confirm, then give it the title of `Darkest Hour.sh`, then confirm the save. 

 Once that is complete you will want to type the following so that you have proper permissions within EmulationStation to launch The Darkest Hour. 

`sudo chmod 775 Darkest\ Hour.sh`

Now we will need to navigate to the /opt/retropie/configs/ folder by typing the following:

`cd /opt/retropie/configs/`

 From here you will want to create a folder in call lower case titled `darkesthour`, by typing the following:

`mkdir darkesthour`

Once this is complete you will want to copy the files from the `doom` folder into the `darkesthour` folder by typing the following:

`cp doom/*.* darkesthour/`

Then you will need to navigate into the `darkesthour` directory by typing:

`cd darkesthour`

From within the folder you will want to edit the file `retroarch.cfg` by typing:

`sudo nano retroarch.cfg`

One inside of Nano, you will see the following:

```
# Settings made here will only override settings in the global retroarch.cfg if placed above the #include line

input_remapping_directory = /opt/retropie/configs/doom/

#include "/opt/retropie/configs/all/retroarch.cfg"
```

Change it so that it reads as follows:

```
# Settings made here will only override settings in the global retroarch.cfg if placed above the #include line

input_remapping_directory = /opt/retropie/configs/darkesthour/

#include "/opt/retropie/configs/all/retroarch.cfg"
```

Save your work by holding Down `CONTROL + X`. Then keep hitting `Y` to confirm each step until save. 

Next you will want to edit `emulators.cfg`. To do this type:

`sudo nano emulators.cfg`

Nano will open and you will see the following:

`lr-prboom="/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/doom/retroarch.cfg /ho$
default="zdoom"
zdoom="/opt/retropie/ports/zdoom/zdoom -iwad /home/pi/RetroPie/roms/ports/doom/doom1.wad"`

Edit it so that it looks like this:

`lr-prboom="/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/darkesthour/retroarch.cfg /ho$
default="zdoom"
zdoom="/opt/retropie/ports/zdoom/zdoom -iwad /home/pi/RetroPie/roms/ports/doom/doom2.wad -file /home/pi/RetroPie/roms/ports/zdoom/DarkestHour/DarkHour.wad"`

Save your work by holding Down `CONTROL + X`. Then keep hitting `Y` to confirm each step until save. 

 Returning to your computer you will want to navigate to your /home/pi/RetroPie/roms/ports/zdoom/DarkestHour/ folder on the Pi, via SFTP or Samba.

Next copy over the `DarkHour.wad` file from your PC into the `DarkestHour` directory on the Pi. 

Now that this is complete you will want to go back two directories so that we are in the `ports` directory. Next advance one folder so that you are inside of the `doom` directory. Now copy over a fully upgraded original DOOM II iWAD, or one from DOOM 3. It should be titled `doom2.wad`, and should be in all lower case.  

 Having completed this step, you will now want to reboot EmulationStation, navigate to `Ports` and test your new `Darkest Hour` entry.

### Music

The most ideal and authentic way to listen to the the original Doom (1&2) tracks is to google 'doom 1 and 2 midis' and download them. You can then convert the midi files into MP3s.

To enable music in your Doom game(s) you need to copy MP3s with specific names into the same folder as your ROMs are located. You can find a list of names [here](https://github.com/libretro/libretro-prboom/blob/master/src/m_misc.c#L605): They follow the scheme e1m1.mp3, e1m2.mp3, ..., e2m1.mp, e2m2.mp3, ... . There are freely available tracks available - find them by searching for "PSX Doom Music".

If you are having trouble with the audio not playing after you have renamed all the MP3s, try clearing all the ID3 tag information for each of the MP3s.

Below are the corresponding tracks if the MP3s are named:

File Name | mp3 
 --- | ---
* mus_e1m1       |           "level 01 (hangar).mp3" 
* mus_e1m2        |          "level 02 (plant).mp3" 
* mus_e1m3         |         "level 03 (toxin refinery).mp3" 
* mus_e1m4          |        "level 04 (command control).mp3" 
* mus_e1m5           |       "level 05 (phobos lab).mp3" 
* mus_e1m6            |      "level 06 (central processing).mp3" 
* mus_e1m7            |      "level 07 (computer station).mp3" 
* mus_e1m8          |        "level 08 (phobos anomaly).mp3" 
* mus_e1m9           |       "level 06 (fistula).mp3" 
* mus_e2m1          |        "level 09 (deimos anomaly).mp3" 
* mus_e2m2          |        "level 10 (containment area).mp3" 
* mus_e2m3          |        "level 11 (refinery).mp3" 
* mus_e2m4          |        "level 12 (deimos lab).mp3" 
* mus_e2m5          |        "level 13 (command center).mp3" 
* mus_e2m6          |        "level 02 (plant).mp3" 
* mus_e2m7          |        "level 01 (hangar).mp3" 
* mus_e2m8          |        "level 03 (toxin refinery).mp3" 
* mus_e2m9          |        "level 02 (virgil).mp3" 
* mus_e3m1          |        "level 17 (hell keep).mp3" 
* mus_e3m2          |        "level 03 (canyon).mp3" 
* mus_e3m3          |        "level 18 (pandemonium).mp3" 
* mus_e3m4          |        "level 06 (central processing).mp3" 
* mus_e3m5          |        "level 20 (unholy cathedral).mp3" 
* mus_e3m6          |        "level 21 (mt erebus).mp3" 
* mus_e3m7          |        "level 22 (limbo).mp3" 
* mus_e3m8          |        "level 09 (nessus).mp3" 
* mus_e3m9          |        "level 10 (paradox).mp3" 
* mus_inter         |        "e2m3.mp3" 
* mus_intro         |        "track 02 title screen.mp3" 
* mus_bunny         |        "track 03 main menu.mp3" 
* mus_victor        |        "track 09 endgame.mp3" 
* mus_introa        |        "track 02 title screen.mp3" 
* mus_runnin        |        "level 01 (hangar).mp3" 
* mus_stalks        |        "level 10 (containment area).mp3" 
* mus_countd        |        "level 22 (limbo).mp3" 
* mus_betwee        |        "level 16 (hell gate).mp3" 
* mus_doom          |        "level 08 (phobos anomaly).mp3" 
* mus_the_da        |        "level 21 (mt erebus).mp3" 
* mus_shawn         |        "level 20 (unholy cathedral).mp3" 
* mus_ddtblu        |        "level 24 (hell beneath).mp3" 
* mus_in_cit        |        "level 11 (refinery).mp3" 
* mus_dead          |        "level 13 (command center).mp3" 
* mus_stlks2           |     "level 09 (deimos anomaly).mp3" 
* mus_theda2           |     "level 17 (hell keep).mp3" 
* mus_doom2            |     "level 08 (minos).mp3" 
* mus_ddtbl2            |    "level 16 (hell gate).mp3" 
* mus_runni2           |     "level 04 (combine).mp3" 
* mus_dead2            |     "level 18 (pandemonium).mp3" 
* mus_stlks3          |      "level 06 (central processing).mp3" 
* mus_romero          |      "level 05 (phobos lab).mp3" 
* mus_shawn2          |      "level 10 (containment area).mp3" 
* mus_messag          |      "level 01 (attack).mp3" 
* mus_count2          |      "level 02 (plant).mp3" 
* mus_ddtbl3         |       "level 03 (toxin refinery).mp3" 
* mus_ampie          |       "level 01 (hangar).mp3" 
* mus_theda3         |       "level 06 (fistula).mp3" 
* mus_adrian           |     "level 07 (computer station).mp3" 
* mus_messg2          |      "level 08 (phobos anomaly).mp3" 
* mus_romer2          |      "level 11 (refinery).mp3" 
* mus_tense           |      "level 07 (geryon).mp3" 
* mus_shawn3          |      "level 05 (catwalk).mp3" 
* mus_openin          |      "level 04 (command control).mp3" 
* mus_evil            |      "level 16 (hell gate).mp3" 
* mus_ultima          |      "level 03 (toxin refinery).mp3" 
* mus_read_m          |      "track 03 main menu.mp3" 
* mus_dm2ttl          |      "track 02 title screen.mp3" 
* mus_dm2int         |       "track 05 stats screen.mp3"

