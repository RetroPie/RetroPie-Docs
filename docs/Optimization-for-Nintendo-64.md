##Hardware and hardware setup. 

Nintendo 64 emulation requires at a bare minimum a Raspberry Pi 2 and a Raspberry  Pi 3 is highly suggested do to it's increased performance. 

A note on overclocking A raspi 3 on default settings is comparable in speed to an overclocked raspi 2. 


Suggested overclock for Raspi 3 for optimal N64 emulation (This to be paired with proper power, cooling, please see https://github.com/retropie/retropie-setup/wiki/Overclocking for further information.

```
#Overclock Settings
arm_freq=1300
gpu_freq=500
sdram_freq=500
over_voltage=6
gpu_mem=256
```

The overclock settings are being adjusted to suit optimal operations.  Of most important note of categories that most correctly benefit the Nintendo 64 is v3d_freq this is not a setting that when increased fails warranty or even really has a huge impact on heat but it has a great effect on higher performing emulators such as N64 and Dreamcast. Clock and SDram speed also assist greatly in emulation.

##Run Command
The run command tool is very important to getting maximum possible performance from your N64 emulation. 
Firstly it allows for the selection of the most optimal plugin to play games.  For example Rice is the best plugin to play Zelda Games on as without it Majoras Mask will bug during the first few stages.  
Additionally Glide is the only plugin that will play Killer Instinct Gold at a playable level.   
It is also crucial to downscale video on games that are having heavy amounts of lag as this allows for less GPU strain and increases the playablity of the game.  So by default I suggest setting all emulators to use mode cea -1 and then define higher video settings to your liking on games that have very high performance ie(Mario Kart, Super Mario 64, etc)
To learn the community tested optimal settings please view either of the 2 rom compatibility lists located here
https://docs.google.com/spreadsheets/d/1Sn3Ks3Xv8cIx3-LGCozVFF7wGLagpVG0csWybnwFHXk/edit
or 
https://docs.google.com/spreadsheets/d/1Wjzbu90l6eCEW1w6ar9NtfyDBQrSPILQL5MbRSpYSzw/edit?usp=sharing
Top Link tracking more testing of Raspi 3 performance. 

##CPU-Govenor
The CPU govenor can be throttled to max performance mode in one of two ways.

```
echo "performance" |sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
Or you can enable it from Runcommand  Go to Retropie-Setup - Setup and Configuration to be used post install - Configure the runcommand launch script - cpu configuration force performance
then cancel exit and reboot


##Note's on Audio
Audio

Use HDMI as composite requires more CPU usage.





## High Resoltuion texture packs
The steps for this are to change the configuration in 
```/opt/retropie/configs/n64/mupen64plus.cfg  ```
Replacing False for True in the Glide and Rice plugin

Glide Line
```
# Use high-resolution texture packs if available.
txHiresEnable = False
```
Rice Line
```
# Enable hi-resolution texture file loading
LoadHiResTextures = False
```

You would then place high res texture packs in the directory

/home/pi/.local/share/mupen64plus/hires_texture

Texture packs are available for download here 
http://textures.emulation64.com/index.php?id=downloads

The folder name in that directory must match the core name in the rom header. 

To find that you can use the command to display the core name just use the command below in terminal then exit and scroll up I do it from a ssh session cause i can scroll up and read it.  But in the first few lines it will show the core name 
```
cd /home/pi/RetroPie/roms/n64
/opt/retropie/emulators/mupen64plus/bin/mupen64plus.sh mupen64plus-video-rice rom name
```

You can use the same command to launch the rom correctly loading the texture pack. 


However if you load up emulation station and use the normal run command launcher it will fail or only partially load the texture pack a issue is open on this subject and will update when it is working correctly.  
Correction to this behavior.  It seems that texture packs will not load correctly when downscaling video to something standard like 640x480 that resolution is not high enough to run the texture pack.  If you have Cea-5 enabled you can launch the texture pack normally via emulation station. 





##Research for further improvments
(Run mupen64plus using sudo/root so that it can change its scheduler policy to 'hog' the CPU)
Test and confirm this behavior has any effect, and if this boost is cancelled out or equaled to setting the cpu cores to performance mode.

(Use 128Mb GPU/CPU memory split. The current code doesn't force the kernel to keep pages in ram so if the split is too high, then pages will be swapped and slow emulation down. (Fix coming soon))
The above comment was from a dev in April of 2014 no update was given as to wether the update was successfull or patched.  Seems to be written for a 256 memory pi and if an even memory split would be applicable.  So more research into if page swapping is happening , if anyone knows how to test if page swapping is intiated please update.  

Quality of Roms
There is a definite difference in some roms.  There are multiple versions of the SOTE rom some of which have noticeable stuttering and seizure screens but there are clean versions which play without the buggy effects.  I believe some of this could be due to the core name in the rom header not correctly matching what is in the .ini files for different plugins which apply different effects per game or could be as simple as bad rips which were never noticed on more powerfull hardware. 

Overclocking past 1400
I believe that the pi 3 can take a higher overclock and that power not heat is the bottleneck here.  Currently awaiting shipment of a 3000 ma charger to attempt more voltage to the chip to get past 1400 clock speed. 


vire_refresh / fullspeed screen rate in mupen64plus.cfg
Continue research as to why increasing options like vire_refresh and full screen framerate in the standalone config file seems to increase performance in plugin loaded non standalone application even though those configs are not supposed to apply to plugin versions.  


Additionally need to research and test optimum video modes, and full screen scaling as well as Anti-Aliasing and its effect or benefit. 





##Optimizations to mupen64plus.cfg

Thesse are all experimental settings I am playing with

Glide

# Size of texture cache in megabytes. Good value is VRAM*3/4
CacheSize = 900


# Enable N64 depth compare instead of OpenGL standard one. Experimental.
EnableN64DepthCompare = True

# Use high-resolution texture packs if available.
txHiresEnable = True
# Allow to use alpha channel of high-res texture fully.
txHiresFullAlphaChannel = True



# Save texture cache to hard disk.
txSaveCache = True
This is currently set to True Investigating if setting to false will overload ram or not If texture cache is 500 by default is there enough overhead on ram to go with this setting.   





Rice Settings
# Use a faster algorithm to speed up texture loading and CRC computation
FastTextureLoading = True

# Enable this option to have better render-to-texture quality
DoubleSizeForSmallTxtrBuf = True
A quality improver  need to verify any performance hit is negligible



# N64 Texture Memory Full Emulation (may fix some games, may break others)
FullTMEMEmulation = False
What games does this fix?  Which ones does it break?

# Widescreen hack
WideScreenHack = True

Fix aspect ratio?




