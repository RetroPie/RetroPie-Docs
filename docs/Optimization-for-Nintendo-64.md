## READ FIRST - Why N64 emulation on the Pi is difficult

N64 emulation on the raspberry pi is difficult due to the pi's under powered GPU (Graphics Processing Unit) and lack of certain GPU features found in more modern devices. For a more detailed explanation please see [this post](https://www.reddit.com/r/RetroPie/comments/6se5nj/why_n64_emulation_on_the_pi_isnt_so_great_from_a/) by a mupen64plus developer. 

If you are looking for a more perfect N64 emulation experience you should seriously consider different hardware first (i.e. a desktop computer, modern mobile phone/tablet etc.). However, listed below are several tweaks that can be made to your raspberry pi that will help maximize N64 performance and make many of the popular N64 titles playable. 

## Hardware and Configuration 

A Raspberry Pi 3 is highly suggested to maximize performance

### Overclocking

**Overclocking should only be attempted by advanced users who understand the risks. An unstable overclock will lead to freezing, crashing and SD card corruption. Back up your image before attempting to overclock. Proceed at your own risk!**

**NOTE** Setting any overclocking parameters to values other than those used by raspi-config may set a permanent bit within the SoC, making it possible to detect that your Pi has been overclocked. The specific circumstances where the overclock bit is set are if force_turbo is set to 1 AND any of the over_voltage_* options are set to a value > 0. Setting the overclock bit can void your warranty.

