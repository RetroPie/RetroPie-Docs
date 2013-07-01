## Video output

### HDMI

|Emulator|System|Dispmanx||Graphics Working|Sound Working|Good Performance|Test Game|
|---|---|---|---|---|---|---|---
|PocketSNES|SNES| ||X|X|X|Super Mario Kart|
|PiSNES|SNES| ||||||
|SNES9X-RPi|SNES| ||||||
|DGEN|Megadrive/Genesis| ||X|X|X|Streets of Rage 2|
||NES|||||||
|Osmose|Gamegear|||||||
||Atari|||||||
|PCSX ReArmed|PSX|||||||
|prboom|Doom|||||||
|eDuke32|Duke3D|||||||
|gngeo-pi-0.85|NeoGeo|||||||
|gngeo-0.7|NeoGeo|||||||
|rpix86|PC|||||||

### Composite


|Video output|Emulator|System|SDL lib|Performance|Graphics|Sound|Test Rom|Emulation Station Command|Info
|---|---|---|---|---|---|---|---|---|---
|Composite|DGEN|MegaDrive|dispmanx|Good|Good|Good|Sonic the Hedgehog.smd|"export LD_LIBRARY_PATH=""/home/xbian/SDL12-kms-dispmanx/build/.libs""| /home/xbian/RetroPie/emulators/dgen-sdl/dgen %ROM%"|
|Composite|DGEN|MegaDrive|standard sdl lib|Black screen|Good|Good|Sonic the Hedgehog.smd|"/home/xbian/RetroPie/supplementary/runcommand/runcommand.sh 1 ""/home/xbian/RetroPie/emulators/dgen-sdl/dgen -f -r /home/xbian/RetroPie/configs/all/dgenrc %ROM%"""|
|HDMI All|DGEN|MegaDrive|standard sdl lib|Good|Good|Good|Sonic the Hedgehog.smd||
||||||||||
|Composite|PiSNES|SNES|standard sdl lib|Good|Good|Good|F-Zero.smc|/home/xbian/RetroPie/emulators/pisnes/snes9x %ROM%|
|Composite|PiSNES|SNES|dispmanx|Error - wont run|Error - won't run|Error - won't run|F-Zero.smc|"export LD_LIBRARY_PATH=""/home/xbian/SDL12-kms-dispmanx/build/.libs""| /home/xbian/RetroPie/emulators/pisnes/snes9x %ROM%"|
|HDMI All|PiSNES|SNES|standard sdl lib|OK|Slow down then run normal|Good|F-Zero.smc|/home/pi/RetroPie/emulators/pisnes/snes9x %ROM%|
|Composite|SNES9x|SNES|dispmanx||||||
|Composite|SNES9x|SNES|standard sdl lib||||||
|Composite|SNES9x-Rpi|SNES|dispmanx|Good|Good|Very bad constant popping|F-Zero.smc|"export LD_LIBRARY_PATH=""/home/xbian/SDL12-kms-dispmanx/build/.libs""| /home/xbian/RetroPie/emulators/snes9x-rpi/snes9x %ROM%"|
|Composite|SNES9x-Rpi|SNES|standard sdl lib|Good|Good|Clicks and pops|F-Zero.smc|/home/xbian/RetroPie/emulators/snes9x-rpi/snes9x %ROM%|
||||||||||
|Composite|Retroarch -> iMAME4All|MAME|dispmanx||||||
|Composite|Retroarch -> iMAME4All|MAME|standard sdl lib||||||
|HDMI All|Retroarch -> iMAME4All|MAME|standard sdl lib|Good|Good|Good|1943.zip , rainbow.zip|retroarch -L /home/pi/RetroPie/emulatorcores/imame4all-libretro/libretro.so --config /home/pi/RetroPie/configs/all/retroarch.cfg --appendconfig /home/pi/RetroPie/configs/mame/retroarch.cfg %ROM% |
|Composite|Advance MAME|MAME|dispmanx|||||"export LD_LIBRARY_PATH=""/home/xbian/SDL12-kms-dispmanx/build/.libs""| /home/xbian/RetroPie/emulators/advancemame-0.94.0/advmame %ROM%"|
|Composite|Advance MAME|MAME|standard sdl lib||||||
||||||||||
|Composite|Doom|Doom|dispmanx|Bad|None|Bad Sound|Doom1.wad|"export LD_LIBRARY_PATH=""/home/xbian/SDL12-kms-dispmanx/build/.libs""| /home/xbian/RetroPie/supplementary/runcommand/runcommand.sh 1 ""retroarch -L /home/xbian/RetroPie/emulatorcores/libretro-prboom/prboom_libretro.so --config /home/xbian/RetroPie/configs/all/retroarch.cfg --appendconfig /home/xbian/RetroPie/configs/doom/retroarch.cfg %ROM%"""|
|Composite|Doom|Doom|standard sdl lib||||||
|HDMI|Doom|Doom|standard sdl lib|Good|Good|Good|Doom1.wad|COMMAND=retroarch -L /home/pi/RetroPie/emulatorcores/libretro-prboom/prboom_libretro.so  --config /home/pi/RetroPie/configs/all/retroarch.cfg --appendconfig /home/pi/RetroPie/configs/doom/retroarch.cfg %ROM% PLATFORMID=1|
||||||||||
|Composite|eDuke32|Duke 3D|dispmanx|Good|Bad colour|Average|duke.grp Full version|"export LD_LIBRARY_PATH=""/home/xbian/SDL12-kms-dispmanx/build/.libs""| eduke32 -g %ROM% -gamegrp %ROM%"|
|Composite|eDuke32|Duke 3D|standard sdl lib||||||
|HDMI|eDuke32|Duke 3D|standard sdl lib|Good|Good|Good|duke,grp Full version||
||||||||||
|Composite|gngeo|Neo Geo|dispmanx||Error - won't run|Error - won't run|Double Dragon|"export LD_LIBRARY_PATH=""export LD_LIBRARY_PATH=""/home/xbian/SDL12-kms-dispmanx/build/.libs""| /home/xbian/RetroPie/emulators/gngeo-0.7/installdir/bin/gngeo -i /home/xbian/RetroPie/roms/neogeo -B /home/xbian/RetroPie/emulators/gngeo-0.7/neogeo-bios %ROM%"|