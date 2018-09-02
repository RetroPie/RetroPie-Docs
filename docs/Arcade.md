# Getting started with arcade emulation

**Arcade emulation requires a different approach than console emulation. Please read this entire page before beginning your RetroPie arcade emulation project.**

## Overview

Here are the general steps you will follow. Each step is explained in detail in the sections below.

1. **Choose your arcade emulator(s)**

    RetroPie comes equipped with several arcade emulators. Depending on your hardware and software setup, some emulators are a better option than others.

1. **Download the right ROMs**

    We don't like telling people where to download ROMs. But we can tell you which ROM _versions_ to get, based on your setup.

1. **Transfer ROMs to Raspberry Pi**

    Arcade ROMs go in `/home/pi/RetroPie/roms/arcade`.

## Step 1: Choose your arcade emulator(s)

RetroPie's arcade emulators come in two main flavors: [MAME](MAME) and [FinalBurn Alpha](FinalBurn-Alpha).

[MAME](MAME) is the most well-known and works with thousands of games. [FinalBurn Alpha](FinalBurn-Alpha) is optimized for classic beat-em-up games like those from [Neo Geo](Neo-Geo) and Capcom.

RetroPie offers multiple versions of both MAME and FinalBurn Alpha. Older versions require less processing power, but newer versions support more games.

Use this table as a guide when choosing an emulator version:

| Raspberry Pi version | Recommended MAME Emulator| Recommended FB Alpha Emulator|
| :---: | :---: | :---: |
|2 or 3| `lr-mame2003` | `lr-fbalpha`|
|1 or Zero| `mame4all` | `pi-fba`|

Learn about other available versions on the pages about [MAME](MAME) and [FinalBurn Alpha](FinalBurn-Alpha).

## Step 2: Download the right ROMs

In most countries, **downloading games is illegal unless you also own legal copies of those games**. We're not going to tell you where to download ROMs. A search engine may help. What follows is a technical description of compatibility between different emulators and ROM versions.

In general, you will only get good results with a full "reference set" of ROMs. Incomplete ROM sets (i.e. smaller collections of individual ROMs) are unlikely to work well. This is because a reference set contains common files shared by multiple ROMs. Without these files, most games will immediately exit.

There are a number of different reference set versions. Different versions contain different games (although there's plenty of overlap). This table tells you which reference set version you need for each emulator, and which games are in each set:

| Emulator | Required ROM Version | # of ROMs | DAT File | Compatibility List |
| :---: | :---: | :---: | :---: | :---: |
| [mame4all](MAME) | MAME 0.37b5 | 2270 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHVUNfWHpUZk82bkk/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1SHspjyHavY9-PKbO2swDr52BS2Wl_mB_Vjx2Z1SXiD8/edit) |
| [lr-mame2003](MAME) | MAME 0.78 | 4705 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing) |
| [pifba](FinalBurn-Alpha) | FB Alpha v0.2.96.71 | 684 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHaHUta2dQYk1HTGM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing) |
| [lr-fbalpha](FinalBurn-Alpha) | FB Alpha v0.2.97.43 | 4896 | [.DAT](https://github.com/libretro/fbalpha/raw/master/dats/FB%20Alpha%20v0.2.97.42%20(ClrMame%20Pro%20XML).dat.zip)| [List](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing) |

To sum up, for best results:

* use a full ROM reference set;
* use the reference set version that matches [the emulator you're using](#step-1-choose-your-arcade-emulators).

## Step 3: Transfer ROMs to Raspberry Pi

You can transfer ROMs in [multiple ways](Transferring-Roms). If you downloaded a reference set zip file, extract the zip, then copy the contents of the `roms` folder to `/home/pi/RetroPie/roms/arcade` on your Raspberry Pi. 

After transferring your ROMs, restart RetroPie. The games will appear in the Arcade section.

## Further Reading

- [Arcade games and how to play them, A non-technical MAME and FBA tutorial by rbaker](https://retropie.org.uk/forum/topic/7247/guide-arcade-games-and-how-to-play-them-a-non-technical-mame-fba-tutorial)
- [Instructions for how to set up FB Alpha as a separate Neo Geo system](Neo-Geo)
- RetroPie docs for [MAME](Mame) and [FB Alpha](FinalBurn-Alpha).
- [How to use MAME with RetroPie Help Guide by Floob](https://retropie.org.uk/forum/topic/2859/how-to-use-mame-with-retropie-help-guide)
- [Demystifying MAME ROMs Tutorial by ChoccyHobNob](http://choccyhobnob.com/tutorials/demystifying-mame-roms/).
- Advanced: [Validating, Rebuilding, and Filtering ROM Collections](Validating,-Rebuilding,-and-Filtering-ROM-Collections)
