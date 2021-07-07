# Getting started with arcade emulation

**Arcade emulation requires a different approach than console emulation. Please read this entire page before beginning your RetroPie arcade emulation project.**

## Overview

RetroPie comes with multiple arcade emulators and each emulator requires a specific romset to work.

Each emulator is optimised for different hardware and different games so read the following sections to know which emulator to use and subsequently which romset is required for that emulator.

## Step 1: Choose your arcade emulator(s)

RetroPie's arcade emulators come in two main flavors: [MAME](MAME) and [FinalBurn](FinalBurn-Neo).

[MAME](MAME) is the most well-known and works with thousands of games. [FinalBurn](FinalBurn-Neo) is optimized for classic beat-em-up games like those from Neo Geo and Capcom. RetroPie includes multiple versions of both MAME and FinalBurn. Older versions require less processing power, but newer versions support more games and feature more accurate emulation.

Use this table as a guide when choosing an emulator version:

| Raspberry Pi version | Recommended MAME Emulator | Recommended FB Emulator |
| :---: | :---: | :---: |
|2 or 3| `lr-mame2003` | `lr-fbneo`|
|1 or Zero| `mame4all` | `pi-fba`|

Learn about other available versions on the pages about [MAME](MAME) and [FinalBurn Neo](FinalBurn-Neo).

## Step 2: Select the right ROM set

ROMS are not included with RetroPie. Copyright law varies by country and is up to the user to determine legality.

In general, you will only get good results with a full set of ROMs. Incomplete ROM sets (i.e. smaller collections of individual ROMs) are unlikely to work well. This is because certain roms (known as child roms) are dependent on files in other ROMs (known as parent ROMs) for example Pacman is actually an american clone (child) of the original japanese game Puckman (Parent). Without both files, most games will immediately exit.

There are a number of different rom set versions. Different versions contain different games (although there's plenty of overlap). This table tells you which rom set version you need for each emulator, and which games are in each set:

| Emulator | Required ROM Version | # of ROMs |
| :---: | :---: | :---: |
| [mame4all](MAME) | MAME 0.37b5 | 2270 |
| [lr-mame2003](MAME) | MAME 0.78 | 4720 |
| [pifba](FinalBurn-Neo#pifba) | FB Alpha v0.2.96.71 | 684 |
| [lr-fbneo](FinalBurn-Neo) | FB Neo v1.0.0.XX | 6746 |

To sum up, for best results:

* use a full ROM set;
* use the ROM set version that matches [the emulator you're using](#step-1-choose-your-arcade-emulators).

## Step 3: Transfer ROMs to Raspberry Pi

Follow the guide on Transferring ROMs [HERE](Transferring-Roms). 

Unlike some other system, arcade games should be zipped, if you extract them, they won't work.

You can place any of the rom sets in the `arcade` rom folder but you'll be required to pick the correct emulator for your rom set through the [runcommand menu](Runcommand). 

They can also be placed in their respective emulator rom folders, this information is included in the system pages: [MAME](MAME), [FBNeo](FinalBurn-Neo) 

## Further Reading

- [Arcade games and how to play them, A non-technical MAME and FBNeo (FBA) tutorial by rbaker](https://retropie.org.uk/forum/topic/7247/guide-arcade-games-and-how-to-play-them-a-non-technical-mame-fba-tutorial)
- [Instructions for how to set up FB Neo as a separate Neo Geo system, by thelostsoul](https://retropie.org.uk/forum/topic/19976/)
- RetroPie docs for [MAME](MAME) and [FB Neo](FinalBurn-Neo)
- [How to use MAME with RetroPie Help Guide by Floob](https://retropie.org.uk/forum/topic/2859/how-to-use-mame-with-retropie-help-guide)
- [Demystifying MAME ROMs Tutorial by ChoccyHobNob](https://web.archive.org/web/20161116054839/http://choccyhobnob.com/articles/demystifying-mame-roms/) (via archive.org)
- Advanced: [Validating, Rebuilding, and Filtering ROM Collections](Validating,-Rebuilding,-and-Filtering-ROM-Collections)