Overclocking is setting a hardware component to run faster than originally intended by the manufacturer. It can add instability if not done properly. It will also make your pi run hotter. There are no standard settings for overclocking and not all pis will handle the same amount of overclocking. Therefore before you begin overclocking please review [this article](https://github.com/retropie/retropie-setup/wiki/Overclocking) first for proper overclocking methods and stability testing to prevent SD card corruption and potential loss of your data.

For boosting N64 performance, it is the```core_freq```(GPU core) setting that will give the most benefit. Most pis I tested were stable between ```core_freq=500``` and ```core_freq=575``` with some amount of ```over_voltage``` applied. Again, it is important to remember that not all pis are equal, some will only overclock a little or not at all. You will need to experiment to see how much your pi can handle. If your pi freezes or crashes then your overclock is unstable. 

Overclocking ```sdram_freq``` will give a very small boost to performance. Going from 450mhz to 550mhz yielded at best about a 1FPS increase. Sdram has its own over voltage value ```over_voltage_sdram```. 

```v3d_freq```can also be overclocked. This helped improve performance for a couple games I tested. Most of the raspberry pis I tested were stable to at least ```v3d_freq=500``` but not much past this.

```arm_freq```(CPU) overclocking is of little to no help for boosting N64 performance on a pi3. There was no discernible FPS increase overclocking the Pi 3b's CPU from the standard 1200mhz to 1350mhz. Though it may help increase performance for other high CPU usage emulators such as PSX or MAME. Overclocking ```arm_freq``` may benefit pi 1, 2 and zero models for some N64 games but offers no benefits for the pi3b or pi3b+.

### CPU-Governor

The CPU governor controls when your overclock is applied. With the cpu-governor set to performance mode your pi will run at full speed while running ROMs but will down-clock when sitting idle in Emulation Station. You can enable it from the retropie setup menu. In Emulation Station go to Retropie-Setup - Setup and Configuration to be used post install - Configure the runcommand launch script - cpu configuration - force performance
then cancel, exit and reboot.

## Selecting the Correct Emulator and Graphics Plugin

Just as important as overclocking, selecting the right emulator/graphics plugin from the [runcommand](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand) menu on a per game basis will also increase performance. Selecting the right plugin can make all the difference in making a game playable. 

To learn the community tested optimal settings please view either of the two rom compatibility lists located [here](https://docs.google.com/spreadsheets/d/1Sn3Ks3Xv8cIx3-LGCozVFF7wGLagpVG0csWybnwFHXk/edit) or [here](
https://docs.google.com/spreadsheets/d/1Wjzbu90l6eCEW1w6ar9NtfyDBQrSPILQL5MbRSpYSzw/edit?usp=sharing). (rom compatibility lists are a mess and all are in need of retesting). Do not accept these lists as 100% accurate as they are community maintained and with updates may change over time. There may be some inaccuracies so it is best just to use the lists as a general starting point. Some games listed as unplayable have with recent updates become playable and vice versa. The current default emulator is mupen64plus-auto which will attempt to select the correct graphics plugin for you, however for best results it is best to test each plugin for yourself on a per game basis. It is recommended that you confirm a game runs well with the standard low-res plugin before attempting to use the hi-res option. 

Each N64 emulator/video plugin should be set to the lowest resolution (CEA-1 for most displays) through the runcommand menu. This will slightly increase performance by limiting the up-scaling the pi has to perform. This is not necessary for the gles2n64 video plugin.

**NOTE** The gliden64 video plugin currently has issues with frame buffer emulation on the pi that causes visual glitches which lead to a crash after about 10-20 mins of playtime. A recent update has taken care of this issue so it is highly recommended that you update mupen64plus to the latest version.


## Notes on Audio
The SDL audio plugin produces less audio drop out and makes for an improved experience over the OMX audio plugin. Previously, the SDL audio plugin produced an audio crackling that was undesirable. With recent updates the audio crackle has been fixed so it is now fine to use SDL audio. To switch to the SDL audio plugin you should first update your mupen64plus emulator to the latest version. Then navigate to: ```/opt/retropie/configs/all/autoconf.cfg``` and make sure that ```mupen64plus_audio = "0"```

As a side benefit from using the SDL audio plugin, save/load states will now function properly with mupen64plus.

I believe this section to be obsolete, and in need of audit. Retropie builds have newer versions of mupen64plus and this config flag is already set. 

## High Resolution Texture Packs

From Current version forward Hi Resolution Texture options are automatically configured to True in the configuration files for Rice and Glide.  You should not need to modify them as you did with previous versions.  Some libretro emulators support loading Hi-Rez textures and you can look for enabling those options in the libretro xmb.  


You need to place high res texture packs in the directory `/home/pi/.local/share/mupen64plus/hires_texture`

Download the texture packs to that directory and then unzip them:
```
mkdir /home/pi/.local/share/mupen64plus/hires_texture
cd /home/pi/.local/share/mupen64plus/hires_texture

wget http://websitewithtexturepack/texturepack.zip
sudo unzip texturepack.zip
```


Texture packs are available for download [here](
http://textures.emulation64.com/index.php?id=downloads)

The folder name in that directory must match the core name in the rom header or the texture pack will not be properly applied.  
Most cases the default directory name is ok but you may need to check if you find if your rom is not correctly launching the texture pack. 

Here is a list of the proper format of names for the top level folder on texture packs I have tested
F-ZERO X
MARIOKART64
PAPER MARIO
SMASH BROTHERS
STARFOX64
SUPER MARIO 64
THE LEGEND OF ZELDA
WAVE RACE 64
ZELDA MAJORA'S MASK


To confirm the correct name for a texture pack you may not be able to get to load  you can use the command to display the core name just use the command below in terminal then exit and scroll up I do it from a remote ssh session like putty cause you can scroll up and read it.  In the first few lines it will show the core name 
```
cd /home/pi/RetroPie/roms/n64
/opt/retropie/emulators/mupen64plus/bin/mupen64plus.sh mupen64plus-video-rice rom name
```

You can use the same command to launch the rom correctly loading the texture pack. 

Two things you need to do once you have texture packs placed in the proper directory and named correctly. 

You need to make sure you are launching that rom specifically with either Glide or Rice (maybe libretro if you have enabled libretro specifically to load hi rez textures)
and
You need to make sure you are using a resolution at 800x600 or higher in order for the texture pack to load.  You should use the highest resolution setting you can get the game performing well on it will look better the higher the resolution.


Please also feel free to reference the Rice 64 github page for the source documentation 
https://github.com/mupen64plus/mupen64plus-video-rice



## Raspberry Pi 4
The Raspberry Pi 4 has much improved hardware.  But it is still early in its development.
Overclocking is possible on a Raspberry Pi 4 and as always offers a better N64 emulation experience.  
Please use the latest unofficial build until such point as an official build is made available. 
You can check for the latest build here, 
https://files.retropie.org.uk/images/weekly/

It is important to install and update from source as development is usually adding things that will help with your emulation of the N64

To get to 2.0 GHZ overclock on a Raspberry Pi 4 Active Cooling is highly recommended and installing the latest rpi firmware is required.  
You need to do the following to update the firmware
```
sudo apt update && sudo apt upgrade -y && sudo apt dist-upgrade -y && sudo rpi-update -y
```

I can recommend the following overclocks

```
#Overclock Options
arm_freq=1900
over_voltage=6
force_turbo=0
```

```
#Overclock
force_turbo=0
over_voltage=6
arm_freq=2000
gpu_freq=600
v3d_freq=650
```

I have two overclocks listed here because the latest firmware seems to have created an issue with overclocking gpu_freq 
The second overclock was stable previous to the last update of the firmware client and is unstable on the current, and have confirmed with other pi 4 users that gpu_freq on that firmware cannot be changed without causing a failure to boot.  

Current Raspberry Pi 4 Comparability and Optimum plugin list [here](
https://docs.google.com/spreadsheets/d/1zFPt58OvjztHHfIIIfBeX_QA_hquQgVUM6snHXDpePk/edit#gid=578864431)


Example videos
RPI4 capabilities over the Pi3B+ [here](https://www.youtube.com/watch?v=UVMHdSRsFew&t=635s)
RPI 4 9 games tested [here](https://www.youtube.com/watch?v=_bUWsag1IHM&t=172s)
Rpi4 Texture packs [here](https://youtu.be/WuYailLfUVU)







