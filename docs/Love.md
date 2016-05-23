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
    # get mrrescue-1.02d.love (freeware game data)
    if [[ ! -f "$romdir/love/mrrescue-1.02d.love" ]]; then
        wget "https://github.com/SimonLarsen/mrrescue/releases/download/v1.02d/mrrescue-1.02d.love" -O "$romdir/love/mrrescue-1.02d.love"
        chown $user:$user "$romdir/love/mrrescue-1.02d.love"
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

It can be run with

```
cd RetroPie-Setup
sudo ./retropie_packages.sh love configure
```