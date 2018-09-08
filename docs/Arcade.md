# Getting started with arcade emulation

**Arcade emulation requires a different approach than console emulation. Please read this entire page before beginning your RetroPie arcade emulation project.**

## Overview

RetroPie comes with multiple arcade emulators and each emulator requires a specific romset to work.

Each emulator is optimised for different hardware and different games so read the following sections to know which emulator to use and subsequently which romset is required for that emulator.

## Step 1: Choose your arcade emulator(s)

RetroPie's arcade emulators come in two main flavors: [MAME](MAME) and [FinalBurn Alpha](FinalBurn-Alpha).

[MAME](MAME) is the most well-known and works with thousands of games. [FinalBurn Alpha](FinalBurn-Alpha) is optimized for classic beat-em-up games like those from [Neo Geo](Neo-Geo) and Capcom.

RetroPie includes multiple versions of both MAME and FinalBurn Alpha. Older versions require less processing power, but newer versions support more games.

Use this table as a guide when choosing an emulator version:

| Raspberry Pi version | Recommended MAME Emulator| Recommended FB Alpha Emulator|
| :---: | :---: | :---: |
|2 or 3| `lr-mame2003` | `lr-fbalpha`|
|1 or Zero| `mame4all` | `pi-fba`|

Learn about other available versions on the pages about [MAME](MAME) and [FinalBurn Alpha](FinalBurn-Alpha).

## Step 2: Select the right ROM set

ROMS are not included with RetroPie. Copyright law varies by country and is up to the user to determine legality.

In general, you will only get good results with a full set of ROMs. Incomplete ROM sets (i.e. smaller collections of individual ROMs) are unlikely to work well. This is because certain roms (known as child roms) are dependent on files in other ROMs (known as parent ROMs) for example Pacman is actually an american clone (child) of the original japanese game Puckman (Parent) . Without both files, most games will immediately exit.

There are a number of different rom set versions. Different versions contain different games (although there's plenty of overlap). This table tells you which rom set version you need for each emulator, and which games are in each set:

| Emulator | Required ROM Version | # of ROMs | DAT File | Compatibility List |
| :---: | :---: | :---: | :---: | :---: |
| [mame4all](MAME) | MAME 0.37b5 | 2270 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHVUNfWHpUZk82bkk/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1SHspjyHavY9-PKbO2swDr52BS2Wl_mB_Vjx2Z1SXiD8/edit) |
| [lr-mame2003](MAME) | MAME 0.78 | 4705 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing) |
| [pifba](FinalBurn-Alpha) | FB Alpha v0.2.96.71 | 684 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHaHUta2dQYk1HTGM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing) |
| [lr-fbalpha](FinalBurn-Alpha) | FB Alpha v0.2.97.43 | 4896 | [.DAT](https://raw.githubusercontent.com/libretro/fbalpha/master/dats/FB%20Alpha%20v0.2.97.43%20(ClrMame%20Pro%20XML).dat)| [List](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing) |

To sum up, for best results:

* use a full ROM set;
* use the ROM set version that matches [the emulator you're using](#step-1-choose-your-arcade-emulators).

## Step 3: Transfer ROMs to Raspberry Pi

Follow the guide on Transferring ROMs [HERE](Transferring-Roms). 

Unlike some other system, arcade games should be zipped, if you extract them, they won't work.

You can place any of the rom sets in the `arcade` rom folder but you'll be required to pick the correct emulator for your rom set through the [runcommand menu](runcommand). 

They can also be placed in their respective emulator rom folders, this information is included in the system pages: [MAME](MAME), [FBA](FinalBurn-Alpha) 

## Further Reading

- [Arcade games and how to play them, A non-technical MAME and FBA tutorial by rbaker](https://retropie.org.uk/forum/topic/7247/guide-arcade-games-and-how-to-play-them-a-non-technical-mame-fba-tutorial)
- [Instructions for how to set up FB Alpha as a separate Neo Geo system](Neo-Geo)
- RetroPie docs for [MAME](Mame) and [FB Alpha](FinalBurn-Alpha).
- [How to use MAME with RetroPie Help Guide by Floob](https://retropie.org.uk/forum/topic/2859/how-to-use-mame-with-retropie-help-guide)
- [Demystifying MAME ROMs Tutorial by ChoccyHobNob](http://choccyhobnob.com/tutorials/demystifying-mame-roms/).
- Advanced: [Validating, Rebuilding, and Filtering ROM Collections](Validating,-Rebuilding,-and-Filtering-ROM-Collections)