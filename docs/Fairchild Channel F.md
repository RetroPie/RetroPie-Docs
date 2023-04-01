***

***
_The Fairchild Channel F (short for channel fun) was the first videogame system to use a microprocesser and game cartridges. It was first released in 1976 with a price of $169.95  and was discontinued in 1983._

***
## Emulators

### lr-fbneo

 * [FinalBurn Neo Github project page](https://github.com/libretro/fbneo)
 * [Important announcement about FBNeo romset constantly changing](https://retropie.org.uk/forum/topic/19741/new-fb-alpha-libretro-pre-v0-2-97-44)

**Note: Please see [lr-fbneo](lr-fbneo) for information on how to configure specific features of this emulator.**

Accepted File Extensions: **.7z .zip**

Place your ChannelF ROMs in
```
/home/pi/RetroPie/roms/channelf
```
## BIOS
To use this core you need a valid BIOS file named `channelf.zip` in BIOS folder:
```
~/RetroPie/BIOS/channelf.zip
```
### lr-freechaf

Accepted File Extensions: **.bin .rom**

## BIOS
FreeChaF requires two BIOS files to be placed in the libretro 'system' folder:

| Filename | Description | MD5 |
|---|---|---|
| sl31253.bin | ChannelF BIOS (PSU 1) | ac9804d4c0e9d07e33472e3726ed15c3 |
| sl31254.bin | ChannelF BIOS (PSU 2) | da98f4bb3242ab80d76629021bb27585 |

If the ChannelF II BIOS is included, it will be used instead of sl31253.  All games are compatible with both.

| Filename | Description | MD5 |
|---|---|---|
| sl90025.bin | ChannelF II BIOS (PSU 1) | 95d339631d867c8f1d15a5f2ec26069d |

* BIOS filenames are case-sensitive

## Console button overlay
Access to the console buttons is provided via an overlay.  Pressing 'start' on either controller will display the console buttons.  You can select a button by moving left and right and press the button with any of the face buttons (A, B, X, Y).  Pressing 'start' a second time will hide the overlay.

## Controls
* **Console Overlay** - allows the user to view and select console buttons.
* **Controller Swap** - Controller Swap swaps the player 1 and player 2 controllers.

| FreeChaF Function | Retropad |
| --- | --- |
|Forward| D-Pad Up, Left-Analog Up|
|Backward| D-Pad Down, Left-Analog Down|
|Rotate Left | Y, L, Right-Analog Left |
|Rotate Right | A, R, Right-Analog Right |
|Pull Up | X, Right-Analog Up |
|Push Down | B, Right-Analog Down |
|Show/Hide Console Overlay | Start |
|Controller Swap | Select |
