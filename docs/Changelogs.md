# CHANGELOGS

This page is a list of all of the changelogs for each version of RetroPie. For a complete list of all commits to the source code see [here:](https://github.com/petrockblog/RetroPie-Setup/commits/master)  

### Version 3.0.0 BETA 4: (June, 18, 2015)

Work around issue with RetroArch GUI not accepting input/freezing.
Fixed up RetroArch control configuration via our new integrated input configuration.
Moved RetroArch joypad cofigurations to /opt/retropie/configs/all/retroarch-joypads

### Version 3.0.0 BETA 3: (June, 10, 2015)
* Integrated controls configuration for EmulationStation and RetroArch – On first start EmulationStation will ask for controls to be configured, and will then also configure RetroArch based on your choices. Note that there will be a delay after selecting OK whilst this is done – this will be improved later to give feedback so it doesn’t look as though EmulationStation has frozen.
* New experimental modules/emulators: limelight (Networked game streamer for Steam), lr-tgbdual (gameboy color emu with link support), DXX-Rebirth port (Decent 1/2), r-mednafen-wswan (Wonderswan emu), lr-mednagen-gbp (NeoGeo Pocket emu), uae4arm (Amiga emu), lr-fuse (ZX Spectrum emu), lr-caprice32 (Amstrad CPC emu), lr-gw (Game and Watch simulator). All modules prefixed with lr- are libretro cores for use with Retroarch.
* New startup picture with new RetroPie logo.
* Added additional ES theme “Color Pi”
* Dosbox bug fixes / Ability to launch custom shell scripts.
* Wifi configuration under RetroPie menu.
* PS3 controller setup improvements
* Various other fixes / improvements.

### Version 3.0.0 BETA 2: (April 4, 2015)

 * More launch options for Hatari
 * Resize framebuffer with video mode change (and allow framebuffer res to be changed independently for terminal/X apps)
 * Improvements to minecraft-pi launch script
 * Added some experimental modules – Adventure Game Studio engine, yabause (Sega saturn), virtualjaguar (Atari Jaguar), beetle-vb (Virtualboy), mgba (game boy advance)
 * Added ProSystem (Atari 7800 emulator)
 * Fixes to mupen64plus build
 * Various other fixes / Improvements

### Version 3.0.0 BETA (March 26, 2015)

* Overhaul of emulator selection / launching – single rom folder per platform, with the facility to change default emulator per platform or per rom on launch. Also allows launch of certain emulators with specific configurations, such as render plugin for mupen64plus, and model configuration for fuse.
* RetroArch render resolution is also configurable on launch. Video output is no longer switched by default, but can be adjusted by the user if needed.
* New retropie menu in EmulationStation with easy access to retropie-setup, file manager, audio settings, controller settings, raspi-config and so on.
* Emulationstation entries are now sorted (by name) – should mostly match alphabetical order of rom folders.
* Work to ensure user configurations are preserved. More configuration files moved to /opt/retropie/configs/ structure.
* EmulationStation restarts on exit by default unless a key is pressed. Makes it easier for those that want to quick and let it restart to pick up any new roms.
* New platforms.cfg file that contains emulator names / supported file extensions. This can be copied to /opt/retropie/configs/all to override extensions added to emulationstation (A reinstall / re-configuration of
the a related emulator is needed after to update the emulationstation configuration)
* Addition of AdvanceMAME 1.2 (based on MAME 0.106) which may be useful for rpi2 owners over the 0.94 version. Framebuffer output code adjusted to work better with the Pi.
* rpix86 is included again by default (was missing from the last image).
* Updates to the usbromservice. If you want to sync rom folders it now requires a folder in the root of the usb stick called “retropie”. The roms will be synced from a sub folder called roms. It also can backup/restore your custom emulationstation gameslists / data.
* RetroArch includes additional shaders and overlays
* Various other emulator updates and fixes.

### Version 2.6.0 (February 17, 2015)

* new uae4all emulator
* updated sdl 1.x with rpi fixes for fbcon and dispmanx backend.
* rpi2 optimisations for dosbox
* update hatari emulator
* jzintv updates
* mupen64plus/mupen64plus-libretro changes/fixes
* atari800 updates (with gles support on rpi)
* allow genesis libretro core to be used for mastersystem
* new experimental cores for gb advance (rpi2 only), and nes
* optimisation / fixes for rpi
* various other fixes / improvements

### Version 2.5.0 (February 7, 2015)

* Updated to latest firmware to support Raspberry Pi 2 (TM)
* Usb rom service should now be working
* updated all binaries
* mupen64plus is out of experimental
* added gpu_mem_1024 to config.txt
* removed overclocking settings
* simplified rom folder permissions
* removed ignore_safe_mode as safe mode is removed since march 2014

### Version 2.4.2 (January 17, 2015)

* reworked vice c64 emulator – defaults with dispmanx, but should run without now without also. Comes with a default config which is better
* suited for the pi. config now resides in /opt/retropie/configs/c64/ rather than home directory.
* retronet improvements – now can enable on game launch from runcommand menu.
* added vectrex libretro core
* always reset framebuffer even when not switching screen mode in runcommmand.sh which should help some emulators that seem to leave the framebuffer in an unusable state.
* fix for fmsx rom install
* use dispmanx sdl by default for uae4all
* use dispmanx sdl by default for dgen
* mame4all configs moved to /opt/retropie/configs/mame/ rather than mame4all (to match existing structure) 

### Version 2.4.1 (January 11, 2015)

* Minor bug fixes
* Updated RetroPie-Setup Script

### Version 2.4 (January 6, 2015)

* Update of all components, e.g., RetroArch supports ZIP files natively now
* Dispmanx can be activated or deactivated for each emulator individually now
* The screen mode is configurable for each emulator individually now
* Added Atari Lynx emulator
* Added Darkplaces Quake (experimental)
* Added Minecraft-Pi (experimental)
* Added OpenMSX (experimental)
* Enhanced integration of ScummVM
* Stripped down number of installed system packages to a minimum
* Several bug fixes
* Reorganization of the binaries
* Separation of sources and binaries

### Version 2.3 (July 20, 2014)

* Several bug fixes

### Version 2.2 (July 5, 2014)

* Added Mednafen PCE Fast
* Fixed configurations for sega32x, segacd
* Updated SAMBA configuration
* Fixed imame4all-rpi rom dir configuration
* Updated Python help scripts

### Version 2.1 (June 29, 2014)

* Fixed black screen when exiting to console
* Fixed Doom Shareware starter
* Removed hidden meta data files from FBA and Megadrive rome directory

### Version 2.0 (May 29, 2014)

* Reorganized folder structure (root dir is now /opt/retropie)
* Complete rebuild of all binaries with latest versions
* EmulationStation 2 as new front-end
* Added MSX emulator OpenMSX
* Refactored RetroPie-Setup Script with command line capabilities

### Version 1.10.1 (Dec 2, 2013)

* Updated Raspbian to the latest packages
* Updated the default splash screen
* Added x86 emulator FastDosbox

### Version 1.9.1 (November 12, 2013)

* Fixed “freezing” bug

### Version 1.9 (November 6, 2013)

* Added emulator Mame4All-RPi
* Added emulator Mupen64Plus-RPi
* Added splash screen configuration to RetroPie Setup Script
* Added configuration menu for RetroArch NetPlay to RetroPie Setup Script
* Enhanced debug log functionality of RetroPie Setup Script

### Version 1.8.1 (September 13, 2013)

* Added freezing fix for Emulation Station
* Re-added source-based installation function for PC-Engine Libretro core

### Version 1.8 (September 4, 2013)

* Added (Libretro based) Genesis emulator Picodrive
* Added emulator PiFBA
* Updated Emulation Station, x86 emulator, and RetroArch to latest release

### Version 1.7 (July 14, 2013)

* Added ES-Config
* Added Atari 2600 emulator Stella
* Updated Emulation Station, x86 emulator to latest releases

### Version 1.6.1 (June 12, 2013)

* Fixed GPSP binary

### Version 1.6 (June 5, 2013)

* Added emulator Basilisk II
* Added Dispmanx
* Updated every installable component
* Enhanced script for switching between resolutions

### Version 1.5 (May 5 2013)

* Added emulator gpSP
* Added emulator SNES9X-RPi
* Added emulator PiSNES
* Added GPIO gamepad drivers
* Updated Emulation Station
* Updated rpix86

### Version 1.4.1 (April 17, 2013)

* Updated Emulation Station
* Updated rpix86

### Version 1.4 (April 7, 2013)

* Added system-dependent change of HDMI video resolution for increased performance for RetroArch-based emulators.
* Added automatic USB ROM-copy service
* Added x86 emulator rpix86
* Added Apple ][ emulator Linapple
* Enhanced themes

### Version 1.3.1 (March 18, 2013)

* Minor changes in the file organization

### Version 1.3 (March 7, 2013)

* Added NXEngine / Cavestory
* Updated DGEN to version 1.32
* Enhanced pre-defined RetroArch input configuration

### Version 1.2.1 (February 25, 2013)

* Resized partition so that the image fits on 4 GB cards

### Version 1.2 (February 20, 2013)

* Added Intellivision emulator
* Added SAMBA share installation and configuration
* Used binaries-based setup for generating the SD-card image
* Updated themes

### Version 1.1 (February 10, 2013)

* Added AdvMAME emulator
* (Re-)added Genesis-GX RetroArch core
* Added Final Burn Alpha emulator