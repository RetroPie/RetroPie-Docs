***
![macintosh](https://cloud.githubusercontent.com/assets/10035308/12192521/6b03d7d0-b59c-11e5-970e-b317595478bb.png)
***
_The Apple Macintosh, later renamed the Macintosh 128K, was a personal computer released in 1984._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [BasiliskII](http://basilisk.cebix.net/) | macintosh  | .img .rom | mac.rom, disk.img | hardcoded |

## Emulator: [BasiliskII](http://basilisk.cebix.net/)

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

If your **disk.img** file (from MacStartup.img) only has a few MB of free space on it while running the emulator, you must create a new larger one if you want more free space. Since the disk setup GUI is not included in RetroPie's version of Basilisk, you must install Basilisk on your PC to create a larger image and copy your disk.img file to it. Similar instructions can be found at
http://www.emaculation.com/forum/viewtopic.php?f=6&t=8068

Once you have a working disk image large enough to install other software on, you can access other install disk images from the "Unix" icon on the Mac desktop which can access the file system of the Raspberry Pi.

## Controls

a keyboard and a mouse

Ctrl + Escape will exit the emulator
