***
![dreamcast](https://cloud.githubusercontent.com/assets/10035308/12191302/2612a414-b590-11e5-82e3-f39acc38eb71.png)
***
_The Sega Dreamcast is a 6th generation home video game console released by Sega in 1998. It is notably the last console that Sega produced._
***
## Emulator: [Reicast](https://github.com/reicast/reicast-emulator) 

It can be very laggy and buggy, but some games work great (see compatibility list below). Pi 2 is required.  

Audio is choppy and not great, and degrades the longer the emulator is in use.  Restarting the emulator (and ultimately the Pi) may become a good idea after a couple hours of gameplay. There is a memory leak somewhere in the Reicast code. Low screen resolution are recommended to get best performance. Performance suffers if HD resolutions are used.   

## ROMS

Accepted File Extensions: **.cdi .gdi** 

Place your Dreamcast ROMs in
```
/home/pi/RetroPie/roms/dreamcast
```

[**DREAMCAST COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1AD91IcudqHP7dDmEXLO25Pzb85uUgAy4chU2QxlZBQk/edit?usp=sharing) feel free to contribute to the list.

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

## Video Setup Guide  

<a href="https://www.youtube.com/watch?v=yAB0_kkaa5s
" target="_blank"><img src="https://i.ytimg.com/vi_webp/yAB0_kkaa5s/mqdefault.webp" 
alt="RetroPie Dreamcast emulation" width="300" height="190" border="10" /></a>  


## VMUs

VMUs are stored as .BIN files under `/home/pi/.reicast/`, and will be automatically created the first time you run Reicast without VMU files.  

On occasion, these VMUs do not get formatted quite right during creation, and the Dreamcast can't save or load data from them.  They just need to be reformatted -- run the `SYSTEMMANAGER` entry in the EmulationStation Dreamcast menu and / or see [this post](http://blog.petrockblock.com/forums/topic/configuring-controllers-in-reicast/page/2/#post-99715) for details.

## Controls
Starting with RetroPie 3.3 controls for the Dreamcast Emulator are automatically configured when you configure your controls through emulationstation.

![sega_dreamcast_diagram](https://cloud.githubusercontent.com/assets/10035308/11432087/ae992b58-9463-11e5-928e-1ff3689c421d.png)

Controls can be mapped via the `/home/pi/.reicast/emu.cfg` file. An example mapping for a PS3 controller is below for reference:

**PlayStation 3 Controller**

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
If mapping is not working correctly try changing controller name for: 
```
[Sony PLAYSTATION(R)3 Controller]
```
For Wireless PS3 Controller use: 
```
[PLAYSTATION(R)3 Controller (xx:xx:xx:xx:xx:xx)]
```
Replace xx:xx:xx:xx:xx:xx with your own controller mac address

Press ctrl+c to exit- Or map a Quit button (PS) as shown above :D 


**Xbox 360 Controller:**

```
[emulator]
mapping_name = Xbox Gamepad (userspace driver)
btn_escape = 0x13a

[dreamcast]
btn_a = 0x130h
btn_b = 0x131h
btn_c = 
btn_d = 0x139h
btn_x = 0x133h
btn_y = 0x134h
btn_z = 0x138h
btn_start = 0x13Bh
axis_x = 0x00
axis_y = 0x01
axis_trigger_left = 0x0a
axis_trigger_right = 0x09

[compat]
axis_dpad1_x = 0x10
axis_dpad1_y = 0x11
```

**iBuffalo USB controller** 

```
button.0=Btn_B
button.1=Btn_A
button.2=Btn_Y
button.3=Btn_X
button.4=DPad2_Left
button.5=DPad2_Right
button.6=Quit
button.7=Btn_Start
axis.0=Axis_X
axis.1=Axis_Y
```