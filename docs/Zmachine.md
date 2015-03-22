![Infocom](http://terpconnect.umd.edu/~molivier/infocom.jpg)
***
_Infocom created a bunch of text based adventure games to be utilised by a Z-Machine interpreter (i.e. an emulator). Notable titles include the Zork Series and The Hitchhikers Guide to the Galaxy._

***
## Emulator: [Frotz](http://frotz.sourceforge.net/)

## ROMS
Accepted File Extensions: **.z3 .DAT**

Place your Infocom interactive fiction ROMs in 
```
/home/pi/RetroPie/roms/zmachine
```

## Controls

By default 3 versions of Zork are already in the Z-Machine ROM folder

```
/home/pi/RetroPie/roms/zmachine/zork1/DATA/ZORK1.DAT

/home/pi/RetroPie/roms/zmachine/zork2/DATA/ZORK2.DAT

/home/pi/RetroPie/roms/zmachine/zork3/DATA/ZORK3.DAT
```
in order to play them you go into the terminal and type:
```
frotz /home/pi/RetroPie/roms/zmachine/zork1/DATA/ZORK1.DAT

frotz /home/pi/RetroPie/roms/zmachine/zork2/DATA/ZORK2.DAT

frotz /home/pi/RetroPie/roms/zmachine/zork3/DATA/ZORK3.DAT
```
Follow the onscreen instructions and type responses- So for example it narrates that it is dark- in turn you type "light" (without quotations) and then it will progress in the story. 

It's a very different type of gameplay than typical gaming systems in that by design it uses an emulator rather than a console and the fact that it is more of an interactive storybook than it is a video game.

if you get tired of the story:

-to quit type: quit

and it will take you back to the terminal. 

As far as it stands right now this isn't integrated by default in EmulationStation but it sure should be!

If you want it added to Emulationstation, Follow these steps in this post:

http://blog.petrockblock.com/forums/topic/zmachine-not-working-when-booted-from-emulationstation/#post-92307