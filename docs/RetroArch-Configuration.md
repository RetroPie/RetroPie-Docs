All RetroArch based emulators can be configured in the following way:

**Global** settings - that are settings which should apply to all systems - are done in the file 

    ROOTDIR/configs/all/retroarch.cfg

Here, ROOTDIR is the folder of the RetroPie installation, e.g., /home/pi/RetroPie/. 

**System-specific** settings are done in the files 

    ROOTDIR/configs/SYSTEMNAME/retroarch.cfg

Here, SYSTEMNAME is atari2600, snes, etc.. All settings in these files will overwrite the corresponding global setting.