![](http://1.bp.blogspot.com/-q1BVHMrTq7M/UT9Y6D_tCLI/AAAAAAAAD40/fM2ZUTzEIqE/s1600/risen3d+3d+models+doom+title.png)

***
_Doom was the one game that popularized First Person Shooting as a genre. It was developed by Id Software in 1993._

***
# Emulators: [lr-prboom](https://github.com/petrockblog/RetroPie-Setup/blob/master/scriptmodules/libretrocores/lr-prboom.sh), [ZDoom](https://github.com/rheit/zdoom)

# Controls

## Configuring controls for lr-prboom

lr-prboom utilises normal Retroarch control configurations found in the RetroArch menu by pressing 'select+x' on your controller after the game software has launched. From the RetroArch menu, navigate to 'Quick Menu' and then to 'Controls'.

For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/retropie/retropie-setup/wiki/retroarch-configuration)

## Configuring controls for ZDoom

ZDoom controls can be found in the Doom options menu by pressing any button or key after the game software has launched. Although the initial configuration may need to be started with a keyboard, full joystick autonomy is possible after being set.

## How to Launch Doom IWADs and Mods (PWADs) from Emulationstation using lr-prboom

### To Launch Doom, Ultimate Doom, Doom 2, TNT, Plutonia, Final Doom (IWADS) - Method 1 (savegames issue)

Place your WADs in the doom rom folder, `/home/pi/RetroPie/roms/ports/doom`.

Create a shell script to launch your WAD. For example, for The Plutonia Experiment, 

```
nano /home/pi/RetroPie/roms/ports/The\ Plutonia\ Experiment.sh
```

The nano text editor will open, where you will now add the following to the text edit field.

```
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/plutonia.wad"
```

press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

Set the proper file permissions for the script with:

```
chmod 0755 "/home/pi/RetroPie/roms/ports/The\ Plutonia\ Experiment.sh"
```

Set the default emulator for ROM to 'lr-prboom' at launch in the runcommand menu.

### To Launch Doom, Ultimate Doom, Doom 2, TNT, Plutonia, Final Doom (IWADS) - Method 2 (savegames separated)

* Place your WADs - like method 1 - in the doom rom folder, `/home/pi/RetroPie/roms/ports/doom`.
* Install zip extension via aptitude `sudo apt install zip`

__Why?__

Keep in mind that PrBoom treats all games equal, so every game got the same saving structure and if you save gamestate for __The Ultimate DOOM__ in first position and you launch __DOOM 2 - Hell on Earth__ then the savestate of the first gameplay is displayed during loading/saving actions in first position. So you can overwrite savegames by mistake... or of you want to load this then PrBoom gives an error message.

This will happen an all WADs DOOM, DOOM2, TNT, Plutonia, FreeDoom1, FreeDoom2..... We have only 8 savepoints at all!

__How to solve?__
 
Create a shell script to launch your WAD. For example, for The Plutonia Experiment, 
```
nano /home/pi/RetroPie/roms/ports/The\ Plutonia\ Experiment.sh
```

The nano text editor will open, where you will now add the following to the text edit field.

```bash
#!/bin/bash
path="/home/pi/RetroPie/roms/ports/doom"
wadfile="plutonia.wad"

unzip -qq -o "${path}/savegames_${wadfile%.*}.zip" -d "$path"
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "${path}/$wadfile"
cd "$path" && zip -mj "savegames_${wadfile%.*}.zip" prbmsav?.dsg
```

press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

Set the proper file permissions for the script with:

```
chmod 0755 "/home/pi/RetroPie/roms/ports/The\ Plutonia\ Experiment.sh"
```

Set the default emulator for ROM to 'lr-prboom' at launch in the runcommand menu.

