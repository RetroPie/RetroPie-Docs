![](http://1.bp.blogspot.com/-q1BVHMrTq7M/UT9Y6D_tCLI/AAAAAAAAD40/fM2ZUTzEIqE/s1600/risen3d+3d+models+doom+title.png)

***
_Doom was one the game the popularised First Person Shooting as a genre. It was developed by Id Software in 1993._

***
## Emulator: [libretro-prboom](https://github.com/petrockblog/RetroPie-Setup/blob/master/scriptmodules/libretrocores/lr-prboom.sh), [ZDOOM](https://github.com/rheit/zdoom)

## Controls
libretro-prboom utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/doom/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

### Music

The most ideal and authentic way to listen to the the original Doom (1&2) tracks is to google 'doom 1 and 2 midis' and download them. You can then convert the midi files into MP3s.

To enable music in your Doom game(s) you need to copy MP3s with specific names into the same folder as your ROMs are located. You can find a list of names [here](https://github.com/libretro/libretro-prboom/blob/master/src/m_misc.c#L605): They follow the scheme e1m1.mp3, e1m2.mp3, ..., e2m1.mp, e2m2.mp3, ... . There are freely available tracks available - find them by searching for "PSX Doom Music".

Below are the corresponding tracks if the MP3s are named:

File Name | mp3 
 --- | ---
* mus_e1m1       |           "level 01 (hangar).mp3" 
* mus_e1m2        |          "level 02 (plant).mp3" 
* mus_e1m3         |         "level 03 (toxin refinery).mp3" 
* mus_e1m4          |        "level 04 (command control).mp3" 
* mus_e1m5           |       "level 05 (phobos lab).mp3" 
* mus_e1m6            |      "level 06 (central processing).mp3" 
* mus_e1m7            |      "level 07 (computer station).mp3" 
* mus_e1m8          |        "level 08 (phobos anomaly).mp3" 
* mus_e1m9           |       "level 06 (fistula).mp3" 
* mus_e2m1          |        "level 09 (deimos anomaly).mp3" 
* mus_e2m2          |        "level 10 (containment area).mp3" 
* mus_e2m3          |        "level 11 (refinery).mp3" 
* mus_e2m4          |        "level 12 (deimos lab).mp3" 
* mus_e2m5          |        "level 13 (command center).mp3" 
* mus_e2m6          |        "level 02 (plant).mp3" 
* mus_e2m7          |        "level 01 (hangar).mp3" 
* mus_e2m8          |        "level 03 (toxin refinery).mp3" 
* mus_e2m9          |        "level 02 (virgil).mp3" 
* mus_e3m1          |        "level 17 (hell keep).mp3" 
* mus_e3m2          |        "level 03 (canyon).mp3" 
* mus_e3m3          |        "level 18 (pandemonium).mp3" 
* mus_e3m4          |        "level 06 (central processing).mp3" 
* mus_e3m5          |        "level 20 (unholy cathedral).mp3" 
* mus_e3m6          |        "level 21 (mt erebus).mp3" 
* mus_e3m7          |        "level 22 (limbo).mp3" 
* mus_e3m8          |        "level 09 (nessus).mp3" 
* mus_e3m9          |        "level 10 (paradox).mp3" 
* mus_inter         |        "e2m3.mp3" 
* mus_intro         |        "track 02 title screen.mp3" 
* mus_bunny         |        "track 03 main menu.mp3" 
* mus_victor        |        "track 09 endgame.mp3" 
* mus_introa        |        "track 02 title screen.mp3" 
* mus_runnin        |        "level 01 (hangar).mp3" 
* mus_stalks        |        "level 10 (containment area).mp3" 
* mus_countd        |        "level 22 (limbo).mp3" 
* mus_betwee        |        "level 16 (hell gate).mp3" 
* mus_doom          |        "level 08 (phobos anomaly).mp3" 
* mus_the_da        |        "level 21 (mt erebus).mp3" 
* mus_shawn         |        "level 20 (unholy cathedral).mp3" 
* mus_ddtblu        |        "level 24 (hell beneath).mp3" 
* mus_in_cit        |        "level 11 (refinery).mp3" 
* mus_dead          |        "level 13 (command center).mp3" 
* mus_stlks2           |     "level 09 (deimos anomaly).mp3" 
* mus_theda2           |     "level 17 (hell keep).mp3" 
* mus_doom2            |     "level 08 (minos).mp3" 
* mus_ddtbl2            |    "level 16 (hell gate).mp3" 
* mus_runni2           |     "level 04 (combine).mp3" 
* mus_dead2            |     "level 18 (pandemonium).mp3" 
* mus_stlks3          |      "level 06 (central processing).mp3" 
* mus_romero          |      "level 05 (phobos lab).mp3" 
* mus_shawn2          |      "level 10 (containment area).mp3" 
* mus_messag          |      "level 01 (attack).mp3" 
* mus_count2          |      "level 02 (plant).mp3" 
* mus_ddtbl3         |       "level 03 (toxin refinery).mp3" 
* mus_ampie          |       "level 01 (hangar).mp3" 
* mus_theda3         |       "level 06 (fistula).mp3" 
* mus_adrian           |     "level 07 (computer station).mp3" 
* mus_messg2          |      "level 08 (phobos anomaly).mp3" 
* mus_romer2          |      "level 11 (refinery).mp3" 
* mus_tense           |      "level 07 (geryon).mp3" 
* mus_shawn3          |      "level 05 (catwalk).mp3" 
* mus_openin          |      "level 04 (command control).mp3" 
* mus_evil            |      "level 16 (hell gate).mp3" 
* mus_ultima          |      "level 03 (toxin refinery).mp3" 
* mus_read_m          |      "track 03 main menu.mp3" 
* mus_dm2ttl          |      "track 02 title screen.mp3" 
* mus_dm2int         |       "track 05 stats screen.mp3"