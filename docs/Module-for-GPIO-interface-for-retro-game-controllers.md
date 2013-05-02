# Overview

The module for retro game controllers allows connecting various home computer joysticks and console gamepads to Raspberry Pi via GPIO, with minimal amount of extra hardware. The module consists of 2 drivers, which each support different types of controllers:

[gamecon_gpio_rpi](gamecon_gpio_rpi):
* NES gamepads
* SNES gamepads and mouses
* PSX/PS2 gamepads, wheels and DDR controllers
* N64 controllers
* Gamecube controllers

[db9_gpio_rpi](db9_gpio_rpi):
* Atari, Commodore, Amiga etc. db9 multisystem joysticks
* Sega Mega Drive (Genesis) pads
* Sega Saturn controllers (Note: custom connector instead of db9)
* Amiga CD32 pads


# Installation

The easiest way to install the drivers is via RetroPie-script, by selecting "Install/update multi-console gamepad drivers for GPIO" option in the setup section.
Alternatively, .deb-packages for the drivers and kernel headers can be directly downloaded [here](http://www.niksula.hut.fi/~mhiienka/Rpi/)


# Configuration

The drivers are loaded/unloaded with _modprobe_. More information and connection diagrams are found in the driver sub-pages and in provided READMEs.