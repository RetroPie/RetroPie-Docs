***
![dreamcast](https://cloud.githubusercontent.com/assets/10035308/12191302/2612a414-b590-11e5-82e3-f39acc38eb71.png)
***
_The Sega Dreamcast is a 6th generation home video game console released by Sega in 1998. It is notably the last console that Sega produced._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Reicast](https://github.com/reicast/reicast-emulator) | dreamcast  | .cdi .chd .gdi | dc_boot.bin, dc_flash.bin | /opt/retropie/configs/dreamcast/mappings |

## Emulator: [Reicast](https://github.com/reicast/reicast-emulator) 

It can be very laggy and buggy, but some games work great (see compatibility list below). Pi 2 is required.  

Audio is choppy and not great, and degrades the longer the emulator is in use.  Restarting the emulator (and ultimately the Pi) may become a good idea after a couple hours of gameplay. There is a memory leak somewhere in the Reicast code. Low screen resolution are recommended to get best performance. Performance suffers if HD resolutions are used.   

## ROMS

Accepted File Extensions: **.cdi .chd .gdi** 

Place your Dreamcast ROMs in
```
/home/pi/RetroPie/roms/dreamcast
```

[**DREAMCAST COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1AD91IcudqHP7dDmEXLO25Pzb85uUgAy4chU2QxlZBQk/edit?usp=sharing) feel free to contribute to the list.

## CHD Archive Usage

Reicast has support for the CHD archive format, but its support is currently only for CHD V4. The problem with CHD V4 is that its compression for ".gdi" is not lossless, which is what CHD V5 addressed.

The reasons you would want to use CHD isn't just for saving space, but also because you can put the CHD compressed ROMs in the "dreamcast" folder instead of putting the GDI and its accompanying files in individual folders within the "dreamcast" folder due to Reicast's strict track naming requirements.

If you don't mind the ROMs being altered permanently or will keep backups of the original ROMs, then all you need to do is have your Dreamcast GDI ROMs (uncompress them if they are in the ".rar", ".7z", or ".zip" archive formats) in individual folders within a folder, download [THIS](https://drive.google.com/file/d/1cBtH3lI--VXtTyJ6k-q1yE7DmOYG333v/view?usp=sharing) archive containing "Dreamcast GDI to CHD", run Dreamcast GDI to CHD.exe to select a ROM's folder as a source and set the destination to wherever you want, then repeat the process for every other ROM you want in the CHD format.

## BIOS

The BIOS files needed are: **dc_boot.bin, dc_flash.bin**. The boot file is often found named something else, such as dc_**bios**.bin. It must be renamed to dc_**boot**.bin when placed in the BIOS folder.

Place your BIOS files in
```
/home/pi/RetroPie/BIOS/dc
```

BIOS files

| File | Region | md5sum | CRC32 | Comment |
| :--: | :--: | :--: | :--: | :--: |
| dc_boot.bin | World | e10c53c2f8b90bab96ead2d368858623 | 89f2b1a1 | |
| dc_flash.bin | USA | 0a93f7940c455905bea6e392dfde92a4 | c611b498 | |
| dc_flash.bin | Europe | 23df18aa53c8b30784cd9a84e061d008 | b7e5aeeb | |
| dc_flash.bin | Japan | 69c036adfca4ebea0b0c6fa4acfc8538 | 5f92bf76 | |
| dc_boot.bin | Free | d407fcf70b56acb84b8c77c93b0e5327 | 61d5613f | Hack |
| dc_flash.bin | Free | 93a9766f14159b403178ac77417c6b68 | e0d202a2 | Hack |
| dc_boot.bin | Free | d552d8b577faa079e580659cd3517f86 | 558f456e | atreyu187 Hack |
| dc_flash.bin | Free | 74e3f69c2bb92bc1fc5d9a53dcf6ffe2 | bda0e9aa | atreyu187 Hack |

**Note:** If you are having trouble with having to set the date/time every time you load Reicast, [see this forum post](https://retropie.org.uk/forum/post/53941) for a guide on how to replace dc_flash.bin. The MD5 of the dc_flash.bin generated from that guide should be `2f818338f47701c606ade664a3e16a8a`

## Video Setup Guide  

<a href="https://www.youtube.com/watch?v=yAB0_kkaa5s
" target="_blank"><img src="https://i.ytimg.com/vi_webp/yAB0_kkaa5s/mqdefault.webp" 
alt="RetroPie Dreamcast emulation" width="300" height="190" border="10" /></a>  

RetroPie 4.0 uses an output resolution independent render resolution of 640x480. Open `/home/pi/.reicast/emu.cfg` to modify render resolution.

## Tweaks

```
/opt/retropie/configs/all/autoconf.cfg
```
Option | Description | Value
--- | --- | ---
reicast_input | enable input auto configuration | (0/1)

## VMUs

VMUs are stored as .BIN files under `/home/pi/.reicast/`, and will be automatically created the first time you run Reicast without VMU files.  

On occasion, these VMUs do not get formatted quite right during creation, and the Dreamcast can't save or load data from them.  They just need to be reformatted -- run the `SYSTEMMANAGER` entry in the EmulationStation Dreamcast menu and / or see [this post](http://blog.petrockblock.com/forums/topic/configuring-controllers-in-reicast/page/2/#post-99715) for details. 

A Dreamcast soft-reset (A+B+X+Y+Start buttons at the same time) at the ROM's title screen will also take you into the Dreamcast BIOS to manage the VMU's. After formatting VMU's, exit the emulator and restart. Pressing 'Play' will cause Reicast to crash.

## Controls
Starting with RetroPie 3.3 controls for the Dreamcast Emulator are automatically configured when you configure your controls through emulationstation.
Please notice that you may be interested in disabled the input auto config ( described above ) in case of any autoconfig issue.

![sega_dreamcast_diagram](https://cloud.githubusercontent.com/assets/10035308/16599638/7f411634-42c0-11e6-811c-456f02b2ea47.png)

Controls can be mapped via the `/home/pi/.reicast/emu.cfg` file. Make sure that evdev_device_id_1 & evdev_device_id_2 are set to the corresponding controller's /dev/input/event* number you want to use. A -1 means no controller which we will use for player 3 and 4. Then have evdev_mapping_1 & evdev_mapping_2 point to the matching controller mapping configuration files and both can either point to the same file or different files if you want to use 2 different controllers types.

Here is an example of this:

```
[input]
evdev_device_id_1 = 2
evdev_device_id_2 = 3
evdev_device_id_3 = -1
evdev_device_id_4 = -1
evdev_mapping_1 = /opt/retropie/configs/dreamcast/mappings/controller_Xbox360WirelessReceiver(XBOX).cfg
evdev_mapping_2 = /opt/retropie/configs/dreamcast/mappings/controller_8BitdoSNES30GamePad.cfg
joystick_device_id = -1
```

If you want to be able to use 2 controllers at the same time, then you would add this section to the `emu.cfg` file:

```
[players]
nb = 2
```

An example mapping for a PS3 controller is below for reference:

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

**Xbox 360 Wireless Controller using xpad driver:**

```
[emulator]
mapping_name = Xbox 360 Wireless Receiver (XBOX)
btn_escape = 316

[dreamcast]
btn_a = 304
btn_b = 305
btn_c =
btn_d =
btn_x = 307
btn_y = 308
btn_z =
btn_start = 315
btn_dpad1_left =
btn_dpad1_right =
btn_dpad1_up = 704
btn_dpad1_down = 707
btn_dpad2_left =
btn_dpad2_right =
btn_dpad2_up =
btn_dpad2_down =
axis_x = 0
axis_y = 1
axis_trigger_left = 10
axis_trigger_right = 9

[compat]
btn_trigger_left = 312
btn_trigger_right = 313
axis_dpad1_x = 16
axis_dpad1_y = 17
axis_dpad2_x =
axis_dpad2_y =
axis_x_inverted = no
axis_y_inverted = no
axis_trigger_left_inverted =
axis_trigger_right_inverted =
axis_dpad1_y_inverted = no
axis_dpad1_x_inverted = no
```

**PS4 Controller:**

```
[emulator]
mapping_name = Sony Computer Entertainment Wireless Controller
btn_escape = 316

[dreamcast]
btn_a = 305
btn_b = 306
btn_x = 304
btn_y = 307
btn_start = 313
axis_x = 0
axis_y = 1
axis_trigger_left = 3
axis_trigger_right = 4

[compat]
axis_dpad1_x = 16
axis_dpad1_y = 17
axis_x_inverted = no
axis_y_inverted = no
axis_trigger_left_inverted = no
axis_trigger_right_inverted = no
axis_dpad1_y_inverted = no
axis_dpad1_x_inverted = no
```

**Akishop Ps 360+ Joystick**
```
[emulator]
mapping_name = Akishop Customs PS360+ v1.66
btn_escape = 316

[dreamcast]
btn_a = 306
btn_b = 305
btn_x = 307
btn_y = 304
btn_start = 312

[compat]
axis_dpad1_x = 16
axis_dpad1_x_inverted = no
axis_dpad1_y = 17
axis_dpad1_y_inverted = no
btn_trigger_left = 309
btn_trigger_right = 311
```

**8Bitdo NES30 Pro**

Open the configuration file using a text editor, e.g.:
```
sudo nano /opt/retropie/configs/dreamcast/mappings/controller_8BitdoNES30Pro.cfg
```

The content of the file should look like this:

```
[emulator]
mapping_name = 8Bitdo NES30 Pro
btn_escape = 314

[dreamcast]
btn_a = 304
btn_b = 305
btn_c =
btn_d =
btn_x = 307
btn_y = 308
btn_z =
btn_start = 315
btn_dpad1_left =
btn_dpad1_right =
btn_dpad1_up =
btn_dpad1_down =
btn_dpad2_left =
btn_dpad2_right =
btn_dpad2_up =
btn_dpad2_down =
axis_x = 0
axis_y = 1
axis_trigger_left = 24
axis_trigger_right =

[compat]
btn_trigger_left = 310
btn_trigger_right = 311
axis_dpad1_x = 16
axis_dpad1_y = 17
axis_dpad2_x =
axis_dpad2_y =
axis_x_inverted = no
axis_y_inverted = no
axis_trigger_left_inverted =
axis_trigger_right_inverted =
axis_dpad1_y_inverted = no
axis_dpad1_x_inverted = no
```

**iBuffalo Classic USB GamePad [EXPERIMENTAL]** 

```
[emulator]
mapping_name = USB,2-axis 8-button gamepad  
btn_escape = 294

[dreamcast]
btn_a = 288
btn_b = 289
btn_x = 290
btn_y = 291
btn_start = 295
axis_x = 0
axis_y = 1

[compat]
btn_trigger_left = 292
btn_trigger_right = 293
axis_x_inverted = no
axis_y_inverted = no
```
Analog movement not supported

**Mobile Gamepad [EXPERIMENTAL]**
```
[emulator]
mapping_name = MobileGamePad
btn_escape = 0x13a

[dreamcast]
btn_a = 0x130
btn_b = 0x131
btn_c = 0x136
btn_d = 0x137
btn_x = 0x133
btn_y = 0x134
btn_z =
btn_start = 0x13b
btn_dpad1_left =
btn_dpad1_right =
btn_dpad1_up =
btn_dpad1_down =
btn_dpad2_left =
btn_dpad2_right =
btn_dpad2_up =
btn_dpad2_down =
axis_x = 0x00
axis_y = 0x01
axis_trigger_left =
axis_trigger_right =

[compat]
btn_trigger_left = 0x138
btn_trigger_right = 0x139
axis_dpad1_x =
axis_dpad1_y =
axis_dpad2_x =
axis_dpad2_y =
axis_x_inverted = no
axis_y_inverted = no
axis_trigger_left_inverted =
axis_trigger_right_inverted =
```

**Mapping a Nonstandard Controller via @Folly**

run in terminal :
```
cd /opt/retropie/emulators/reicast/bin
```

Here is a script called 'reicast-joyconfig'
run it :
```
./reicast-joyconfig
```

Choose your joystick.
Now you can map your buttons.
When all is done it outputs the text for making a file in `/home/pi/.reicast/mappings`.

It outputs something like this (numbers are in decimals not hexadecimal such as in other contollers' config file):

```
[emulator]
mapping_name = Your Gamepad
btn_escape = 316

[dreamcast]
.......etc
```

Create a file in `/home/pi/.reicast/mappings` called `controller_Your Gamepad.cfg` and paste the text in this file, then modify the `/home/pi/.reicast/emu.cfg` and reference this file in the **`evdev_mapping_1`** (change the number according to the player you want to configure) configuration option.