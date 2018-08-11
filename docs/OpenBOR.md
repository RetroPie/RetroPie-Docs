
***

![](http://i.imgur.com/QSPlNYP.png)

***
_OpenBOR is the open source continuation of Beats of Rage - a 2D sidescrolling beat em up game engine._
***
### Emulator: [OpenBOR](https://github.com/rofl0r/openbor.git)

### ROMS:

Accepted extensions: **.pak**

Place your OpenBOR games in 
```
/home/pi/RetroPie/roms/ports/openbor
```

Then you need to run
```
/opt/retropie/ports/openbor/extract.sh
```

Your games are extracted and ready to be played. Your originals are stored safely in `/home/pi/RetroPie/roms/ports/openbor/original` but they won't be needed anymore. Everything within it can be deleted.

Alternative to the current extracting script (because the way above fails on FAT32 devices!) use [this extraction script from RetroPie forum.](https://retropie.org.uk/forum/topic/18565/tutorial-openbor-the-complete-guide/57)
1. There you place your paks to `/home/pi/RetroPie/roms/ports/openbor/pak`
2. just run the script. The script extracts all pak-files (even with mixed characters) to openbor directory
3. Extracted data will be stored to `/home/pi/RetroPie/roms/ports/openbor/gamename.bor/data`
4. The script backups the old PAK files automatically `gamename.pak` will be `gamename.pak.original`

For Windows users, just search for `Openbor Makepak & Extractor` and download the toolset.

See more info from the OpenBOR Community [HERE](http://www.chronocrash.com/forum/index.php)

### Controls:

You need a keyboard to navigate the menus or you can setup the system with preconfigurated control settings. Therefore read more in the hints: [OpenBOR - the complete guide](https://retropie.org.uk/forum/topic/18565)


### Hints:

* [How to create OpenBOR system in ES](https://retropie.org.uk/forum/topic/13784)
* [OpenBOR - the complete guide](https://retropie.org.uk/forum/topic/18565)