***
![nes](https://cloud.githubusercontent.com/assets/10035308/12213379/4a0e517a-b634-11e5-98c4-91cc27549706.png)
***
_The Nintendo Entertainment System (NES) is an 8-bit home video game console that was released by Nintendo in 1985. This console officially ended the [video game crash of 1983-1984](https://en.wikipedia.org/wiki/Video_game_crash_of_1983)._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fceumm](https://github.com/libretro/libretro-fceumm) | nes  | .7z .fds .fig .mgd .nes .sfc .smc .swc .zip | disksys.rom | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-nestopia](https://github.com/libretro/nestopia) | nes  | .7z .fds .fig .mgd .nes .sfc .smc .swc .zip | disksys.rom | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-quicknes](https://github.com/libretro/QuickNES_Core) | nes  | .7z .fig .mgd .nes .sfc .smc .swc .zip | none | /opt/retropie/configs/nes/retroarch.cfg |

If you want Famicom Disk System as a seperate system, see the wiki page [HERE](Famicom-Disk-System)

## Emulators: [lr-nestopia](https://github.com/libretro/nestopia), [lr-fceumm](https://github.com/libretro/libretro-fceumm), [lr-quicknes](https://github.com/libretro/QuickNES_Core)

## ROMS

Accepted File Extensions: **.7z .fds .fig .mgd .nes .sfc .smc .swc .zip** - Make sure your roms have headers. Roms without headers will not work. If you want to use PAL roms, make sure they contain `(E)` or `(Europe)` in the filename, or else they may be run at the wrong speed.

Place your NES Roms in
```
/home/pi/RetroPie/roms/nes
```
## BIOS

FDS games require the **disksys.rom** bios file.

Place the BIOS in
```
/home/pi/RetroPie/BIOS
```

| Name | md5sum | CRC32 |
| :--: | :--: | :--: |
| Family Computer Disk System (Japan) (Rev 1) | ca30b50f880eb660a320674ed365ef7a | 5e607dcf |

## Controls

All three emulators utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/nes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nesdiagram](https://cloud.githubusercontent.com/assets/10035308/8245062/4f0c5b8e-15e6-11e5-9255-b920543518d6.png)

## Tweaks

### How to setup Turbo Buttons for lr-fceumm

Open the RetroArch RGUI by pressing **Select+X** on the controller, or **Hotkey+F1** on the keyboard then navigate to:

* Quick Menu
    * Options
        * Change `Turbo Enable` to either `Player 1`, `Player 2`, `Both` or `None` by pressing left or right
        * You can also change the `Turbo Delay (in frames)` (Default is `3`)

Go back to the **Quick Menu** and then to **Resume**.

### How to disable Crop Overscan in lr-fceumm

Open the RetroArch RGUI:

* Quick Menu
    * Options
        * Change `Crop Overscan` to `disabled` by pressing left or right

Go back to the **Quick Menu** and then to **Resume**.

### How to disable Crop Overscan in lr-quicknes

Add this to your `/opt/retropie/configs/nes/retroarch.cfg` file. Make sure that this is placed **above** the `#include` line.

```shell
video_crop_overscan = false
```

### The NES Select Button

The NES controller has a select button that would be used to make selections in menu or change function in-game. For a list, see [here](http://www.racketboy.com/retro/nintendo/nes/so-what-was-the-nes-select-button-for).

When configuring RetroArch emulators, the select button is usually mapped to the physical select button on your controller as is the hotkey. Consequently, when you press the select button on your controller in a NES game to make a selection in a menu, in The Legend of Zelda, for example, nothing will happen as RetroArch is expecting a second button to be pressed such as start to exit the emulator.

There are two solutions to overcome this.

**Either Remap the select button**

In the NES RetroArch config file, `/opt/retropie/configs/nes/retroarch.cfg`, **above** the `#include"` line, add the following line:

```
input_player1_select_btn = "x"
```

where x is the button number you wish to remap the select button to.

**Or Remap the hotkey button**

In the NES RetroArch config file, `/opt/retropie/configs/nes/retroarch.cfg`, **above** the `#include"` line, add the following line:

```
input_enable_hotkey_btn = "x"
```

where x is the button number you wish to remap the hotkey to.

Both of these changes can also be made using the RGUI.