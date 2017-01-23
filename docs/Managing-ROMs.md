# Getting Started with Arcade Emulation

**Arcade emulation requires a different planning approach than console systems. Please read this entire page before beginning your RetroPie arcade emulation project.**

## Step One: Choose an arcade emulator

| System | Recommended MAME Emulator| Recommended FB Alpha Emulator|
|---|---|---|
|Pi 2 and Pi 3| `lr-mame2003` | `lr-fbalpha`|
|Pi 1 and Pi Zero| `mame4all`  (not `lr-mame4all`) | `pi-fba`|

Other [[MAME]]and [[FB Alpha|FinalBurn Alpha]] emulator versions are also available in RetroPie. Please be aware that earlier versions generally run faster than later versions, but also support fewer games.

**Further Reading**

* [Arcade games and how to play them, A non-technical MAME and FBA tutorial by rbaker](https://retropie.org.uk/forum/topic/7247/guide-arcade-games-and-how-to-play-them-a-non-technical-mame-fba-tutorial)
* [[Instructions for how to set up FB Alpha as a separate Neo Geo system|Neo-Geo]]

## Step Two: Use the right ROM Set Version
Start with a full Non-Merged ROM collection (not an individual ROM) with the exact MAME or FB Alpha version number for the emulator you wish to use. An incorrect version or missing files will cause most or all games to immediately exit. In other words, lr-mame2003 will only work correctly with a collection of MAME 0.78 ROMs, mame4all will only work with a collection of MAME 0.37b5 ROMs, and so on.

| Emulator | Required ROM Version | # of ROMs | DAT File | Compatibility List |
| :---: | :---: | :---: | :---: | :---: |
| [mame4all](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.37b5 | 2270 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing) |
| [lr-mame2003](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.78 | 4705 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing) |
| [pifba](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | FB Alpha v0.2.96.71 | 684 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHaHUta2dQYk1HTGM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing) |
| [lr-fbalpha](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | FB Alpha v0.2.97.39 | 4375 | [.DAT](https://github.com/libretro/fbalpha/blob/master/dats/FB%20Alpha%20v0.2.97.39%20(ClrMame%20Pro%20XML).dat.zip?raw=true)| [List](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing) |


# Crash Course in Arcade ROMs

**Arcade Emulator Terminology**
* **ROM, ROM set, and romset**: Arcade games are packaged as zip files, most of which are composed of more than one individual 'ROM' files. That is why some resources refer to an individual arcade game as a ROM (like people use to describe a zipped game cartridge ROM) while other resources refer to an individual game as a ROM set or romset.
* **ROM version or ROM set version**: Each version of an arcade emulator must be used with ROMs that have the same exact version number. For example, MAME 0.37b5 ROMs are required by the MAME4ALL emulator, but will not work correctly with the lr-mame2010 emulator, which requires MAME 0.139 ROMs.
* **Sample**: Some games require an additional zip file with recorded sounds or music in order for audio to work correctly. The path where these samples should be copied varies from emulator to emulator.
* **CHD**: Some MAME games require data from an internal hard drive, CD-ROM, laserdisk, or other media in order to be emulated -- those forms of media are packaged as CHD files. CHDs files should be copied to subfolders within the folder where the MAME ROM zips have been installed.

In addition to having a version number, arcade ROMs can be formatted three ways:

* **Non-merged**: All ROMs can be used standalone because each zip contains all the files needed to run that game, including any files from 'parent ROMs'. This is the recommended format for RetroPie arcade emulators.
* **Split**: Some ROMS that are considered clones, translations, or bootlegs also require a "parent ROM" to run. The parent ROM is often the first or most common variant of a game. In some cases the parent is not the most popular or best working version of the game, however. For example, in a Split set pacman.zip (a clone), will not work without puckman.zip (its parent).
* **Merged**: Clones are merged into the parent ROM zip, meaning that more than one game is stored per file. Merged ROM sets are not recommended.

**Further Reading**
* Wiki pages for [[MAME]] and [[FB Alpha|FinalBurn-Alpha]].
* [How to use MAME with RetroPie Help Guide by Floob](https://retropie.org.uk/forum/topic/2859/how-to-use-mame-with-retropie-help-guide)
* [Demystifying MAME ROMs Tutorial by ChoccyHobNob](http://choccyhobnob.com/tutorials/demystifying-mame-roms/).

## Correct ROM versions are essential
So how do you tell you have the right ROM if you aren't sure that your set matches the version required by the emulator you chose? What if you don't have the right version?

It is possible to 'rebuild' from one version of an arcade ROM collection to another. If you also have access to a newer ROM collection you can 'roll forward' your ROM version, of if you have access to an older ROM collection or a 'rollback' collection you can rebuild to a lower ROM version. 

**Note: the process of verifying and rebuilding ROMs is complex and requires a substantial investment of time and effort in order to master. If your goal is to have working arcade ROMs, it is almost always simpler to download a full ROM set that has already been verified to match the arcade emulator you chose.**

Visit the page on [[Validating, Rebuilding, and Filtering ROMs|Validating,-Rebuilding,-and-Filtering-Arcade-ROMs]] to learn more about rebuilding.