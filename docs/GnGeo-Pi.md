GnGeo-RPi can be installed via the RetroPie Setup Script. You can find more information in the wiki at https://github.com/ymartel06/GnGeo-Pi/wiki.

When using roms for gngeo you need 3 steps.

1 – You must put the bios file neogeo.zip in the rom folder.

2 – gngeo has a gngeo_data.zip file in the installdir/share/gngeo folder. The files inside this zip are .drv. You can only play roms that have the same name as these .drv files, e.g. mslug2.zip (rom) and mslug2.drv (data). If the names of these files dont match the game will crash.

3 – Also make sure the /home/pi/.gngeo/gngeorc file exists (this is the file you edit for configurations, joypad etc).