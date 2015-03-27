This is the RetroPie SD-card image Version 3.0 BETA for Raspberry Pi 2.

CHANGELOG

* Overhaul of emulator selection / launching – single rom folder per
platform, with the facility to change default emulator per platform or
per rom on launch. Also allows launch of certain emulators with specific
configurations, such as render plugin for mupen64plus, and model
configuration for fuse.
* RetroArch render resolution is also configurable on launch. Video
output is no longer switched by default, but can be adjusted by the user
if needed.
* New retropie menu in EmulationStation with easy access to
retropie-setup, file manager, audio settings, controller settings,
raspi-config and so on.
* Emulationstation entries are now sorted (by name) – should mostly
match alphabetical order of rom folders.
* Work to ensure user configurations are preserved. More configuration
files moved to /opt/retropie/configs/ structure.
* EmulationStation restarts on exit by default unless a key is pressed.
Makes it easier for those that want to quick and let it restart to pick
up any new roms.
* New platforms.cfg file that contains emulator names / supported file
extensions. This can be copied to /opt/retropie/configs/all to override
extensions added to emulationstation (A reinstall / re-configuration of
the a related emulator is needed after to update the emulationstation
configuration)
* Addition of AdvanceMAME 1.2 (based on MAME 0.106) which may be useful
for rpi2 owners over the 0.94 version. Framebuffer output code adjusted
to work better with the Pi.
* rpix86 is included again by default (was missing from the last image).
* Updates to the usbromservice. If you want to sync rom folders it now
requires a folder in the root of the usb stick called “retropie”. The
roms will be synced from a sub folder called roms. It also can
backup/restore your custom emulationstation gameslists / data.
* RetroArch includes additional shaders and overlays
* Various other emulator updates and fixes.