GnGeo-RPi can be installed via the RetroPie Setup Script. You can find more information in the wiki at https://github.com/ymartel06/GnGeo-Pi/wiki.


Retropie has 2 versions of gngeo (neogeo emulator).
Disregard the older version (0.7), its too old and buggy.
When using roms for the gngeo-pi-0-85 you need 3 steps.

1 – You must put the bios files (extracted) in the rom folder and in the neogeobios folder (/home/pi/RetroPie/emulators/gngeo-pi-0.85/neogeobios/). You can find bios files (neogeo.zip and unibios.zip) in google.

2 – You also need gngeo_data.zip file in the installdir/share/gngeo folder. Search google also for this file. The files inside this zip are .drv. You can only play roms that have the same name as these .drv files, e.g. mslug2.zip (rom) and mslug2.drv (data). If the names of these files dont match the game will crash.

3 – Also make sure the /home/pi/.gngeo/gngeorc file exists (this is the file you edit for configurations, joypad etc).



## Location of the file neogeo.zip

The file `neogeo.zip` has to be located in the same directory as where the ROMs are located (see also https://github.com/petrockblog/RetroPie-Setup/issues/219#issuecomment-24192844).