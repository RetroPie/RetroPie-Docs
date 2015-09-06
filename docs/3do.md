![](http://vignette3.wikia.nocookie.net/retroconsoles/images/7/74/R.E.A.L_3DO_Interactive_Multiplayer_logo.png/revision/latest?cb=20130607161233)
***
_The Panasonic 3do Real Multiplayer was a Home Video Game Console developed by the 3do company in 1994_

***
## Emulator: [lr-4do](https://github.com/libretro/4do-libretro) (EXPERIMENTAL)

Note that this is experimental- even with an overclocked RPi2 it was incredibly laggy and slow. Definitely won't be coming out of experimental any time soon. It can be installed from the experimental menu of the setup script.

## ROMS
Accepted File Extensions: **.iso**

Place your 3do ROMs in
```
/home/pi/RetroPie/roms/3do
```
## BIOS

The file needed is **panafz10.bin**

Place your panafz10.bin BIOS file in
```
/home/pi/RetroPie/BIOS
```
## Controls

lr-4do utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/3do/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![3dodiagram](https://cloud.githubusercontent.com/assets/10035308/8237801/0ae4d6fc-15af-11e5-803f-8ba408d48362.png)