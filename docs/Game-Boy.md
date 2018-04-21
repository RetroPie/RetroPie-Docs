***
![gb](https://cloud.githubusercontent.com/assets/10035308/12191785/d743f5e4-b595-11e5-98dd-ca2ec58a1769.png)
***
_The Game Boy was released by Nintendo in 1989 thus kicking off the era of handheld gaming and Pokemon._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-gambatte](https://github.com/libretro/gambatte-libretro) | gb  | .7z .gb .zip | none | /opt/retropie/configs/gb/retroarch.cfg |
| [lr-tgbdual](https://github.com/libretro/tgbdual-libretro) | gb  | .7z .gb .zip | none | /opt/retropie/configs/gb/retroarch.cfg |
| [lr-mgba](https://github.com/libretro/mgba) | gb  | .7z .gb .zip | gb_bios.bin | /opt/retropie/configs/gb/retroarch.cfg |

## Emulators: [lr-gambatte](https://github.com/libretro/gambatte-libretro), [lr-tgbdual](https://github.com/libretro/tgbdual-libretro), [lr-mgba](https://github.com/libretro/mgba)

lr-gambatte is the prefered single-player emulator, while lr-tgbdual runs two instances of the same game for either two-player link cable games or parallel play on the same system.
lr-gambatte supports playing link cable games over network (not to be mixed up with netplay).
lr-mgba is a modern emulator that aims to be fast and accurate, supports local cable games, external BIOS, Super Game Boy emulation, among many other features. It also emulates Game Boy Color and Game Boy Advance.

## ROMS

Accepted File Extensions: **.7z .gb .zip**

Place your Game Boy ROMs in
```
/home/pi/RetroPie/roms/gb
```

## BIOS

lr-mgba can load external Game Boy and Super Game Boy BIOSes: **gb_bios.bin**, **sgb_bios.bin**

Place these BIOS in
```
/home/pi/RetroPie/BIOS
```

The correct MD5 for **gb_bios.bin** is `32fbbd84168d3482956eb3c5051637f5` and for **sgb_bios.bin** is `d574d4f9c12f305074798f54c091a8b4`

## Controls

All the emulators utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/gb/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![gameboy](https://cloud.githubusercontent.com/assets/10035308/7334402/bd640072-eb4e-11e4-8251-d2bc3b876153.png)

## Syncing Save Games

For games which can share save games, such as Pokemon Blue and Pokemon Red, it is possible to link one save to the other.

This procedure assumes you have *one* save game. If you've played both games, you'll need to delete one save, it's not possible to combine both after you've played them.

Get to the commandline with F4 or [SSH](ssh), change directory to the Game Boy folder, and look at the save files:

~~~
cd RetroPie/roms/gb
ls *.srm
~~~

You should see your existing save game, for example:

~~~
Pokemon Blue.srm
~~~

If you have two save files, such as:

~~~
Pokemon Blue.srm
Pokemon Red.srm
~~~

Then delete the one you *don't* want to keep:

~~~
rm Pokemon Red.srm
~~~

Now create an "imaginary" save for the other game by creating a symbolic link.

~~~
ln -s "Pokemon Blue.srm" "Pokemon Red.srm"
~~~

The above example takes an existing Blue save and makes an imaginary Red save.

## How to change the color palette

Open the RetroArch RGUI by pressing **Select+X** on the controller, or **Hotkey+F1** on the keyboard then navigate to:

* Quick Menu
    * Core Options
        * Change `GB Colorization` to `internal` by pressing left or right
        * Select an `Internal Palette` with left and right

Press **B** to go back to the Quick Menu and **Resume Content**.

To make the change permanent, choose **Save Configuration** on the main RGUI menu.

It's also possible to edit `/opt/retropie/configs/all/retroarch-core-options.cfg` and set the palette like:

~~~
gambatte_gb_colorization = "internal"
gambatte_gb_internal_palette = "GBC - Grayscale"
~~~

The complete list of palettes can be found in the emulator core source:

~~~
GBC - Blue
GBC - Brown
GBC - Dark Blue
GBC - Dark Brown
GBC - Dark Green
GBC - Grayscale
GBC - Green
GBC - Inverted
GBC - Orange
GBC - Pastel Mix
GBC - Red
GBC - Yellow
Special 1
Special 2
Special 3
~~~

https://github.com/libretro/gambatte-libretro/blob/master/libgambatte/libretro/libretro.cpp

## How to Add a Custom Palette

You may also add custom palettes by adding your new .pal file to 
~~~
/home/pi/RetroPie/BIOS/palettes
~~~ 
Set the following value in `/opt/retropie/configs/all/retroarch-core-options.cfg` gambatte_gb_colorization = "custom"

You can define different palettes for specific games by creating a .pal file in the "palettes" folder with "INTERNALROMNAME.pal" or "rom-name.pal". If no specific palette is found for a ROM then the default palette is used.

You may also use the Retroarch RGUI to accomplish this as well by following the steps below once you have added a custom palette. 

Open the RetroArch RGUI by pressing **Select+X** on the controller, or **Hotkey+F1** on the keyboard then navigate to:

* Quick Menu
    * Core Options
        * Change `GB Colorization` to `custom` by pressing left or right
        * Select an `Internal Palette` with left and right

Press **B** to go back to the Quick Menu and **Resume Content**.

To make the change permanent, choose **Save Configuration** on the main RGUI menu.

## Playing two-player link cable games

To play two-player link cable games with lr-tgbdual no further configuration needs to be done. The only thing needed of course are two controllers. Two synced game screens will be displayed side-by-side by default. Player one is able to control the left screen, while player two controls the right.

To play two-player link cable games with lr-gambatte, two RetroPie systems in the same network are needed.
Make the following changes to `/opt/retropie/configs/all/retroarch-core-options.cfg` :

System 1 (Server, e.g. 192.168.0.1):
~~~
gambatte_gb_link_mode = "Network Server"
gambatte_gb_link_network_port = "56400"
gambatte_gb_link_network_server_ip_octet1 = "0"
gambatte_gb_link_network_server_ip_octet2 = "0"
gambatte_gb_link_network_server_ip_octet3 = "0"
gambatte_gb_link_network_server_ip_octet4 = "0"
~~~

System 2 (Client):
~~~
gambatte_gb_link_mode = "Network Client"
gambatte_gb_link_network_port = "56400"
gambatte_gb_link_network_server_ip_octet1 = "192"
gambatte_gb_link_network_server_ip_octet2 = "168"
gambatte_gb_link_network_server_ip_octet3 = "0"
gambatte_gb_link_network_server_ip_octet4 = "1"
~~~
To begin the network game first start the game on system 1 and then join system 2.