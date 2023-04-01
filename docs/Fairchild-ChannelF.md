# Fairchild Channel F
***

<img src="https://upload.wikimedia.org/wikipedia/commons/3/34/Fairchild-Channel-F.png" width="480" title="Fairchild Channel F system">

***
_The Fairchild Channel F (short for "Channel Fun") was the first videogame system to use a microprocessor and game cartridges. It was first released in 1976 with a price of $169.95 and was discontinued in 1983._

***
## Emulators: [lr-fbneo](https://github.com/libretro/fbneo), [lr-freechaf](https://github.com/libretro/freechaf)


| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-FreeChaf](https://github.com/libretro/freechaf) | channelf  | .bin .chf | sl31253.bin, sl31254.bin, sl90025.bin | /opt/retropie/configs/channelf/retroarch.cfg |
| [lr-FBNeo](https://github.com/libretro/fbneo) | channelf  | .zip .7z | channelf.zip | /opt/retropie/configs/channelf/retroarch.cfg |


## Roms

Place your ChannelF ROMs in:
```
/home/pi/RetroPie/roms/channelf
```

**NOTE**: [lr-fbneo](lr-fbneo) expects the game roms to be in `.zip`/`.7z` archives named in a similar fashion to arcade romsets, so the filenames of the roms is important. Use a romset validation/building program like Clrmamepro or RomCenter to have the correct filenames, with the [FBNeo ChannelF DAT file](https://github.com/libretro/FBNeo/blob/master/dats/FinalBurn%20Neo%20(ClrMame%20Pro%20XML%2C%20Fairchild%20Channel%20F%20Games%20only).dat) file and a No-Intro ChannelF ROM collection to get the correct ROMset.  

More info is provided [here](https://docs.libretro.com/library/fbneo/#building-romsets-for-fbneo).

## BIOS

Pleace your BIOS files in
```
/home/pi/RetroPie/BIOS
```

**lr-fbneo** requires a `channelf.zip` file. It can also be copied in a `fbneo` sub-folder under the main BIOS folder.

| Filename | Description | MD5 |
|---|---|---|
| channelf.zip | ChannelF BIOS | 2f2f8de3827ae1faf2495e497ca95232 |

**lr-freechaf** uses the following files

| Filename | Description | MD5 |
|---|---|---|
| sl31253.bin | ChannelF BIOS (PSU 1) | ac9804d4c0e9d07e33472e3726ed15c3 |
| sl31254.bin | ChannelF BIOS (PSU 2) | da98f4bb3242ab80d76629021bb27585 |
| sl90025.bin | ChannelF II BIOS (PSU 1) (optional)| 95d339631d867c8f1d15a5f2ec26069d |

If the ChannelF II BIOS is included, it will be used instead of `sl31253.bin` file. All games are compatible with both.

## Controls

Both emulators utilise RetroArch configurations.

### FreeChaf

Access to the console buttons is provided via an overlay.  Pressing 'start' on either controller will display the console buttons.  You can select a button by moving left and right and press the button with any of the face buttons (A, B, X, Y).  Pressing 'start' a second time will hide the overlay.

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
