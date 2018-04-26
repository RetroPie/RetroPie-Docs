## READ FIRST - Why N64 emulation on the Pi is not so great

N64 emulation on the raspberry pi is difficult due to the pi's under powered GPU (Graphics Processing Unit) and lack of certain GPU features found in more modern devices. For a more detailed explanation please see [this post](https://www.reddit.com/r/RetroPie/comments/6se5nj/why_n64_emulation_on_the_pi_isnt_so_great_from_a/) by a mupen64plus developer. 

If you are looking for a more perfect N64 emulation experience you should seriously consider different hardware first (i.e. a desktop computer, modern mobile phone/tablet etc.). However, listed below are several tweaks that can be made to your raspberry pi that will help maximize N64 performance and make many of the popular N64 titles playable. 

## Hardware and Configuration 

A Raspberry Pi 2 or Raspberry Pi 3 is highly suggested. 

### Overclocking

**Overclocking should only be attempted by advanced users who understand the risks. There is a possibility that your warranty will be voided. An unstable overclock will lead to freezing, crashing and SD card corruption. Proceed at your own risk!**

Overclocking is setting a hardware component to run faster than originally intended by the manufacturer. It can add instability if not done properly. It will also make your pi run hotter. There is are no standard settings for overclocking and not all pis will handle the same amount of overclocking. Therefore before you begin overclocking please review [this article](https://github.com/retropie/retropie-setup/wiki/Overclocking) first for proper overclocking methods and stability testing to prevent SD card corruption and potential loss of your data.

For boosting N64 performance, ```gpu_freq``` and ```core_freq``` are the two settings that will give the most benefit to N64 performance. Most pis seem to be stable at ```gpu_freq=500``` and ```core_freq=550``` with some amount of ```over_voltage``` applied. Again it is important to remember that not all pis are equal, some will only overclock a little or not at all. If your pi freezes or crashes then your overclock is unstable. 

```arm_freq```(CPU) and ```sdram_freq```overclocking are of little to no help for boosting N64 performance on the pi. Though they may help increase performance for other high demand emulators such as PSX or MAME.

```v3d_freq``` is set by the ```gpu_freq``` setting so it does not need to be set separately. 


### CPU-Governor

The CPU governor controls when your overclock is applied. With the cpu-governor set to performance mode your pi will run at full speed while running ROMs but will down-clock when sitting idle in Emulation Station. The CPU governor can be set to max performance mode in one of two ways.
```
echo "performance" |sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
Or you can enable it from Runcommand  Go to Retropie-Setup - Setup and Configuration to be used post install - Configure the runcommand launch script - cpu configuration force performance
then cancel, exit and reboot.

## Selecting the Correct Emulator and Graphics Plugin

Just as important as overclocking, selecting the right emulator/graphics plugin from the [runcommand](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand) menu on a per game basis will also increase performance. Selecting the right plugin can make all the difference in making a game playable. 

To learn the community tested optimal settings please view either of the two rom compatibility lists located [here](https://docs.google.com/spreadsheets/d/1Sn3Ks3Xv8cIx3-LGCozVFF7wGLagpVG0csWybnwFHXk/edit) or [here](
https://docs.google.com/spreadsheets/d/1Wjzbu90l6eCEW1w6ar9NtfyDBQrSPILQL5MbRSpYSzw/edit?usp=sharing). (rom compatibility lists are a mess and all are in need of retesting). Do not accept these lists as 100% accurate as they are community maintained and with updates may change over time. There may be some inaccuracies so it is best just to use the lists as a general starting point. Some games listed as playable have with recent updates become playable and vice versa. The current default emulator is mupen64plus-auto which will attempt to select the correct graphics plugin for you, however for best results it is best to test each plugin for yourself on a per game basis. It is recommended that you confirm a game runs well with the standard low-res plugin before attempting to use the hi-res option. 

Each plugin should be set to the lowest resolution (CEA-1) through the runcommand menu. This will slightly increase performance. This can be scaled up for some games that perform really well like Mario kart and Super Mario 64 at your own discretion. 



## Notes on Audio
The SDL audio plugin produces less audio drop out during lag and makes for an improved experience over the the OMX audio plugin. Previously, the SDL audio produced an audio crackling that was undesirable. With recent updates the audio crackle has been fixed so it is now fine to use SDL audio. To switch to the SDL audio plugin you should first update your mupen64plus emulator to the latest binary version. Then navigate to: ```/opt/retropie/configs/all/autoconf.cfg``` and make sure that ```mupen64plus_audio = "0"```

As a side benefit from using SDL audio, save/load states will now function properly with mupen64plus.

## High Resolution Texture Packs

From Current version forward Hi Resolution Texture options are automatically configured to True in the configuration files.  You should not need to modify them as you did with previous versions.  

If it is critical to check that everything is enabled simply run this command in one line


``cat /opt/retropie/configs/n64/mupen64plus.cfg | grep Textures && cat /opt/retropie/configs/n64/mupen64plus.cfg | grep txHiresEnable``

and you should get a result looking like

``LoadHiResTextures = True
DumpTexturesToFiles = False
txHiresEnable = True
txHiresEnable = True``

Which will confirm that Hi Rez is turned on for both Glide and Rice Plugins

Make sure you have launched a rom with both Rice and Glide before checking the file or the variables will not be there to confirm. 

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
update the mupen64plus package  (I suggest installing from source)

Go to launch one of the N64 games you have uploaded a high resolution texture pack for. 
Launch that game
Press x or any key when it launches 
change the video mode to one of the following options
mupen64plus-gles2rice-highres
or
mupen64plus-GLideN64-highres

Then hit launch 

Please also feel free to reference the Rice 64 github page for the source documentation 
https://github.com/mupen64plus/mupen64plus-video-rice




