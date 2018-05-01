***
![psp](https://cloud.githubusercontent.com/assets/10035308/12213680/cebac73c-b639-11e5-84b5-13a5589b1dcd.png)
***
_The PlayStation Portable or PSP is a handheld video game system released by Sony in 2004._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [ppsspp](https://github.com/hrydgard/ppsspp) | psp  | .cso .iso .pbp | none | hardcoded |
| [lr-ppsspp](https://github.com/libretro/libretro-ppsspp) | psp  | .cso .iso .pbp | none | /opt/retropie/configs/psp/retroarch.cfg |

## Emulators: [lr-ppsspp](https://github.com/libretro/libretro-ppsspp), [ppsspp](https://github.com/hrydgard/ppsspp)
Not available for the Raspberry Pi 1. Lr-ppsspp has the convenience of retroarch controller configs, but standalone ppsspp has the best performance and compatibility.

## ROMS
Accepted File Extensions: **.cso .iso .pbp**

Place your PSP ROMs in 
```
/home/pi/RetroPie/roms/psp
```
#### [**PSP COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1V-MEx1tOXqCcJL1fQzGh9xLHny-qL-PSWqvY7F80Y90/edit?usp=sharing) feel free to contribute!

#### [PSP Compatibility List - Overclocked Hardware Edition](https://github.com/RetroPie/RetroPie-Setup/wiki/PSP-Compatibility-List) - Pi 3B+ Testing Needed
This is mostly a selection of PSP games that were tested against an overclocked Raspberry Pi 3B. Upsides of this list over the other are you'll have an easy list of 51 games to look through that will without a doubt run well on your hardware if you are overclocking near or exceeding the provided overclock example and will also know not to bother with a little over 100 other games that will not run well.

## Controls

### lr-ppsspp

lr-ppsspp use Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/psp/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![psp_diagram](https://cloud.githubusercontent.com/assets/10035308/16599632/7f34c9ec-42c0-11e6-8988-0b2d6e795d10.png)

### ppsspp

Controls can be mapped from the main menu under Settings >> Controls >> Control Mapping . To access this, connect a keyboard and press Esc during a game.

## Enhancements

### ppsspp
From the [RetroPie Subreddit](https://www.reddit.com/r/RetroPie/comments/5jieuu/how_to_get_most_psp_games_to_run_beautifully/)

> What I've done so far with a very noticeable difference is set frameskip to 2 (will probably increase this a bit) Turn on auto frameskip (will limit frame skipping to whatever you set for the previous value) then tick Prevent FPS from exceeding 60.
>
> After that you want to change rendering resolution to 2x1, this will make everything look better on bigger screens.
>
> Then you want to goto the audio menu and set Audio Latency to high.


