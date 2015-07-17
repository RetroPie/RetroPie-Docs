![Dreamcast Logo](http://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Dreamcast_logo.svg/320px-Dreamcast_logo.svg.png)
***
_The Sega Dreamcast is a 6th generation home video game console released by Sega in 1998. It is notably the last console that Sega produced._
***
## Emulator: [Reicast](https://github.com/reicast/reicast-emulator) (NOTE: EXPERIMENTAL!)

You'll download this from the experimental section of the setup script. it is very laggy and buggy, but some games work great (See small list below). Pi 2 is required.  

Audio is choppy and not great, and degrades the longer the emulator is in use.  Restarting the emulator (and ultimately the Pi) may become a good idea after a couple hours of gameplay.  (There is a memory leak somewhere in the Reicast code)

### Game compatibility list

* San Francisco Rush 2049 = Totally playable 1player, full speed most times (except particle effects)!  Split-screen multiplayer bounds rendered incorrectly :(
* Marvel Vs Capcom 1 = Totally playable multiplayer, full speed!
* Marvel Vs Capcom 2 = Totally playable multiplayer, almost full speed!
* Coaster Works = Totally playable except when utilizing 4-split view to edit a track (split-screen bounds rendered incorrectly, all overlaid)


#### Games not working so well

* Gauntlet Legends = Not playable, rendering blanks out every other frame and may cause epilepsy; wouldn't recommend it just yet



## ROMS

Accepted File Extensions: **.cdi .gdi** 

Place your Dreamcast ROMs in
```
/home/pi/RetroPie/roms/dreamcast
```

## BIOS

The BIOS files needed are: **dc_boot.bin, dc_flash.bin**

Place your BIOS files in
```
/home/pi/RetroPie/BIOS
```
for older versions place BIOS files in
```
/home/pi/.reicast/data/
```

## VMUs

VMUs are stored as .BIN files under `/home/pi/.reicast/`, and will be automatically created the first time you run Reicast without VMU files.  

On occasion, these VMUs do not get formatted quite right during creation, and the Dreamcast can't save or load data from them.  They just need to be reformatted -- run the `SYSTEMMANAGER` entry in the EmulationStation Dreamcast menu (coming soon from [Pull Request #862](https://github.com/petrockblog/RetroPie-Setup/pull/862)) and / or see [this post](http://blog.petrockblock.com/forums/topic/configuring-controllers-in-reicast/page/2/#post-99715) for details.

## Controls

Controls can be mapped via the `/home/pi/.reicast/emu.cfg` file.  An example mapping for a PS3 controller is below for reference:

```
[PLAYSTATION(R)3 Controller]
button.0=Btn_Z
button.1=Btn_C
button.2=Btn_D
button.3=Btn_Start
button.4=DPad_Up
button.5=DPad_Right
button.6=DPad_Down
button.7=DPad_Left
button.8=Axis_LT
button.9=Axis_RT
button.10=DPad2_Left
button.11=DPad2_Right
button.12=Btn_Y
button.13=Btn_B
button.14=Btn_A
button.15=Btn_X
button.16=Quit
axis.0=Axis_X
axis.1=Axis_Y
```

Press ctrl+c to exit- Or map a Quit button as shown above :D 

