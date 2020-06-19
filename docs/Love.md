***
![](https://love2d.org/style/logo.png)
***
_Löve is a 2d game engine programmed primarily in lua._
***
## Emulator [Löve](https://bitbucket.org/rude/love/src) (Experimental)

It only really works well on a Raspberry Pi 2. Games are programmed for different versions of Löve. RetroPie uses Love 11.1 and so it is likely a lot of games will not work because they have not been updated for version 11.1. See the section "Versions" below for step by step instruction how to install the older version 0.10.2 of Löve.

## ROMS

Accepted File Extensions: **.love**

Place your Löve games in

```
/home/pi/RetroPie/roms/love/
```

Note that love games are basically .zip files with a .love extension instead of a .zip, so when building LÖVE files from repos, the files all need to be in the top level directory (especially main.lua)
(If you are an advanced user you can edit these files to change things like the game resolution, gampad/keyboard mappings, or add gamepad support

## Controls

Controls vary by game though most will need a keyboard. [**Mari0**](http://stabyourself.net/mari0/) (which is installed when you install Löve) has some support for gamepads but you still need to use a keyboard to navigate the menus.

## Display
For display it is best to leave the video settings alone in the runcommand menu and just use the in game settings to scale it to 5.

If the games you are playing are not scaled correctly and the in-game video options don't work (or don't exist) then adjust the resolution with the runcommand menu.

## Other Games

* [Itch.io](https://itch.io/games/tag-love2d) games created with Löve

### Full gamepad support
* [**Mr. Rescue**](http://tangramgames.dk/games/mrrescue/), download [here](https://github.com/SimonLarsen/mrrescue/releases/download/1.02e/mrrescue1.02e.love) 

* [**Duck Marines**](http://tangramgames.dk/games/duckmarines/), download [here](https://github.com/SimonLarsen/duckmarines/releases/download/v1.0c/duckmarines-1.0c.love")

* [**Curse of the Arrow**](https://egordorichev.itch.io/curse-of-the-arrow/), download [here](https://egordorichev.itch.io/curse-of-the-arrow/purchase")

### Keyboard/Mouse Only

* [**Sienna**](http://tangramgames.dk/games/sienna/), download [here](https://github.com/SimonLarsen/sienna/releases/download/v1.0d/sienna-1.0d.love)

* [**90 Second Portraits**](http://tangramgames.dk/games/90secondportraits/), download [here](https://github.com/SimonLarsen/90-Second-Portraits/releases/download/1.01b/90secondportraits-1.01b.love)

## Versions

The default behavior of RetroPie is to always install the latest version of Löve. Currently, this is v11. However, most games are written for v10. 

In order to get other games to work, it is necessary to install Löve v10, which is available as the `love-0.10.2` package from RetroPie-Setup. After installing it, use the [runcommand launch menu](Runcommand.md#runcommand-launch-menu) to choose the version of Löve required to run a game.