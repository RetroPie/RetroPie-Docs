## Hardware and hardware setup. 

Nintendo 64 emulation requires at a bare minimum a Raspberry Pi 2 and a Raspberry  Pi 3 is highly suggested due to its increased performance. 

Suggested overclock for Raspi 3 for optimal N64 emulation (This to be paired with proper power, cooling, please see [this article](https://github.com/retropie/retropie-setup/wiki/Overclocking) for further information.)

```
#Overclock Settings
arm_freq=1300
gpu_freq=500
sdram_freq=500
over_voltage=6
v3d_freq=525
```

Of most important note of categories that most correctly benefit the Nintendo 64 is v3d_freq this is not a setting that when increased fails warranty or even really has a huge impact on heat but it has a great effect on higher performing emulators such as N64 and Dreamcast. 

Run Command
To learn the community tested optimal settings please view either of the 2 rom compatibility lists located [here](https://docs.google.com/spreadsheets/d/1Sn3Ks3Xv8cIx3-LGCozVFF7wGLagpVG0csWybnwFHXk/edit) or [here](
https://docs.google.com/spreadsheets/d/1Wjzbu90l6eCEW1w6ar9NtfyDBQrSPILQL5MbRSpYSzw/edit?usp=sharing).
From Retropie 4 and on Glide is the Default Emulator and render has been hard coded to 320x240. 
This can be scaled up for some games that perform really well like Mario kart and Super Mario 64 at your own discretion. 
If you wish to enable a High Resolution Texture pack you will want to select the Glide or Rice High Rez options under category 2. 


## CPU-Governor
The CPU governor can be throttled to max performance mode in one of two ways.

```
echo "performance" |sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
Or you can enable it from Runcommand  Go to Retropie-Setup - Setup and Configuration to be used post install - Configure the runcommand launch script - cpu configuration force performance
then cancel exit and reboot


## Notes on Audio
Audio

Use HDMI as composite requires more CPU usage.


## High Resolution texture packs
Special note on High Resolution texture packs, as of Retropie 4.2 mupen64plus.cfg is being overwritten when launched via runcommand so any changes that enabled hi-res will be reverted.  This is a bug and has been filed, https://github.com/RetroPie/RetroPie-Setup/issues/1983 
Also referenced in the support forum 
https://retropie.org.uk/forum/topic/10338/n64-hi-res-no-longer-working

I will leave the steps in the page as for now, but until the bug is addressed the functionality will not work, older versions such as 3.8 were not known to overwrite the mupen64plus.cfg


The steps for this are to change the configuration in 
```/opt/retropie/configs/n64/mupen64plus.cfg  ```
Replacing False for True in the Glide and Rice plugin
Make sure you have launched a rom with both Rice and Glide before going to edit the file or the variables will not be there to edit. 

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

You would then place high res texture packs in the directory `/home/pi/.local/share/mupen64plus/hires_texture`

Download the texture packs to that directory and then unzip them:
```
mkdir /home/pi/.local/share/mupen64plus/hires_texture
cd /home/pi/.local/share/mupen64plus/hires_texture

wget http://websitewithtexturepack/texturepack.zip
sudo unzip texturepack.zip
```


Texture packs are available for download [here](
http://textures.emulation64.com/index.php?id=downloads)

The folder name in that directory must match the core name in the rom header. 
Most cases the default directory name is ok but you may need to check if you find if your rom is not correctly launching the texture pack. 

To find that you can use the command to display the core name just use the command below in terminal then exit and scroll up I do it from a ssh session cause I can scroll up and read it.  But in the first few lines it will show the core name 
```
cd /home/pi/RetroPie/roms/n64
/opt/retropie/emulators/mupen64plus/bin/mupen64plus.sh mupen64plus-video-rice rom name
```

You can use the same command to launch the rom correctly loading the texture pack. 


To get the texture pack to load from emulation station you must do the following.
Launch Retropie Setup
Update Retropie Setup Script
Go to Manage Packages 
update the mupen64plus package

Go to launch one of the N64 games you have enabled a high resolution texture pack for. 
Launch that game
Press x when it launches 
change the video mode to one of the High Resolution options. Most likely mupen64plus-GlideN64-highres 
You can make that setting as the default for all 64 roms, which would be fine but likely as N64 stuff requires so much video tuning you will probably want to set this option on each rom you have uploaded a hi-resolution texture pack for. 


Please also feel free to reference the Rice 64 github page for the source documentation 
https://github.com/mupen64plus/mupen64plus-video-rice








Quality of Roms
There is a definite difference in some roms.  There are multiple versions of the SOTE rom some of which have noticeable stuttering and seizure screens but there are clean versions which play without the buggy effects.  I believe some of this could be due to the core name in the rom header not correctly matching what is in the .ini files for different plugins which apply different effects per game or could be as simple as bad rips which were never noticed on more powerful hardware. 

Overclocking past 1400
Well, not going to say its impossible but 1400 is the only stable option I can get after testing on about 8 different pi 3s.  


  







## Optimizations to mupen64plus.cfg

These are all experimental settings I am playing with

Glide

```
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
# This is currently set to True Investigating if setting to false will overload ram or not If texture cache is 500 by default is there enough overhead on ram to go with this setting.   
```

Rice 

```
# Use a faster algorithm to speed up texture loading and CRC computation
FastTextureLoading = True

# Enable this option to have better render-to-texture quality
DoubleSizeForSmallTxtrBuf = True
# A quality improver - need to verify any performance hit is negligible

# N64 Texture Memory Full Emulation (may fix some games, may break others)
FullTMEMEmulation = False
# What games does this fix?  Which ones does it break?

# Widescreen hack
WideScreenHack = True

# Fix aspect ratio?
```




