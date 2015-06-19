![Intellivision Logo](http://upload.wikimedia.org/wikipedia/en/a/aa/Intellivision_logo.gif)

***

_The Intellivision is a home video game console released by Mattel in 1979_

***
## Emulator: [jzintv](http://spatula-city.org/~im14u2c/intv/)

## ROMS
Accepted File Extensions: **.int .bin**

Place your Intellivision ROMs in
```
/home/pi/RetroPie/roms/intellivision
```
## BIOS
There are a few BIOS files for the Intellevision. The first two are the main ones you'll probably use.
* Executive ROM: **exec.bin**
* Graphics ROM: **grom.bin**
* Entertainment Computer System ROM: Commonly named ECS.BIN. Required to play ECS games. 
* Intellivoice ROM: Commonly named IVOICE.BIN. Required to play Intellivoice games. 

Place your BIOS files in:
```
/home/pi/RetroPie/BIOS
```
**You should only have to do these steps for older versions of RetroPie:**

According to [this post](http://blog.petrockblock.com/forums/topic/intellivision-emulation/#post-2208):

I put my exec.bin and grom.bin in:
```shell
/usr/local/share/jzintv/rom
```
This is one of the two paths that the emulator is set to look in. The jzintv and subfolder rom did not exist so I had to create them..
```shell
cd /usr/local/share
sudo mkdir jzintv
sudo mkdir jzintv/rom
```
and then I moved the exec.bin and gbrom.bin file from my intellivision rom directory:
```shell
sudo mv ~/RetroPie/roms/intellivision/* /usr/local/share/jzintv/rom
```

Then I was able to launch my intellivision roms… hope this helps!

## Controls:
```shell
Function/Special keys, all maps:
    F1              Quit
    F4              Break into debugger
    F5              Switch to keymap 0 (default keymap)
    F6              Switch to keymap 1 (left controller only for 1 player games)

    F7              Switch to keymap 2 (ECS keyboard keymap)
    F8              Shift to keymap 3 while held (command keys)
    F9              Toggle fullscreen/windowed 
    F10             Toggle movie recording 
    F11             Take screen shot
    F12             Reset emulator
    Pause           Pause the emulator
    PgUp            Increase volume
    PgDn            Decrease volume

Numeric Keypad, maps 0 and 1
    1-9             Left controller 1 - 9
    0               Left controller Clear
    .               Left controller 0
    Enter           Left controller Enter

Main Keyboard, map 0.  (Map 1 just moves right controller mappings to left.)
    0-9             Right controller 0 - 9
    -               Right controller Clear
    =               Right controller Enter
    Left Shift      Right controller top action buttons
    Left Alt        Right controller lower left action button
    Left Control    Right controller lower right action button

    Right Shift     Left controller top action buttons
    Right Alt       Left controller lower left action button
    Right Control   Left controller lower right action button

    Up Arrow        Left controller disc up
    Down Arrow      Left controller disc down
    Left Arrow      Left controller disc left
    Right Arrow     Left controller disc right

Fine-grain directional pad inputs:

    U   I   O
      \ | /
       \|/ 
    J --+-- K      Left controller disc
       /|\
      / | \
    N   M   , 
   
    W   E   R
      \ | /
       \|/ 
    S --+-- D      Right controller disc
       /|\
      / | \
    Z   X   C
```

![intellivision](https://cloud.githubusercontent.com/assets/10035308/8246393/3e98c8c2-15fb-11e5-9398-3f5abd60361b.png)