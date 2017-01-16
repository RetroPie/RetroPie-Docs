# Getting Started

Arcade emulation requires a different planning approach than console systems.

1. Choose an arcade emulator listed in the table below that your system is powerful enough to run
2. **Either download or 'rebuild' a set of arcade ROMs with a version number that exactly matches the emulator you selected**

The recommended emulators are:

* Pi 2 and Pi 3: `lr-mame2003` and `lr-fbalpha`
* Pi 1 and Pi Zero: `mame4all`  (the native emulator, not the RetroArch core) and `pi-fba`

If the ROM you wish to play is only supported by other emulator versions, please be aware that earlier arcade emulator versions usually run faster than later versions, but also that earlier versions support fewer games. Native emulators like MAME4ALL or AdvanceMAME perform better than RetroArch cores but they cannot take advantage of global RetroArch configurations so they must be configured individually. Generally 2D games can be emulated by the Pi 3's prococessor, but most 3D and vector games do not run at playable speed or at all.

| Emulator | Required ROM Version | # of ROMs | [.DAT Files](https://github.com/HerbFargus/retropie-dat/archive/master.zip) | Compatibility List |
| :---: | :---: | :---: | :---: | :---: |
| [mame4all](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.37b5 | [2270](http://code.google.com/p/imame4all/wiki/GameList) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing) |
| [lr-imame4all](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.37b5 | [2270](http://code.google.com/p/imame4all/wiki/GameList) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHQnJqS19JRUhzSmM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing) |
| [lr-mame2003](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.78 | 4705 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing) |
| [lr-mame2010](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.139 | 8782 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHUFdCc04zZ3o4dnM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1IRSmFrSDvIc6gAw0gn12TcQ3HDOwmrETTor8wvvb7VI/edit?usp=sharing) |
| [advmame-.94](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.94 | 5563 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHa2E5Rzl4ZEdMdjQ/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1AEQ94buG0rvbW0xdnYKeuEhHeCbuZlRfRJQCb1Dt8fw/edit?usp=sharing) |
| [advmame-1.4](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME) | MAME 0.106 | 6166 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHMEZnb1RxQWNmdHM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1RapyxChe2BMOfbX-FsCup9SXGxvS1WmXAofwaTJtmxc/edit?usp=sharing) |
| [pifba](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | FB Alpha v0.2.96.71 | 684 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHaHUta2dQYk1HTGM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing) |
| [lr-fbalpha2012](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | FB Alpha v0.2.97.30 | [3369](https://raw.githubusercontent.com/libretro/fbalpha2012/master/svn-current/trunk/gamelist.txt) | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHcF96YmdjaWlEdXM/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1rWO7Lm0bTGNpak6J-CPzde0GNIDP0NHDoQdJ6iWosfA/edit?usp=sharing) |
| [lr-fbalpha](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha) | FB Alpha v0.2.97.39 | [4375](https://raw.githubusercontent.com/libretro/fbalpha/master/gamelist.txt) | [.DAT](https://github.com/libretro/fbalpha/blob/master/dats/FB%20Alpha%20v0.2.97.39%20(ClrMame%20Pro%20XML).dat.zip?raw=true)| [List](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing) |
| [gngeopi](https://github.com/RetroPie/RetroPie-Setup/wiki/Neo-Geo) | [Varies - read more](https://github.com/retropie/retropie-setup/wiki/neo-geo#roms) | 203 | [.DAT](https://drive.google.com/file/d/0B2TMeZ6iEFvHZVVCYmVtaUM1VlU/view?usp=sharing)| [List](https://docs.google.com/spreadsheets/d/1A_a_9t14uzDUMrrO0RgLDwiVUiycmclcPIs6cU6Iox8/edit?usp=sharing) |

[**All Arcade ROMS Compatibility List**](https://docs.google.com/spreadsheets/d/1antILt7D12EWOFzyJwTfB86NceghMJKXG7CdYumuHec/edit?usp=sharing) feel free to contribute to the list.

## Crash Course in Arcade ROMs

Arcade ROMs are usually distributed as ZIP files which should not be unzipped or renamed. The version of any given arcade ROM must match the specific version of the arcade emulator because ROMs change from version to version of the emulator. For example, MAME2003 is based on MAME 0.78, so you must use MAME 0.78 ROMs with MAME2003. ROMs from an earlier or later MAME version, such as 0.50 or 0.173, will probably not work with MAME2003.

In addition to having a version number, arcade ROMs can be formatted three ways:

* **Non-merged**: All ROMs are standalone, each zip contains all the files needed to run that game, including any files from 'parent ROMs'. This is the recommended format for RetroPie arcade emulators.
* **Split**: Some ROMS that are considered clones, translations, or bootlegs also require a "parent ROM" to run. The parent ROM is normally the most common variant of a game in the English language. In some cases the parent is not the best working version of the game, however. For example, in a Split set pacman.zip (a clone), will not work without puckman.zip (its parent).
* **Merged**: Clones are merged into the parent ROM zip, meaning that more than one game is stored per file. Merged ROM sets are not supported.

For further details, see the system-specific wiki pages for [MAME](https://github.com/petrockblog/RetroPie-Setup/wiki/MAME) and [FBA](https://github.com/petrockblog/RetroPie-Setup/wiki/FinalBurn-Alpha). Recommended external resources for understanding more about MAME/FBA arcade ROMs and their usage are:

* [RetroPie Forum: How to use MAME with RetroPie Help Guide](https://retropie.org.uk/forum/topic/2859/how-to-use-mame-with-retropie-help-guide)
* [Demystifying MAME ROMs Tutorial by ChoccyHobNob](http://choccyhobnob.com/tutorials/demystifying-mame-roms/).

# Verifying and Rebuilding ROMs 
So how do you tell you have the right ROM if you aren't sure that your set matches the version required by the emulator you chose? What if you don't have the right version?

**Note: the process of verifying and rebuilding ROMs is complex and requires a substantial investment of time and effort in order to master. If your goal is to have working arcade ROMs, it is almost always simpler to download a full ROM set that has already been verified to match the arcade emulator you chose.**

Visit the page on [Validating, Rebuilding, and Filtering ROMs](https://github.com/RetroPie/RetroPie-Setup/wiki/Validating,-Rebuilding,-and-Filtering-Arcade-ROMs) to learn more.