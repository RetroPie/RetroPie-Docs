***
![virtualboy](https://cloud.githubusercontent.com/assets/10035308/12214017/8fcf5e08-b642-11e5-8ee6-7ee08f23c5c1.png)
***
_The Virtual Boy was Nintendo's attempt at virtual reality in 1995 and it was a horrid commercial failure._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-beetle-vb](https://github.com/libretro/beetle-vb-libretro) | virtualboy  | .7z .vb .zip | none | /opt/retropie/configs/virtualboy/retroarch.cfg |

## Emulator: [lr-beetle-vb](https://github.com/libretro/beetle-vb-libretro) 

## ROMS
Accepted File Extension: **.7z .vb .zip**

Place your Virtual Boy ROMs in 
```
/home/pi/RetroPie/roms/virtualboy
```

## Controls

### Game Specific Control Information

If you have a limited input method such as an snes-style controller or handheld, then the spreadsheet below will help you figure out which games you will be able to play.

[Virtual Boy - General Game Info](https://docs.google.com/spreadsheets/d/1Om4WsHFk7y5xyc2HMFH3IRUclgkRG4XSe452yiJbykk/edit?usp=sharing)

>If you want to improve the spreadsheet, then request editing permission and you will be approved in a timely manner.

### lr-beetle-vb Controls

lr-beetle-vb utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/virtualboy/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nintendo_virtualboy_diagram](https://cloud.githubusercontent.com/assets/10035308/16599637/7f382d3a-42c0-11e6-8e7d-bdbacf7afd82.png)

## Enabling Right D-Pad to Right Analog Stick

Just go to the Options in the Quick Menu and enable "Right analog to digital". If the option isn't in the menu, then update lr-beetle-vb.

For a closer replication of the Virtual Boy's unique dual d-pad input, you may also want to toggle the left d-pad to the left analog stick in Controls.