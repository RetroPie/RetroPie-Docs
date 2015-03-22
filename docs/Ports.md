# Ports
Doom, Duke Nukem 3D, Quake, Quake III Arena

## Doom: [(libretro-prboom)](https://github.com/libretro/libretro-prboom)
***
![Doom](http://vignette4.wikia.nocookie.net/doom/images/4/4b/Doom-1-.gif/revision/latest?cb=20080630083507)
***


### Old Configs

**Music**

To enable music in your Doom game(s) you need to copy MP3s with specific names into the same folder as your ROMs are located. You can find a list of names [here](https://github.com/libretro/libretro-prboom/blob/master/src/m_misc.c#L605): They follow the scheme e1m1.mp3, e1m2.mp3, ..., e2m1.mp, e2m2.mp3, ... . There are freely available tracks available - find them by searching for "PSX Doom Music".

Below are the corresponding tracks if the MP3s are named:

* mus_e1m1                  "level 01 (hangar).mp3" 
* mus_e1m2                  "level 02 (plant).mp3" 
* mus_e1m3                  "level 03 (toxin refinery).mp3" 
* mus_e1m4                  "level 04 (command control).mp3" 
* mus_e1m5                  "level 05 (phobos lab).mp3" 
* mus_e1m6                  "level 06 (central processing).mp3" 
* mus_e1m7                  "level 07 (computer station).mp3" 
* mus_e1m8                  "level 08 (phobos anomaly).mp3" 
* mus_e1m9                  "level 06 (fistula).mp3" 
* mus_e2m1                  "level 09 (deimos anomaly).mp3" 
* mus_e2m2                  "level 10 (containment area).mp3" 
* mus_e2m3                  "level 11 (refinery).mp3" 
* mus_e2m4                  "level 12 (deimos lab).mp3" 
* mus_e2m5                  "level 13 (command center).mp3" 
* mus_e2m6                  "level 02 (plant).mp3" 
* mus_e2m7                  "level 01 (hangar).mp3" 
* mus_e2m8                  "level 03 (toxin refinery).mp3" 
* mus_e2m9                  "level 02 (virgil).mp3" 
* mus_e3m1                  "level 17 (hell keep).mp3" 
* mus_e3m2                  "level 03 (canyon).mp3" 
* mus_e3m3                  "level 18 (pandemonium).mp3" 
* mus_e3m4                  "level 06 (central processing).mp3" 
* mus_e3m5                  "level 20 (unholy cathedral).mp3" 
* mus_e3m6                  "level 21 (mt erebus).mp3" 
* mus_e3m7                  "level 22 (limbo).mp3" 
* mus_e3m8                  "level 09 (nessus).mp3" 
* mus_e3m9                  "level 10 (paradox).mp3" 
* mus_inter                 "e2m3.mp3" 
* mus_intro                 "track 02 title screen.mp3" 
* mus_bunny                 "track 03 main menu.mp3" 
* mus_victor                "track 09 endgame.mp3" 
* mus_introa                "track 02 title screen.mp3" 
* mus_runnin                "level 01 (hangar).mp3" 
* mus_stalks                "level 10 (containment area).mp3" 
* mus_countd                "level 22 (limbo).mp3" 
* mus_betwee                "level 16 (hell gate).mp3" 
* mus_doom                  "level 08 (phobos anomaly).mp3" 
* mus_the_da                "level 21 (mt erebus).mp3" 
* mus_shawn                 "level 20 (unholy cathedral).mp3" 
* mus_ddtblu                "level 24 (hell beneath).mp3" 
* mus_in_cit                "level 11 (refinery).mp3" 
* mus_dead                  "level 13 (command center).mp3" 
* mus_stlks2                "level 09 (deimos anomaly).mp3" 
* mus_theda2                "level 17 (hell keep).mp3" 
* mus_doom2                 "level 08 (minos).mp3" 
* mus_ddtbl2                "level 16 (hell gate).mp3" 
* mus_runni2                "level 04 (combine).mp3" 
* mus_dead2                 "level 18 (pandemonium).mp3" 
* mus_stlks3                "level 06 (central processing).mp3" 
* mus_romero                "level 05 (phobos lab).mp3" 
* mus_shawn2                "level 10 (containment area).mp3" 
* mus_messag                "level 01 (attack).mp3" 
* mus_count2                "level 02 (plant).mp3" 
* mus_ddtbl3                "level 03 (toxin refinery).mp3" 
* mus_ampie                 "level 01 (hangar).mp3" 
* mus_theda3                "level 06 (fistula).mp3" 
* mus_adrian                "level 07 (computer station).mp3" 
* mus_messg2                "level 08 (phobos anomaly).mp3" 
* mus_romer2                "level 11 (refinery).mp3" 
* mus_tense                 "level 07 (geryon).mp3" 
* mus_shawn3                "level 05 (catwalk).mp3" 
* mus_openin                "level 04 (command control).mp3" 
* mus_evil                  "level 16 (hell gate).mp3" 
* mus_ultima                "level 03 (toxin refinery).mp3" 
* mus_read_m                "track 03 main menu.mp3" 
* mus_dm2ttl                "track 02 title screen.mp3" 
* mus_dm2int                "track 05 stats screen.mp3"

## Duke Nukem 3D

***
![Duke Nukem 3D](http://monkeydesk.at/content/attachments/5843d1337609358-duke-nukem-3d.jpg/)

***


**Old Configs**

The grp-file-argument gets ignored.
It always loads the grp-file located at

> /usr/share/games/eduke32/duke3d.grp

If you swap this with a full version of the grp-file it works.

If you start EDuke32 and it is not recognizing your controller bring down the console and type:

`in_joystick 1`

# Quake [(libretro-tyrquake)](https://github.com/libretro/libretro-tyrquake)

***
![Quake](http://firsthour.net/screenshots/quake/quake-cover-thumb.jpg)
***

# Quake III Arena

***
![Quake III Arena](http://games-history.ru/upload/box/quake3_box.jpg)
***





