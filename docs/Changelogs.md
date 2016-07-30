# CHANGELOGS

This page is a list of all of the changelogs for each version of RetroPie. For a complete list of all commits to the source code see [here:](https://github.com/petrockblog/RetroPie-Setup/commits/master)  

### Version 4.0 RC1: (July 23, 2016)

   - Setup script improvements:
       - Added the ability to install/update and remove packages.
       - Added help docs to the setup script.
   - Renamed mednafen emulators to beetle to match upstream libretro repositories.
   - Renaming of ES input configuration which was causing confusion for shoulder/trigger inputs.
   - Input configuration script to set up player 1 automatically on pifba.
   - Updated PSP emulators ppsspp and lr-ppsspp with a fix for the pausing during play.
   - Autostart improvements: boot to kodi option added - (exiting kodi will take you back to emulationstation).
   - Improvements to mupen64plus Glide64 video plugin, which is now the default.
   - Updates to various other emulators including reicast, lr-fceumm, lr-nestopia, lr-snes9x-next and the RetroArch frontend.
   - SDL2 dispmanx scaling, so SDL2 software can render to a lower resolution and be scaled in hardware. This enhances performance on mupen64plus for example, without having to change the video mode.
   - Improvements to the bluetooth configuration, including the ability to try and reconnect to devices in the background, and an option to switch off our mapping hack for 8bitdo, so devices with a newer firmware will work correctly with retroarch.
   - Splashscreen improvements: New default splashscreen thanks to rookervik and a new splashscreen repository with more splashscreens.
   - New experimental modules:
       - TRS-80 emulator sdltrs.
       - TI-99/4A emulator ti99sim.
       - Oric 1/Atmos emulator Oricutron.
       - Dinothawr (lr-dinothawr - standalone libretro puzzle game).
       - Alternate Virtual Gamepad by sbidolach.
   - Various other bugfixes and improvements.

### Version 4.0 BETA 2: (June 21, 2016)
   - Setup script improvements:
       - Added the ability to install/update and remove packages.
       - Added help docs to the setup script.
   - Renamed mednafen emulators to beetle to match upstream libretro repositories.
   - Input configuration script to set up player 1 automatically on pifba.
   - Updated PSP emulators ppsspp and lr-ppsspp with a fix for the pausing during play.
   - Autostart improvements: boot to kodi option added - (exiting kodi will take you back to emulationstation).
   - Improvements to the bluetooth module.
   - Splashscreen improvements: New default splashscreen thanks to rookervik and a new splashscreen repository with more splashscreens.
   - New experimental modules:
       - TRS-80 emulator sdltrs.
       - TI-99/4A emulator ti99sim.
       - Oric 1/Atmos emulator Oricutron.
       - Dinothawr (lr-dinothawr - standalone libretro puzzle game).
       - Alternate Virtual Gamepad by sbidolach.
   - Various bugfixes and improvements.

### Version 3.8.1: (June 4, 2016)
 - Fix escaping in iniSet causing initial backslashes to be incorrect in ini files (Affected some +Start Scripts with spaces such as DOSBox).
 - Don’t overwrite existing configs when updating advmame.
 - SSelph’s scraper – Add option to set -append and -use_nointro_name=false flags
 - Disable binary install on Wheezy.
 - Fix building of gamecondriver.
 - Correct Emulation Station autobooting configuration due to changes in raspi-config.
 - Added missing zip dependency for Solarus.
 - Fix c&p error with mupen64plus that broke the initial config generation.
 - Added new EmulationStation theme “material” from user lilbud.
 - Lr-nxengine – no error message was shown when required data files are missing.

### Version 3.8: (May 27, 2016)
 - Raspbian package/firmware rollups that fix the lockups with the Raspberry Pi 3 internal bluetooth.
 - New SDL1 dispmanx backend from Vanfanel with triple buffering which should solve some of the performance issues on the previous code. Also some additional changes are included so you can adjust the aspect ratio with env variable SDL_DISPMANX_RATIO (eg 1.33 for 4:3). The aspect ratio will be ignored if SDL_DISPMANX_IGNORE_RATIO is set and sdl1 apps will display full screen. Vice is now set to use 4:3 ratio on the Raspberry Pi.
 - Reicast (Dreamcast emulator), now supports multiplayer.
 - lr-pcsx-rearmed (PlayStation emulator) now supports 3-8 players.
 - Updated Raspberry Pi binaries for lr-fba-next, uae4arm, mupen64plus, Reicast, lr-picodrive, lr-nestopia, lr-pcsx-rearmed, lr-mgba, lr-genesis-plus-gx, lr-mame2003, and lr-fceum.
 - Added new videocore mupen64plus video plugin.
 - Improvements to Apple2 (supports automount now).
 - Added wiki viewer.
 - Improvements to the splashscreen module (added previewer, randomiser, and no longer requires a folder to be created in the splashscreen directory).
 - Various other bugfixes and minor improvements.

### Version 3.7: (April 14, 2016)

- Added new experimental modules: 
  - The Ur Quan Masters  (Port of DOS game Star Control 2).
  - Xrick (Port of Rick Dangerous).
  - Tyrquake (Standalone, not libretro).
  - Solarus Engine (Homebrew Zelda Clone).
  - SDLPoP (Prince of Persia Port).
  - Cannonball (Outrun Engine).
  - Stratagus (Warcraft and Starcraft Engine).
  - OpenBOR (Beats of Rage 2d Sidescrolling Game Engine).
  - Commander Genius (Port of Commander Keen).
  - Micropolis (Open source version of Sim City Classic).
  - Aleph One (Open Source port of Marathon Series).
  - Giana’s Return (Fan-Made sequel to the Giana Sisters).
  - Lincity (Sim City Clone).
  - Simcoupe (SAM Coupé Emulator).
- LXDE Desktop (Option in raspi-tools to reinstall the desktop environment).
- Updated Kodi to Kodi 16 (which includes joypad support).
- Updated PS3 Module (timeout fixed).
- SDL2 PS3/Wii U Pro controller fixes.
- UAE4Arm updated.
- lr-mame2003 updated with sample/nvram support and additional core settings.
- Mupen64plus updated with fix for black screen with rice plugin.
- Scummvm Improvements (updated to 1.8 with OpenGL and partial Myst support).
- Updated Config Editor (https://github.com/RetroPie/RetroPie-Setup/wiki/Configuration-Editor).
- Updated Carbon and Pixel Themes and added default images to the RetroPie Menu.
- Added “Other Settings” menu to Emulationstation with “save metadata on exit” and “parse gamelists only”. These options were added to mitigate the long boot and shutdown times with large romsets.
- Various other improvements and fixes.

### Version 3.6: (March 1, 2016)

**Added Support for the Raspberry Pi 3 [Via Raspbian Firmware Update]**

- Added new experimental modules:
 - Daphne (Laserdisc Emulator)
 - Libretro-QuickNES
 - Libretro-Beetle PSX (x86 only)
 - Libretro-Beetle Lynx
 - GemRB engine (Baldur’s Gate, Icewind Dale, Planescape)
 - ResidualVM (Engine for Grim Fandango and Escape from Monkey Island)
 - Libretro-MESS (based on the most recent version of MAME)
 - Libretro-MAME (based on the most recent version of MAME)
- Added EmulationStation theme Simpler Turtle Pi to the theme installer from Omnija.
- Added version details and uninstall option to the RetroPie Setup Script.
- Fixed insert coin not working on arcade based emulators.
- Various other bugfixes and improvements.

### Version 3.5: (February 6, 2016)

After taking into consideration the feedback from the vibrant RetroPie community, we have provided a few more functions to simplify the user experience such as automatic expansion of the filesystem on boot, less terminal text, and more configuration options for the runcommand launch menu. We have also fixed up some bugs with Raspbian Jessie such as the USB ROM service and have added two new experimental modules - the Löve game engine and a ColecoVision emulator (CoolCV). 

 - Added new experimental modules, Lӧve 2D Game Engine, Colecovision (CoolCV).
 - Debian usbmount package fixed up for systemd udev compatibility, making the USB ROM service work properly again without being killed after 30 seconds. Also added ntfs support by default.
 - Added an arcade rom folder option where all arcade games can be placed. 
 - Improvements to EmulationStation (Fix crash on rom delete, direct launch, symlink support, and other bug fixes).
 - Improvements to the Runcommand Launch Menu: Cleaner dialog on launch, ability to show game artwork on launch, ability to disable joystick support as well as the ability to disable the entire runcommand launch menu.
 - PS3 Controller improvements - Add multiple gasia and shanwan controller support.
 - Updated lr-mgba emulator binaries (new upstream release of mgba 0.4.0)
 - Improvements on pre-built image - disabled screen blanking, quieter boot, and filesystem automatically expanded on first boot.
 - Various other bug fixes.

### Version 3.4: (January 19, 2016)

Mostly fixes and improvements rather than new stuff this time folks. There were some problems with our RetroArch configuration defaults in RetroPie 3.3 which should be sorted now, and we have fixed up a few things that didn’t work correctly with Raspbian Jessie. We also have added early support for using the RetroPie-Setup script on a X86/X11 desktop setup, as well as some basic support for building EmulationStation & RetroArch + cores on the ODroid-C1. For more information regarding installation on x86 see https://github.com/RetroPie/RetroPie-Setup/wiki/RetroPie-Ubuntu-15.10-x86-Flavor.

We are now using Raspbian Jessie as the base for the RetroPie image. Those using Wheezy can update RetroPie-Setup and emulators by following the instructions at https://github.com/RetroPie/RetroPie-setup/wiki/Updating-RetroPie - however moving to Jessie is recommended. As it takes time to pre-build binaries, in the future we will only be providing pre-built binaries for Raspbian Jessie.

Changes since 3.3:

- Now using Raspbian Jessie for the RetroPie image. 
- Fixes for controller input issues with RetroArch including improved config generation to work around problems with 8bitdo controllers.
- Fixed up Bluetooth pairing module on Jessie.
- Improvements to the Xbox userspace driver (xboxdrv) including partial support of Xbox One controller.
- Can now choose to exit or restart Emulation Station. Metadata will no longer be lost if choosing to shutdown or reboot.
- Preliminary support for using the RetroPie-Setup script on x86 + X11 on Debian/Ubuntu and Ubuntu on the Odroid-C1 (building from source only).
- $HOME/.emulationstation has relocated to /opt/retropie/configs/all/emulationstation - but is symlinked from the original location. The USB Rom Service script will backup all of /opt/retropie/configs to USB. Previously it only backed up /$HOME/.emulationstation.
- Support for choosing RetroArch shaders and overlays from the RetroPie-Setup configuration editor.
- Added pixel theme from Rookervik to theme installer.
- Wonderswan and NeoGeo Pocket separated into Wonderswan/Wonderswan Colour, NeoGeo Pocket/NeoGeo Pocket Colour. 
- Various other bugfixes and improvements.

### Version 3.3: (December 21, 2015)

- Mupen64plus controller configs (including hotkeys) and Reicast (Dreamcast) controller configs added to the autoconfiguration script in emulationstation. Mupen64plus is now the default n64 emulator due to compatibility.
- AdvanceMAME 1.4 (replaces 1.2 - still based on MAME 0.106).
- PlayStation Portable emulator ppsspp is included by default (libretro version is default, the standalone version is optional).
- Removed cpc4rpi emulator, and added CapriceRPI which has many improvements over cpc4rpi.
- Updated libretro binaries including lr-fba-next updated to v0.2.97.37, and an improved lr-caprice32 which is now moved out of experimental and is the default Amstrad CPC emulator.
- Updates to Reicast emulator, which has been moved out of experimental.
- New experimental modules: OpenTTD (open source simulation game based on Transport Tycoon Deluxe), Wolf4SDL (Port of Wolfenstein 3d), Zdoom (Enhanced Port of the official DOOM source)
- PS3 controller improvements (added Gasia PS3 clone Support).
- Updated OpenMSX emulator (to the dev version 0.12.0+).
- Beta images based on Raspbian Jessie are included. They may have bugs that are not present in the Raspbian Wheezy release.
- New themes added to the theme installer (Eudora from AmadhiX, Tronkyfran from Tronkyfran, and Retroplay Canela from InsecureSpike).
- RetroArch joy-config tool removed (custom configs are now done through the RGUI or manually).
- Various other bugfixes/improvements.


### Version 3.2.1: (October 28, 2015)

- Fixes issues with controller d-pad configurations for all RetroArch-based emulators.

### Version 3.2: (October 26, 2015)

- Fixed binaries of mupen64plus and lr-tyrquake and removed mupen64plus-testing as it is now included in the default mupen64plus.
- Updated to Hatari 1.9, and built in IPF image support.
- Binary installs are now supported for those running under Raspbian Jessie - although there still may be bugs.
- New experimental modules - ppsspp / lr-ppsspp (PlayStation Portable emulator), px68k (X68000 emulator - too slow to be usable on a rpi2 though), opentyrian (a port of the DOS shoot-em-up Tyrian), and SuperTux.
uae4arm is now moved from experimental.
- Improvements to the generic bluetooth pairing module.
- Improvements to ps3controller pairing
- Fixed SNESDev driver building (failed on first attempt).
- New Turtle Pi Emulation Station theme installable via the themes installer
- GLideN64 video plugin for mupen64plus
- Various other bugfixes.

### Version 3.1: (October 6, 2015)

* Workaround for lr-snes9x-next crashes for certain games.
* New theme installation script and excellent new theme “Carbon” which is lighter on memory than the Simple theme (no more white screen of death! - works with all systems).
* Initial bluetooth module for pairing keyboards.
* We now provide images for use with Berryboot.
* Moved Super Mario War out of experimental.
* New default lr-fba-next emulator for rpi2 owners.
* Added lr-mame2003 (based on MAME 0.78) emulator.
* Minor Emulation Station tweaks, reduced time to skip buttons, and improved parsing with brackets in gamelists.
* New experimental modules - sselph’s scraper and lr-mame2010 (based on MAME 0.139)
Improved ps3 controller pairing.
* Initial support for installing RetroPie manually on Raspbian Jessie and OSMC (via source only - consider this experimental for now).
* Splashscreen improvements- can be added from samba shares, splash videos play all the way through without emulationstation cutting them off.
* Lots of bugfixes, and improvements to the RetroPie Wiki.

### Version 3.0.0 Stable : (August 11, 2015)

* New GUI for basic WiFi configuration and Config editing
* Added Dragon 32 / TRS-80 (CoCo) emulator xroar
* Added Super Mario War to ports
* Move some emulators out of experimental – lr-bluemsx (Now default for msx), lr-mednafen-ngp, lr-mednafen-wswan, lr-mgba, lr-tgbdual, lr-vba-next
* Added virtualgamepad to experimental which allows gamepad emulation via a mobile
* Restarting setup script no longer needed after updating the setup script.
* Improved support for video splashscreens and a centralised splashscreen repo (https://github.com/RetroPie/retropie-splashscreens)

### Version 3.0.0 RC1: (July 18, 2015)

* Input configuration improvements / fixes / optimisations
* Basic joypad control in RetroPie-Setup / emulator prelaunch menus.
* Make libretro Fuse default spectrum emulator (for easier joypad control)
* Added new spectrum emulator ZEsarUX to the experimental section.
* Added launching RetroArch with RGUI from the RetroPie menu in EmulationStation.
* Various other bugfixes – you can follow changes as they happen on the GitHub site –https://github.com/RetroPie/RetroPie-Setup/commits/master

### Version 3.0.0 BETA 4: (June 18, 2015)

* Work around issue with RetroArch GUI not accepting input/freezing.
* Fixed up RetroArch control configuration via our new integrated input configuration.
* Moved RetroArch joypad cofigurations to /opt/retropie/configs/all/retroarch-joypads

### Version 3.0.0 BETA 3: (June 10, 2015)
* Integrated controls configuration for EmulationStation and RetroArch – On first start EmulationStation will ask for controls to be configured, and will then also configure RetroArch based on your choices. Note that there will be a delay after selecting OK whilst this is done – this will be improved later to give feedback so it doesn’t look as though EmulationStation has frozen.
* New experimental modules/emulators: limelight (Networked game streamer for Steam), lr-tgbdual (gameboy color emu with link support), DXX-Rebirth port (Decent 1/2), r-mednafen-wswan (Wonderswan emu), lr-mednagen-gbp (NeoGeo Pocket emu), uae4arm (Amiga emu), lr-fuse (ZX Spectrum emu), lr-caprice32 (Amstrad CPC emu), lr-gw (Game and Watch simulator). All modules prefixed with lr- are libretro cores for use with Retroarch.
* New startup picture with new RetroPie logo.
* Added additional ES theme “Color Pi”
* Dosbox bug fixes / Ability to launch custom shell scripts.
* Wifi configuration under RetroPie menu.
* PS3 controller setup improvements
* Disabled root password by default
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