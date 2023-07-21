***
![gb](https://cloud.githubusercontent.com/assets/10035308/12191785/d743f5e4-b595-11e5-98dd-ca2ec58a1769.png)
***
_The Game Boy was released by Nintendo in 1989 thus kicking off the era of handheld gaming and Pokemon._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-gambatte](https://github.com/libretro/gambatte-libretro) | gb  | .7z .gb .zip | gb_bios.bin (optional)| /opt/retropie/configs/gb/retroarch.cfg |
| [lr-tgbdual](https://github.com/libretro/tgbdual-libretro) | gb  | .7z .gb .zip | none | /opt/retropie/configs/gb/retroarch.cfg |
| [lr-mgba](https://github.com/libretro/mgba) | gb  | .7z .gb .zip | gb_bios.bin (optional), sgb_bios.bin (optional) | /opt/retropie/configs/gb/retroarch.cfg |

## Emulators: [lr-gambatte](https://github.com/libretro/gambatte-libretro), [lr-tgbdual](https://github.com/libretro/tgbdual-libretro), [lr-mgba](https://github.com/libretro/mgba)

lr-gambatte is the preferred single-player emulator, while lr-tgbdual runs two instances of the same game for either two-player link cable games or parallel play on the same system.
lr-gambatte supports playing link cable games over network (not to be mixed up with netplay).

lr-mgba is a modern emulator that aims to be fast and accurate, supports local cable games, external BIOS, Super Game Boy emulation, among many other features. It also emulates [[Game Boy Color]] and [[Game Boy Advance]].

## ROMS

Accepted File Extensions: **.7z .gb .zip**

Place your Game Boy ROMs in
```
/home/pi/RetroPie/roms/gb
```

## BIOS
lr-gambatte can load external BIOS for Game Boy (**gb_bios.bin**).

lr-mgba can load external BIOS for Game Boy (**gb_bios.bin**) and Super Game Boy (**sgb_bios.bin**).

Place these BIOS in
```
/home/pi/RetroPie/BIOS
```

The correct MD5 for **gb_bios.bin** is `32fbbd84168d3482956eb3c5051637f5`and for **sgb_bios.bin** is `d574d4f9c12f305074798f54c091a8b4`

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

Get to the command line with F4 or [SSH](SSH), change directory to the Game Boy folder, and look at the save files:

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

## Changing colour palette

Change the **Core Option** for **GB Colorization** to **Internal** and then change **Internal Palette* to your preference. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

## Custom Palettes

You may also add custom palettes by adding your new .pal file to 
~~~
/home/pi/RetroPie/BIOS/palettes
~~~ 
To select, change the **Core Option** for **GB Colorization** to **custom**. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

You can define different palettes for specific games by creating a .pal file in the "palettes" folder with "INTERNALROMNAME.pal" or "rom-name.pal". If no specific palette is found for a ROM then the default palette is used.

## Two-player link cable games

### Using _lr-tgbdual_

To play two-player link cable games with _lr-tgbdual_, turn on the **Link cable emulation** option from the [Core Options](RetroArch-Core-Options#setting-core-options) and restart the game. Two synced game screens will be displayed side-by-side by default. Player one is able to control the left screen, while player two controls the right, but the screens can be switched using the **Screen layout** [core option](RetroArch-Core-Options#setting-core-options).

The above configuration will enable playing the same game using link cable emulation, but if two different games need to be linked, the process is a bit more involved and it involves setting up the games through the *Subsystems* RetroArch menu. Here's a rundown of the steps needed:

* Start a Gameboy game using _lr-tgbdual_ (doesn't have to be one of the games linked). Make sure the **Link cable emulation** [core option](RetroArch-Core-Options#setting-core-options) is enabled and the ROM files for the games to be linked are **not** zipped
* Open the RetroArch menu and then press _back_ (mapped to the **B** button) to access the main menu
* Open the _Subsystems_ menu and then choose _Load 2 Player Game Boy Link *_. A file browser menu will open to choose the 1st game ROM file
* Open again the _Susystems_ menu and choose _Load 2 Player Game Boy Link *_. A file browser menu will open to choose the 2nd game ROM file
* Open a 3rd time the _Subsystems_ menu and choose the _Start 2 Player Game Boy Link *_ option. This will start restart the core with the 2 ROM files loaded side-by-side with link cable emulation enabled

### Using _lr-gambatte_
To play two-player link cable games with lr-gambatte, two RetroPie systems in the same network are needed.
Change the following **Core Options** to the values below (see [Setting Core Options](RetroArch-Core-Options#setting-core-options)):

System 1 (Server, e.g. 192.168.0.1):

| Core Option | Value |
| :---: | :---: |
| gambatte_gb_link_mode | Network Server |
| gambatte_gb_link_network_port | 56400 |

System 2 (Client):

| Core Option | Value |
| :---: | :---: |
| gambatte_gb_link_mode | Network Client |
| gambatte_gb_link_network_port | 56400 |
| gambatte_gb_link_network_server_ip_1| 1 |
| gambatte_gb_link_network_server_ip_2| 9 |
| gambatte_gb_link_network_server_ip_3| 2 |
| gambatte_gb_link_network_server_ip_4| 1 |
| gambatte_gb_link_network_server_ip_5| 6 |
| gambatte_gb_link_network_server_ip_6| 8 |
| gambatte_gb_link_network_server_ip_7| 0 |
| gambatte_gb_link_network_server_ip_8| 0 |
| gambatte_gb_link_network_server_ip_9| 0 |
| gambatte_gb_link_network_server_ip_10| 0 |
| gambatte_gb_link_network_server_ip_11| 0 |
| gambatte_gb_link_network_server_ip_12| 1 |

For older versions of lr-gambatte use this config parameters: 

System 1 (Server, e.g. 192.168.0.1):

| Core Option | Value |
| :---: | :---: |
| Link Mode | Network Server |
| Network Port | 56400 |
| Network Server IP Octet1 | 0 |
| Network Server IP Octet2 | 0 |
| Network Server IP Octet3 | 0 |
| Network Server IP Octet4 | 0 |

System 2 (Client):

| Core Option | Value |
| :---: | :---: |
| Link Mode | Network Client |
| Network Port | 56400 |
| Network Server IP Octet1 | 192 |
| Network Server IP Octet2 | 168 |
| Network Server IP Octet3 | 0 |
| Network Server IP Octet4 | 1 |

To begin the network game first start the game on system 1 and then join system 2.
