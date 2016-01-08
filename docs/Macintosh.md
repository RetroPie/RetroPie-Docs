***
![macintosh](https://cloud.githubusercontent.com/assets/10035308/12192521/6b03d7d0-b59c-11e5-970e-b317595478bb.png)
***
_The Apple Macintosh, later renamed the Macintosh 128K, was a personal computer released in 1984._
***

## Emulator: [BasiliskII](http://basilisk.cebix.net/)

Prerequisites:
Make sure you have the latest version of the retropie-setup script and binaries/source build of basilisk.

Make sure you have the latest emulationstation config for it also by running

```
sudo ./retropie_packages basilisk configure
```

## ROMS
Accepted File Extensions: **.img .rom  (.dsk?, .sit?)**

Place your Macintosh ROMs in
```
/home/pi/RetroPie/roms/macintosh
```

## BIOS
To start up your mac you need two main files: 

**mac.rom** (can be renamed from PERFORMA.ROM)

**disk.img** (can be renamed from MacStartup.img)

You will also place these files in
```
/home/pi/RetroPie/roms/macintosh
```
For more details see the forum post at http://blog.petrockblock.com/forums/topic/installing-basiliskii-an-early-macintosh-emulator/ and the links therein for detailed instructions about how to set up Basilisk II.

There is also detailed information along with roms and a startup disk image at http://www.redundantrobot.com/sheepshaver-tutorial/

## Controls

a keyboard and a mouse

Ctrl + Escape will exit the emulator
