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

Overclocking ```sdram_freq``` will give a very small boost to performance. Going from 450mhz to 550mhz yielded at best about a 1FPS increase. Sdram has its own over voltage value ```over_voltage_sdram```.  You may also need to add ```sdram_schmoo=0x02000020```to your config.txt. This is a set of timings that can help add stability if your sdram is overclocked.

```v3d_freq```can also be overclocked. This helped improve performance for a couple games I tested. Most of the raspberry pis I tested were stable to at least ```v3d_freq=500``` but not much past this.

```arm_freq```(CPU) overclocking is of little to no help for boosting N64 performance on the pi. There was no discernible FPS increase overclocking the Pi 3's CPU from the standard 1200mhz to 1350mhz. Though it may help increase performance for other high demand emulators such as PSX or MAME. Overclocking ```arm_freq``` may benefit earlier pi models though additional testing is needed to confirm. 

### CPU-Governor

The CPU governor controls when your overclock is applied. With the cpu-governor set to performance mode your pi will run at full speed while running ROMs but will down-clock when sitting idle in Emulation Station. The CPU governor can be set to max performance mode in one of two ways.
```
echo "performance" |sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
Or you can enable it from the retropie setup menu. In Emulation Station go to Retropie-Setup - Setup and Configuration to be used post install - Configure the runcommand launch script - cpu configuration - force performance
then cancel, exit and reboot.

## Selecting the Correct Emulator and Graphics Plugin

Just as important as overclocking, selecting the right emulator/graphics plugin from the [runcommand](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand) menu on a per game basis will also increase performance. Selecting the right plugin can make all the difference in making a game playable. 

To learn the community tested optimal settings please view either of the two rom compatibility lists located [here](https://docs.google.com/spreadsheets/d/1Sn3Ks3Xv8cIx3-LGCozVFF7wGLagpVG0csWybnwFHXk/edit) or [here](
https://docs.google.com/spreadsheets/d/1Wjzbu90l6eCEW1w6ar9NtfyDBQrSPILQL5MbRSpYSzw/edit?usp=sharing). (rom compatibility lists are a mess and all are in need of retesting). Do not accept these lists as 100% accurate as they are community maintained and with updates may change over time. There may be some inaccuracies so it is best just to use the lists as a general starting point. Some games listed as unplayable have with recent updates become playable and vice versa. The current default emulator is mupen64plus-auto which will attempt to select the correct graphics plugin for you, however for best results it is best to test each plugin for yourself on a per game basis. It is recommended that you confirm a game runs well with the standard low-res plugin before attempting to use the hi-res option. 

Each N64 emulator/video plugin should be set to the lowest resolution (CEA-1 for most displays) through the runcommand menu. This will slightly increase performance by limiting the up-scaling the pi has to perform. This is not necessary for the gles2n64 video plugin.

**NOTE** The gliden64 video plugin currently has issues with frame buffer emulation on the pi that causes visual glitches which lead to a crash after about 10-20 mins of playtime. A recent update has taken care of this issue so it is highly recommended that you update mupen64plus from SOURCE.


## Notes on Audio
The SDL audio plugin produces less audio drop out and makes for an improved experience over the OMX audio plugin. Previously, the SDL audio plugin produced an audio crackling that was undesirable. With recent updates the audio crackle has been fixed so it is now fine to use SDL audio. To switch to the SDL audio plugin you should first update your mupen64plus emulator to the latest binary version. Then navigate to: ```/opt/retropie/configs/all/autoconf.cfg``` and make sure that ```mupen64plus_audio = "0"```

As a side benefit from using the SDL audio plugin, save/load states will now function properly with mupen64plus.

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




