***
![gb](https://cloud.githubusercontent.com/assets/10035308/12191785/d743f5e4-b595-11e5-98dd-ca2ec58a1769.png)
***
_The Game Boy was released by Nintendo in 1989 thus kicking off the era of handheld gaming and Pokemon._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-gambatte](https://github.com/libretro/gambatte-libretro) | gb  | .gb .zip | none | /opt/retropie/configs/gb/retroarch.cfg |
| [lr-tgbdual](https://github.com/libretro/tgbdual-libretro) | gb  | .gb .zip | none | /opt/retropie/configs/gb/retroarch.cfg |

## Emulator: [lr-gambatte](https://github.com/libretro/gambatte-libretro)

lr-gambatte is a libretro port of Gambatte that utilises RetroArch configurations for your controller

## ROMS

Accepted File Extensions: **.gb**

Place your Game Boy ROMs in
```
/home/pi/RetroPie/roms/gb
```
## Controls

lr-gambatte utilises Retroarch configurations

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

## How to add a custom palette

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


## Emulator: [lr-tgbdual](https://github.com/libretro/tgbdual-libretro)

lr-tgbdual is a libretro port of TGB Dual that utilises RetroArch configurations for your controllers
## ROMS

Accepted File Extensions: **.gb**

Place your Game Boy ROMs in
```
/home/pi/RetroPie/roms/gb
```
## Controls

lr-tgbdual utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/gb/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

## Com Link

Once a ROM is launched with lr-tgbdual, two synced game screens will be displayed side-by-side by default. Player one is then able to control the left screen, while player two controls the right.