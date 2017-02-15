***
![videopac](https://cloud.githubusercontent.com/assets/10035308/12212914/3db2135a-b62d-11e5-8bc8-314eef1f117f.png)
![odyssey2](https://cloud.githubusercontent.com/assets/10035308/12213667/802575ea-b639-11e5-837d-354e3f6be631.png)
***
_The Magnavox Odyssey2 known in Europe as the Philips Videopac G7000 (and a bunch of other names a bunch of other places) is a home video game console released in 1978. One of the earliest gaming consoles, it is one of the least known today. Games are quite similar in detail to that of Atari 2600... except worse._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-o2em](https://github.com/libretro/libretro-o2em) | videopac  | .bin | o2rom.bin | /opt/retropie/configs/videopac/retroarch.cfg |

## Emulator: [lr-o2em](https://github.com/libretro/libretro-o2em)

## ROMS: 

Accepted File Extensions: **.bin**

Place your ROMs here:
```
/home/pi/RetroPie/roms/videopac
```

## BIOS

The BIOS file required is **o2rom.bin**

Place your BIOS in
```
/home/pi/RetroPie/BIOS
```

## Controls

Really it says it uses Retroarch configurations and some gamepads work but for almost all of your games you will need a keyboard. Typically you will press 1 to start a game- for people who grew up in the 70's controls might be more intuitive, but they can be tricky to figure out as they change for each game...

lr-o2em utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/videopac/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![philips_videopac](https://cloud.githubusercontent.com/assets/10035308/8192731/79eeaea2-142d-11e5-924d-9d284d280981.png)

### Switching Emulation Station to the Odyssey² logo:

If you are from the United States it is likely that you had the Odyssey² rather than the Videopac. If you want EmulationStation to show the Odyssey² graphics instead of Videopac then you should create a file `/opt/retropie/configs/all/platforms.cfg` with the following contents (note this requires at least v4.1.6 of the RetroPie-Setup script).

```
videopac_theme="odyssey2"
videopac_platform="odyssey2"
```

Once this is done, please update the currently installed Videopac emulator from RetroPie-Setup and Emulation Station will now use the Odyssey² logo. Scraping from within Emulation Station should also return Odyssey² artwork.