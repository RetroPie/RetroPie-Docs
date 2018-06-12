***
![](http://dedarwin.net/wp-content/uploads/2015/03/love2d.png)
***
_Löve is a 2d game engine programmed primarily in lua._
***
## Emulator [Löve](https://bitbucket.org/rude/love/src) (Experimental)

It only really works well on a Raspberry Pi 2. Games are programmed for different versions of Löve. RetroPie uses Love 0.10.0 and so it is likely a lot of games will not work because they have not been updated for version 0.10.0

## ROMS

Accepted File Extensions: **.love**

Place your Löve games in

```
/home/pi/RetroPie/roms/love/
```

Note that love games are basically .zip files with a .love extension instead of a .zip, so when building love files from repos, the files all need to be in the top level directory (especially main.lua)

## Controls

Controls vary by game though most will need a keyboard. [**Mari0**](http://stabyourself.net/mari0/) (which is installed when you install Löve) has some support for gamepads but you still need to use a keyboard to navigate the menus. 

For display it is best to leave the video settings alone in the runcommand menu and just use the in game settings to scale it to 5.

### Other Games:

You can add the following scripts in the configure function of `/home/pi/RetroPie-Setup/scriptmodules/ports/love.sh`

or you can just follow the links and download the .love files and place them into your ROM folders manually.


[**Mr. Rescue**](http://tangramgames.dk/games/mrrescue/)

```
    # get mrrescue-1.02e.love (freeware game data)
    if [[ ! -f "$romdir/love/mrrescue-1.02e.love" ]]; then
        wget "https://github.com/SimonLarsen/mrrescue/releases/download/1.02e/mrrescue1.02e.love" -O "$romdir/love/mrrescue-1.02e.love"
        chown $user:$user "$romdir/love/mrrescue-1.02e.love"
    fi
```


[**Sienna**](http://tangramgames.dk/games/sienna/)

```
    # get sienna-1.0c.love (freeware game data)
    if [[ ! -f "$romdir/love/sienna-1.0c.love" ]]; then
        wget "https://github.com/SimonLarsen/sienna/releases/download/v1.0c/sienna-1.0c.love" -O "$romdir/love/sienna-1.0c.love"
        chown $user:$user "$romdir/love/sienna-1.0c.love"
    fi
```

[**90 Second Portraits**](http://tangramgames.dk/games/90secondportraits/)

```
    # get 90secondportraits-1.01b.love (freeware game data)
    if [[ ! -f "$romdir/love/90secondportraits-1.01b.love" ]]; then
        wget "https://github.com/SimonLarsen/90-Second-Portraits/releases/download/1.01b/90secondportraits-1.01b.love" -O "$romdir/love/90secondportraits-1.01b.love"
        chown $user:$user "$romdir/love/90secondportraits-1.01b.love"
     fi
```

It can be run with

```
cd RetroPie-Setup
sudo ./retropie_packages.sh love configure
```

## Versions

The default behavior of RetroPie is to always install the latest version of Love. Currently, this is version 11. However, most games are written for version 10 and are incompatible with this version. This includes the bundled Mari0 game which will just show a blue screen and an error message if it is started with version 11 of Love.

In order get Mari0 and most other games to work, it is necessary to install the older version 10 of Love. This requires editing the install script to point it to the older version, and then (re-)installing Love from source. For this, a keyboard and internet access are required:

- in Emulationstation, press F4 to open a command line, then enter
```
sudo nano RetroPie-Setup/scriptmodules/ports/love.sh
```
- An editor should open
- Use the cursor keys to navigate to the line
```
hg clone https://bitbucket.org/rude/love "$md_build"
```
- Change it to read
```
hg clone https://bitbucket.org/rude/love/#0.10.2 "$md_build"
```
- Press CTRL-x and then y to save the changes
- Enter ```sudo reboot``` to restart Emulationstation
- In Emulationstation, select Retropie -> Retropie Setup
- In the Retropie Setup menu, select Manage Packages -> Optional Packages
- In the list of optional packages, select love
- Select "Install from source" (if Love is already installed, select 'uninstall' first and then 'install from source')
- Love 0.10.2 is now being downloaded and installed automatically. This takes a while.
- Perform a reboot once installation is done
- Emulationstation should now show Love as a selection, and the pre-installed Love game Mari0 should now work without errors.