# Getting Started with Arcade Emulation

**Arcade emulation requires a different planning approach than console systems. Please read this entire page before beginning your RetroPie arcade emulation project.**

## Step One: Choose an arcade emulator

| System | Recommended MAME Emulator| Recommended FB Alpha Emulator|
| :---: | :---: | :---: |
|Pi 2 and Pi 3| `lr-mame2003` | `lr-fbalpha`|
|Pi 1 and Pi Zero| `mame4all` | `pi-fba`|

Other [MAME](MAME) and [FB Alpha](FinalBurn-Alpha) emulator versions are also available in RetroPie. Please be aware that earlier versions generally run faster than later versions, but also support fewer games.

**Further Reading**

* [Arcade games and how to play them, A non-technical MAME and FBA tutorial by rbaker](https://retropie.org.uk/forum/topic/7247/guide-arcade-games-and-how-to-play-them-a-non-technical-mame-fba-tutorial)
* [Instructions for how to set up FB Alpha as a separate Neo Geo system](Neo-Geo)

## Step Two: Use the right ROM Set Version
Start with a full Non-Merged ROM collection (not an individual ROM) with the exact MAME or FB Alpha version number for the emulator you wish to use. An incorrect version or missing files will cause most or all games to immediately exit. In other words, lr-mame2003 will only work correctly with a collection of MAME 0.78 ROMs, mame4all will only work with a collection of MAME 0.37b5 ROMs, and so on.

| Emulator | Required ROM Version | # of ROMs | DAT File | Compatibility List |
| :---: | :---: | :---: | :---: | :---: |
| [mame4all](MAME) | MAME 0.37b5 | 2270 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1SHspjyHavY9-PKbO2swDr52BS2Wl_mB_Vjx2Z1SXiD8/edit) |
| [lr-mame2003](MAME) | MAME 0.78 | 4705 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing) |
| [pifba](FinalBurn-Alpha) | FB Alpha v0.2.96.71 | 684 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHaHUta2dQYk1HTGM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing) |
| [lr-fbalpha](FinalBurn-Alpha) | FB Alpha v0.2.97.42 | 4896 | [.DAT](https://github.com/libretro/fbalpha/raw/master/dats/FB%20Alpha%20v0.2.97.42%20(ClrMame%20Pro%20XML).dat.zip)| [List](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing) |


**Further Reading**

- Wiki pages for [MAME](Mame) and [FB Alpha](FinalBurn-Alpha).
- [How to use MAME with RetroPie Help Guide by Floob](https://retropie.org.uk/forum/topic/2859/how-to-use-mame-with-retropie-help-guide)
- [Demystifying MAME ROMs Tutorial by ChoccyHobNob](http://choccyhobnob.com/tutorials/demystifying-mame-roms/).
- Advanced: [Validating, Rebuilding, and Filtering Arcade ROMs](Validating,-Rebuilding,-and-Filtering-Arcade-ROMs)
