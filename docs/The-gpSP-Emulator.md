## BIOS file

The gpSP emulator needs a GBA BIOS file in the directory of the gpsp binary. The RetroPie SD-card image, e.g., has the gpsp binary located in /home/pi/RetroPie/emulators/gpsp/raspberry/. Copy your GBA BIOS file into this directory.

## Controller Setup

From [here](https://github.com/petrockblog/RetroPie-Setup/issues/193#issuecomment-19900909):

It appears that gpsp is not run via libretro thus its not configured like the rest of RetroArch. My solution was to run gpsp from command line with no arguments (sudo ./~/RetroPie/emulators/gpsp/raspberrypi/gpsp ) and configure my buttons through the onscreen menu there. This generated a gpsp.cfg file (binary).