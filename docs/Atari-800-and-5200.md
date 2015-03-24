![Atari 5200](http://client-cdn.crystalcommerce.com/photo/pinkgorillagames/file/64518/large/atari-5200-logo.jpg?1377816190)
***
_Atari released a series of 8 bit computers (400, 800, 1200XL, 600XL, 800XL, 130XE, XEGS) and a video game console known as the Atari 5200 from 1979 to 1992_
***
## Emulator: [Atari800](http://atari800.sourceforge.net/) 
This emulator emulates the Atari 8 bit family: 400, 800, 1200XL, 600XL, 800XL, 130XE, XEGS and the Atari 5200. This one of the more tricky emulators to get set up as it requires a multiplicity of BIOS files and configurations depending on what systems you want to utilise but it seems to run Atari 5200 games pretty well.
## ROMS
Accepted File Extensions: **.xex .bin .a52**

Place your Atari 400,800,5200 ROMS in
```shell
/home/pi/RetroPie/roms/atari800
```
## BIOS
There are 5 main BIOS needed for the Atari800 emulator:

**ATARIXL.ROM** (BIOS for Atari XL/XE OS)

**ATARIBAS.ROM** (BIOS for the BASIC interpreter)

**ATARIOSA.ROM** (BIOS for Atari 400/800 PAL)

**ATARIOSB.ROM** (BIOS for Atari 400/800 NTSC)

**atari5200.rom** (BIOS for the Atari 5200)

Place these files in
```shell
/home/pi/RetroPie/BIOS
```
Once you have your ROMS and your BIOS files where they belong there is one more step of configurations needed where you tell the emulator where to look for your BIOS files.

Navigate to the Atari800 emulator on emulationstation and choose a game. A screen will open up with a bunch of different cartridge options. If you are playing a 5200 game then choose a 5200 cartridge option (Option #4 seems to work). You will then get a warning telling you that it needs a real Atari/OS. (you need to legally own the 5200 hardware to have the BIOS) Then press F1 to open the menu and navigate down to "Emulator Configuration" and press enter. Then navigate down to System ROM settings and then press Enter (Quick hint: use the escape button to go back up a step in the GUI)

The easiest option is to just select "Find ROM images in a directory" then navigate into the BIOS directory and press the space bar. If you have the right files and file names it should automatically place the BIOS files where they belong. 

Alternatively you can configure them manually:

For 400/800: 
      Custom OS ROM: select ATARIOSB.ROM in /home/pi/RetroPie/BIOS/ATARIOSB.ROM
      ROM_OS_A_PAL=  select ATARIOSA.ROM in /home/pi/RetroPie/BIOS/ATARIOSA.ROM
For XL/XE:
      BBO1 REV. 2: select ATARIXL.ROM in /home/pi/RetroPie/BIOS/ATARIXL.ROM
For 5200:
      Original: Select atari5200.rom in /home/pi/RetroPie/BIOS/atari5200.rom
For BASIC:
      Rev. C:  Select ATARIBAS.ROM in /home/pi/RetroPie/BIOS/ATARIBAS.ROM 

Then press escape a few times to go back to the "Emulator Settings" and select Save Configuration File or alternatively change Save configuration file on exit from no to yes

Then you can exit the emulator by pressing F9 and then try the game again or press shift+F5 to reboot the game.

if you can't seem to make it work that way, once you have tried to start a game and use F9 to exit the emulator a file called .atari800.cfg will be created in the /home/pi directory 

This is a verified working .atari800.cfg file     
```shell
Atari 800 Emulator, Version 3.1.0
ROM_OS_A_NTSC=
ROM_OS_A_PAL=/home/pi/RetroPie/BIOS/ATARIOSA.ROM
ROM_OS_B_NTSC=
ROM_OS_AA00R10=
ROM_OS_AA00R11=
ROM_OS_BB00R1=
ROM_OS_BB01R2=/home/pi/RetroPie/BIOS/ATARIXL.ROM
ROM_OS_BB02R3=
ROM_OS_BB02R3V4=
ROM_OS_CC01R4=
ROM_OS_BB01R3=
ROM_OS_BB01R4=
ROM_OS_BB01R59=
ROM_OS_BB01R59A=
ROM_5200=/home/pi/RetroPie/BIOS/atari5200.rom
ROM_5200_A=
ROM_BASIC_A=
ROM_BASIC_B=
ROM_BASIC_C=/home/pi/RetroPie/BIOS/ATARIBAS.ROM
ROM_XEGAME=
ROM_400/800_CUSTOM=/home/pi/RetroPie/BIOS/ATARIOSB.ROM
ROM_XL/XE_CUSTOM=
ROM_5200_CUSTOM=
ROM_BASIC_CUSTOM=
ROM_XEGAME_CUSTOM=
OS_400/800_VERSION=AUTO
OS_XL/XE_VERSION=AUTO
OS_5200_VERSION=AUTO
BASIC_VERSION=AUTO
XEGS_GAME_VERSION=AUTO
H1_DIR=
H2_DIR=
H3_DIR=
H4_DIR=
HD_READ_ONLY=1
PRINT_COMMAND=lpr %s
SCREEN_REFRESH_RATIO=1
MACHINE_TYPE=Atari XL/XE
RAM_SIZE=64
DEFAULT_TV_MODE=PAL
MOSAIC_RAM_NUM_BANKS=0
AXLON_RAM_NUM_BANKS=0
ENABLE_MAPRAM=0
DISABLE_BASIC=1
ENABLE_SIO_PATCH=1
ENABLE_H_PATCH=1
ENABLE_P_PATCH=1
ENABLE_NEW_POKEY=1
STEREO_POKEY=0
SPEAKER_SOUND=1
BUILTIN_BASIC=0
KEYBOARD_LEDS=0
F_KEYS=0
BUILTIN_GAME=0
KEYBOARD_DETACHED=0
1200XL_JUMPER=0
CFG_SAVE_ON_EXIT=1
MIO_ROM=
BLACK_BOX_ROM=
XLD_D_ROM=
XLD_V_ROM=
CARTRIDGE_FILENAME=
CARTRIDGE_TYPE=0
CARTRIDGE_PIGGYBACK_FILENAME=
CARTRIDGE_PIGGYBACK_TYPE=0
CARTRIDGE_AUTOREBOOT=1
CASSETTE_FILENAME=
CASSETTE_LOADED=0
CASSETTE_WRITE_PROTECT=0
RTIME=1
COLOURS_NTSC_SATURATION=0
COLOURS_NTSC_CONTRAST=0
COLOURS_NTSC_BRIGHTNESS=0
COLOURS_NTSC_GAMMA=0.3
COLOURS_NTSC_HUE=0
COLOURS_NTSC_GTIA_DELAY=26.8
COLOURS_NTSC_EXTERNAL_PALETTE=
COLOURS_NTSC_EXTERNAL_PALETTE_LOADED=0
COLOURS_NTSC_ADJUST_EXTERNAL_PALETTE=0
COLOURS_PAL_SATURATION=0
COLOURS_PAL_CONTRAST=0
COLOURS_PAL_BRIGHTNESS=0
COLOURS_PAL_GAMMA=0.3
COLOURS_PAL_HUE=0
COLOURS_PAL_GTIA_DELAY=23.2
COLOURS_PAL_EXTERNAL_PALETTE=
COLOURS_PAL_EXTERNAL_PALETTE_LOADED=0
COLOURS_PAL_ADJUST_EXTERNAL_PALETTE=0
ARTIFACT_NTSC=NONE
ARTIFACT_PAL=NONE
ARTIFACT_NTSC_MODE=0
SCREEN_SHOW_SPEED=0
SCREEN_SHOW_IO_ACTIVITY=1
SCREEN_SHOW_IO_COUNTER=0
SCREEN_SHOW_1200XL_LEDS=1
SOUND_ENABLED=1
SOUND_RATE=44100
SOUND_BITS=16
SOUND_FRAG_FRAMES=0
SOUND_LATENCY=20
VIDEO_FILTERING=1
VIDEO_ZOOM=1.00
SDL_JOY_0_ENABLED=1
SDL_JOY_0_LEFT=260
SDL_JOY_0_RIGHT=262
SDL_JOY_0_UP=264
SDL_JOY_0_DOWN=261
SDL_JOY_0_TRIGGER=305
SDL_JOY_1_ENABLED=0
SDL_JOY_1_LEFT=97
SDL_JOY_1_RIGHT=100
SDL_JOY_1_UP=119
SDL_JOY_1_DOWN=115
SDL_JOY_1_TRIGGER=306
```
## Controls
```shell
F1 Built in user interface
F2 Option key
F3 Select key
F4 Start key
F5 Reset key ("warm reset")
Shift+F5 Reboot ("cold reset")
F6 Help key (XL/XE only)
F7 Break key
F8 Enter monitor
F9 Exit emulator
F10 Save screenshot
Shift+F10 Save interlaced screenshot
Alt+R Run Atari program
Alt+D Disk management
Alt+C Cartridge management
Alt+Y Select system
Alt+O Sound settings
Alt+W Sound recording start/stop
Alt+S Save state file
Alt+L Load state file
Alt+A About the emulator
```
### Quick Tips for Gameplay:
```shell
Start Game: F4
Up: up or numpad 8
Down: down or numpad 2
Right: right or numpad 6
Left: left or numpad 4
Fire: RCTRL
Exit Emulator: F9
```
## Troubleshooting

* If it freezes up on you on the cartridge screen then try rebooting your pi and try again. If it keeps failing you either have the wrong BIOS, your ROM isn't compatible, or you chose the wrong cartridge option.
