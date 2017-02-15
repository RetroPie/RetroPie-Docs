***

![3do right](https://cloud.githubusercontent.com/assets/10035308/12186059/8d7ec76a-b55c-11e5-9231-b0c561de271c.png)

***
_The Panasonic 3do Real Multiplayer was a Home Video Game Console developed by the 3do company in 1994_

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-4do](https://github.com/libretro/4do-libretro) | 3do  | .iso | panafz10.bin | /opt/retropie/configs/3do/retroarch.cfg |

## Emulator: [lr-4do](https://github.com/libretro/4do-libretro)

Note that this is experimental- even with an overclocked RPi2 it was incredibly laggy and slow. Definitely won't be coming out of experimental any time soon. It can be installed from the experimental menu of the [RetroPie Setup Script](Updating RetroPie).

With RPi3 (stock and overclocked) no real difference in performance compared to the RPi2. Bust-A-Move took around 1 minute to load on stock speed and 39 seconds overclocked. Both had choppy sound and controller lag. As of 8/6/2016.

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
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![goldstar_3do_diagram](https://cloud.githubusercontent.com/assets/10035308/16599643/7f450bd6-42c0-11e6-84d7-9cc0944e7b01.png)