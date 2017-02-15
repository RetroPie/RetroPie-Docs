***
![z-machine](https://cloud.githubusercontent.com/assets/10035308/12212915/3dbf6b90-b62d-11e5-8f13-0b1a61bcbdf8.png)
***
_Infocom created a bunch of text based adventure games to be utilised by a Z-Machine interpreter (i.e. an emulator). Notable titles include the Zork Series and The Hitchhikers Guide to the Galaxy._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Frotz](http://frotz.sourceforge.net/) | zmachine | .dat .zip .z1 .z2 .z3 .z4 .z5 .z6 .z7 .z8 | none | hardcoded |

## Emulator: [Frotz](http://frotz.sourceforge.net/)

## ROMS
Accepted File Extensions: **.dat .zip .z1 .z2 .z3 .z4 .z5 .z6 .z7 .z8**

Place your Infocom interactive fiction ROMs in 
```
/home/pi/RetroPie/roms/zmachine
```

## Controls

It's a very different type of gameplay than typical gaming systems. It is more of an interactive storybook than it is a video game.

By default 3 versions of Zork are already in the Z-Machine ROM folder

Follow the onscreen instructions and type responses- So for example it narrates that it is dark- in turn you type `light` or `turn on light` and then it will progress in the story. 

if you get tired of the story:

to quit type: `quit`

## Larger Font Size

If you are on a high resolution screen and the font size is tiny you can change the framebuffer's resolution using the [runcommand](runcommand) menu to 640x480 and it should make the font more visible.