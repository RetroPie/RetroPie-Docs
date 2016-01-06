![PSP Logo](http://vignette4.wikia.nocookie.net/danganronpa/images/d/df/PSP_Logo.png/revision/latest?cb=20141222033722)

***
_The PlayStation Portable or PSP is a handheld video game system released by Sony in 2004._

***
## Emulators: [lr-ppsspp](https://github.com/libretro/libretro-ppsspp), [ppsspp](https://github.com/hrydgard/ppsspp)

Works best on a Raspberry Pi 2. Lr-ppsspp has the convenience of retroarch controller configs, but standalone ppsspp has the best performance and compatibility.

## ROMS
Accepted File Extensions: **.cso .iso .pbp**

Place your PSP ROMs in 
```
/home/pi/RetroPie/roms/psp
````
#### [**PSP COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1V-MEx1tOXqCcJL1fQzGh9xLHny-qL-PSWqvY7F80Y90/edit?usp=sharing) feel free to contribute!

## Controls

### lr-ppsspp

lr-ppsspp utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/psp/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![psp_diagram](https://cloud.githubusercontent.com/assets/10035308/10719289/b31a8bd0-7b4b-11e5-9374-935630d1ed03.png)

### ppsspp

Controls can be mapped from the main menu under Settings >> Controls >> Control Mapping . To access this, connect a keyboard and press Esc during a game.