More scripts can be [downloaded here](https://github.com/crcerror/launch-doom-packs-RP)

### To Launch Doom Mods (PWADS)

In the doom rom folder, you will need prboom.wad and whichever Doom IWAD is required for the particular mod (`doom.wad` and/or `doom2.wad`).

Create a folder named for the intended mod and transfer the custom PWAD there. 

Using the 'Batman Doom' mod as an example, we'll create a folder called 'batman_doom' by typing:

```
mkdir /home/pi/RetroPie/roms/ports/batman_doom/
```

Create symlinks to prboom.wad and Doom2 WAD in the batman_doom folder with the following commands. If you have problems creating these links, you can also just copy these files.

```shell
ln -s /home/pi/RetroPie/roms/ports/doom/prboom.wad /home/pi/RetroPie/roms/ports/batman_doom/prboom.wad
```
```shell
ln -s /home/pi/RetroPie/roms/ports/doom/doom2.wad /home/pi/RetroPie/roms/ports/batman_doom/doom2.wad
```

Copy prboom.cfg from the Doom folder to the custom WAD folder. Add the name(s) of the custom WADs to #Files section (line 15/16).

Create a shell script named 'Batman Doom.sh' that will launch the custom WAD. 

```
nano /home/pi/RetroPie/roms/ports/Batman\ Doom.sh
```

The nano text editor will open, where you will now add the following to the text edit field. It's the same as Doom 2 script but it points to the Doom 2 IWAD in the batman folder instead.

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/doom/batman/doom2.wad" "lr-prboom"
```
press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

Set the proper file permissions for the script with:

```
chmod 0755 "/home/pi/RetroPie/roms/ports/Batman\ Doom.sh"
```

Repeat for each mod (PWAD), creating a new folder for each one and a copy of the script above replacing the folder name as required.

## How to Launch Doom IWADs and Mods (PWADs) from Emulationstation using ZDoom.

### To Launch Doom, Ultimate Doom, Doom 2, TNT, Plutonia, Final Doom (IWADS)

Use the same method for IWADS detailed above for lr-prboom, only set the default emulator for ROM to 'zdoom' at launch in the runcommand menu.

### To Launch Doom Mods (PWADS)

Here, we'll use [Rex Claussen's, The Darkest Hour](http://doomnexus.drdteam.org/DH_Pix.html) as an example that can be used for any mod. Start by downloading [The Darkest Hour](ftp://ftp.fu-berlin.de/pc/msdos/games/idgames/levels/doom2/Ports/d-f/darkhour.zip). Next you will either want to SSH into your Pi, or drop out of EmulationStation using F4 on your keyboard. 

At the command line, type the following to create a directory for the `DarkHour.wad` file from the 'Darkest Hour' download.

```
mkdir /home/pi/RetroPie/roms/ports/darkesthour
```

You may now transfer the `DarkHour.wad` file to this location via SFTP or Samba.

Next you'll want to create a new script that we will use to launch The Darkest Hour from EmulationStation.

To do this, type:

```
nano /home/pi/RetroPie/roms/ports/The\ Darkest\ Hour.sh
```

The nano text editor will open, where you will now add the following to the text edit field.

```shell
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ darkesthour
```

press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

Set the proper file permissions for the script with:

```
chmod 0755 "/home/pi/RetroPie/roms/ports/The\ Darkest\ Hour.sh"
```

Now we want to create a config folder by typing the following:

```
mkdir /opt/retropie/configs/ports/darkesthour
```

Once this is complete you will want to create a 'emulators.cfg' file for this new config folder by typing:

```
nano /opt/retropie/configs/ports/darkesthour/emulators.cfg
```

The nano text editor will open, where you will now add the following to the text edit field.

```
zdoom = "/opt/retropie/ports/zdoom/zdoom +set fullscreen 1 -iwad /home/pi/RetroPie/roms/ports/doom/doom2.wad -file /home/pi/RetroPie/roms/ports/darkesthour/DarkHour.wad"
default="zdoom"
```

press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

You'll notice that in the above example that ZDoom is making use of the 'Doom II' wad as a base for the 'Darkest Hour' modification. This is common in most cases. However, some mods will need to make use of the 'Ultimate Doom' wad file entitled `doom.wad` instead. Both `doom.wad` and `doom2.wad` should be installed to `/home/pi/RetroPie/roms/ports/doom/` and the above example should be set accordingly.

Having completed this step, you will now want to restart Emulation Station, navigate to 'Ports' and test your new menu entry.

## How to setup Freedoom

[Freedoom](https://freedoom.github.io/index.html) is a collection of reusable assets (textures, sound effects and music tracks) that will completely replace the original Doom assets and are liberally licensed under the [BSD license](https://en.wikipedia.org/wiki/BSD_licenses).

Why is this important to me?

[id Software](http://www.idsoftware.com/) released the source code for Doom's engine under the [GNU General Public License](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html) but not the assets so to legally use this, you would either need the [shareware version](ftp://ftp.idsoftware.com/idstuff/doom/) or you would need to own the original game (which you can still purchase online on [Steam](http://store.steampowered.com/sub/18397/), [GOG.com](https://www.gog.com/game/the_ultimate_doom) and other places like eBay).

Freedoom aims to be compatible with many of the thousands of Doom levels and other “mods” already released for the original game making them playable without the need to use non-free software.  This project has been a work-in-progress for many years now and has already replaced a considerable amount of the game's content but still haven't reached the targeted version 1.0.

Freedoom is divided into three [IWADs](https://zdoom.org/wiki/IWAD).

* Phase 1, which is a replacement for the original Doom and The Ultimate Doom containing 4 chapters with 9 levels each.

* Phase 2, which replaces Doom II and Final Doom and contains a massive 32-level chapter.

* Last FreeDM, which also replaces Doom II and Final Doom and is designed to be a fast-paced competitive deathmatch only campaign containing no monsters.

First you need to download Freedoom: [https://freedoom.github.io/download.html](https://freedoom.github.io/download.html)

As of this writing, the newest version of Freedoom is 0.11.2 so you can use wget to download the 2 files needed:
```
cd
wget https://github.com/freedoom/freedoom/releases/download/v0.11.2/freedoom-0.11.2.zip && wget https://github.com/freedoom/freedoom/releases/download/v0.11.2/freedm-0.11.2.zip
```

Next extract both files:

`unzip freedoom-0.11.2.zip && unzip freedm-0.11.2.zip`

The files will be extracted to folders named `freedoom-0.11.2` and `freedm-0.11.2` respectively and I like to keep all the Doom WADs in the same folder so why not put them with the shareware doom1.wad.

`mv freedoom-0.11.2/freedoom*.wad freedm-0.11.2/freedm.wad /home/pi/RetroPie/roms/ports/doom/`

Now we need to make scripts so we can launch Freedoom from EmulationStation using lr-prboom. We want to place these scripts in the Ports directory.

`nano /home/pi/RetroPie/roms/ports/Freedoom\ Phase\ 1.sh`

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/ports/doom/freedoom1.wad" "lr-prboom"
```

`nano /home/pi/RetroPie/roms/ports/Freedoom\ Phase\ 2.sh`

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/ports/doom/freedoom2.wad" "lr-prboom"
```

`nano /home/pi/RetroPie/roms/ports/FreeDM.sh`

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/ports/doom/freedm.wad" "lr-prboom"
```

If you would rather use [ZDoom](https://zdoom.org/News) use this with the correct WAD filename:

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/ports/zdoom/zdoom -iwad /home/pi/RetroPie/roms/ports/doom/freedoom1.wad" "zdoom"
```

After all the scripts have been made, you will need to set them to be executable.

`chmod +x /home/pi/RetroPie/roms/ports/Freedoom\ Phase\ 1.sh /home/pi/RetroPie/roms/ports/Freedoom\ Phase\ 2.sh /home/pi/RetroPie/roms/ports/FreeDM.sh`

Last step is to reboot EmulationStation and navigate to the Ports.  You should now see these 3 Freedoom games on the list.

To delete the left over extracted folders and downloaded files:
```
cd
rm -rf freedoom-0.11.2/ freedm-0.11.2/ freedoom-0.11.2.zip freedm-0.11.2.zip
```

## Music

### Music for lr-prboom

To enable music in your Doom games, you need to copy MP3s with specific names into the same folder your WAD for the game is located via ftp client such as this one https://winscp.net/eng/download.php. You can find a list of the names [here](https://github.com/libretro/libretro-prboom/blob/master/src/m_misc.c#L605).

The easiest to use and highest quality soundtrack you can get for games running in lr-prboom are the ones generated by a Roland SC-55 then digitized to MP3. Due to legal reasons, these soundtracks can't be linked here, but if this music is found, a leading `d_` will need to be removed from each MP3's filename.

Keep in mind that the soundtracks for Doom 2, Final Doom: TNT: Evilution, and Final Doom: The Plutonia Experiment are different even though their tracks are named identically. This means that the WADs/MP3s for those three games must be in separate folders to avoid filename conflicts between the MP3s.

An alternative source for alternative music for your Doom games would be from [Aubrey Hodges](https://aubreyhodges.bandcamp.com/), who scored Doom/Doom 2 and Final Doom: TNT: Evilution/The Plutonia Experiment on the PSX, though properly renaming/duplicating the MP3s for each game would currently be an arduous task due to lack of a chart to reference.

### Where to put the mp3 tracks for doom

Make sure you've launched Ir-prboom at least once within Emulationstation as this would generate the prboom.cfg file.

Log into your raspberry pi via ftp client(hostname: ip address, username: pi, password: raspberry). 

Navigate to /home/pi/RetroPie/roms/ports/doom.

We will need to create a new directory within /doom where you will store all your mp3 tracks in. Lets call it         mp3-directory. 

Navigate to /home/pi/RetroPie/roms/ports/doom/doom1 and open prboom.cfg

Scroll down until you see the line #Music.

From there you will see the track names off to the right.

Now, just follow this naming scheme for each track: 


"./mp3-directory/trackname.mp3"

### Note

For Doom 2,  the prboom.cfg file would be located in the /doom2 directory(or folder).







   

