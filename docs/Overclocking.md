## Overclocking

For overclocking there aren't "the best settings" per se. You have to test your overclocking settings to see how far you can go To push the Raspberry Pi to the limits, a heat sink is recommended. (there will be varying overclock settings for each version of raspberry pi). You may also want to make sure your power supply is sufficient (5V 2A) with a decent cable.

You can change the overclock from the raspi-config menu that can be accessed from the retropie menu in emulationstation or by typing `sudo raspi-config` in the terminal

![overclock](https://cloud.githubusercontent.com/assets/10035308/10713805/9e6c826c-7a90-11e5-92c9-e613e8154366.png)

You'll see this warning (overclocking may shorten the lifespan of your pi)

![warning](https://cloud.githubusercontent.com/assets/10035308/10713808/d45abaec-7a90-11e5-8677-341d82ce217b.png)

Then select your preferred overclock setting (this menu may vary depending on your version of raspberry pi)

![presets](https://cloud.githubusercontent.com/assets/10035308/10713816/290103ee-7a91-11e5-8c65-9a69fa48e0ff.png)

The following are settings for a raspberry pi 2 with heat sinks but you should test a few different settings just to make sure everything works. (these can be set manually in the following file if you don't want to set them from raspi-config):

**`/boot/config.txt`**
```bash
arm_freq=1050
gpu_mem_512=384
core_freq=500
h264_freq=0
isp_freq=0
avoid_pwm_pll=1
sdram_freq=550
over_voltage=6
avoid_safe_mode=1
force_turbo=0
```
If your Rapberry Pi crashes (freezes etc.), use lower settings. If it freezes before you can change anything you can boot while holding shift and that should disable the overclock so that you can change it to something lower. Sometimes it seems to run stable, but crashes in emulationstation or running a game. To test the stability and a possible SD Card corruption, You can use a stresstest script. e.g. from [elinux.org](http://elinux.org/RPi_config.txt#Overclock_stability_test):

**`/home/pi/stresstest.sh`**

`sudo chmod +x /home/pi/stresstest.sh`  
(I've changed the iterations):  
```bash
stresstest.sh
#!/bin/bash
#Simple stress test for system. If it survives this, it's probably stable.
#Free software, GPL2+

echo "Testing overclock stability..."

#Max out the CPU in the background (one core). Heats it up, loads the power-supply. 
nice yes >/dev/null &

#Read the entire SD card, 2x. Tests RAM and I/O
for i in {1..2}; do echo reading: $i; sudo dd if=/dev/mmcblk0 of=/dev/null bs=4M; done

#Writes 512 MB test file,  5x.
for i in {1..5}; do echo writing: $i; dd if=/dev/zero of=deleteme.dat bs=1M count=512; sync; done

#Clean up
killall yes
rm deleteme.dat

#Print summary. Anything nasty will appear in dmesg.
echo -n "CPU freq: " ; cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
echo -n "CPU temp: " ; cat /sys/class/thermal/thermal_zone0/temp
dmesg | tail 

echo "Not crashed yet, probably stable."
```
To get the current temperature in an human readable output try `vcgencmd measure_temp`. its possible th pi can freeze if the temperature goes over 65 degrees celsius.

see also: http://linuxonflash.blogspot.com/2015/02/a-look-at-raspberry-pi-2-performance.html


## Raspberry Pi 3 Overclocking

The Raspberry Pi 3 has a noticeable performance boost from the Raspberry Pi 2. 

There are a few things that need to be taken into consideration when using a Raspberry Pi 3.

- Proper Power Supply
- Proper Cooling
- Overclock Settings

#### Proper Power Supply

Do not just use any old cell phone power adapter you have around, she is a power hungry beast and if your going to overclock and use all 4 ports you need to give her enough power, 
Grab you a 5v 2500 mA adapter [This](http://www.amazon.com/gp/product/B011BE929S) is the adapter I used.

#### Proper Cooling

Heat will probably be an issue with 3's luckily it is easy to overcome. Pick you up a set of [heatsinks](http://www.amazon.com/gp/product/B00HPQGTI4),  keep in mind that there are 3 core areas on the pi biggest chip on the top is SOC (CPU+GPU) the smaller one is the ethernet/usb controller and on the bottom is the 1GB LPDDR2 memory module. 

The stock heatsinks you order have some adhesive on them it is not thermal paste. I would definitely recommend purchasing some thermal adhesive to create the best bond between your heatsink and cores. 
[This](http://www.amazon.com/gp/product/B0087X725S) is what I picked up then i used alcohol to completely clean the heatsinks before applying the thermal expoxy.

Finally for a little extra cooling grab a well ventilated case with an active fan on it, this is especially important because the wifi / bluetooth chip has a thin type of pad on the bottom and it is extremely sensitive so its critical to get it in a case asap or risk damaging your wifi/bluetooth

For the extremly experimental look up users who have submersed their pi's in mineral oil for what is called immersion cooling. 

#### Pi 3 Overclock Settings

Under the impression that the default clock with the Raspberry Pi 3 will be 1.2 GHZ 

I went ahead and SSH'd into my box and modified the following values into my `/boot/config.txt` file

```
#Overclock Settings
arm_freq=1400 (Try 1350 if 1400 does not work)
over_voltage=6
temp_limit=80
core_freq=500

#GPU Based
h264_freq=333
avoid_pwm_pll=1
gpu_mem=450
v3d_freq=500
#Ram Overclock
sdram_freq=588
sdram_schmoo=0x02000020
over_voltage_sdram_p=6
over_voltage_sdram_i=4
over_voltage_sdram_c=4
#Sound Fix
hdmi_drive=2



```

Mind you these are just stable settings I have found and I am far from done tuning.  
Under load my cpu is running cool and i have not seen it spike over 51c 
I have had no shutdowns or freezes related to heat.
I will continue messing with moving the gpumem variable around and I do want to try going up to 1550 on the clock but not until i get an immersion cooling setup. 

If your pi wont boot after applying a setup just take out the sdcard put it in a card reader on your pc and downclock 

I have been experimenting and you can see some of the results I have gotten in [this video](https://www.youtube.com/watch?v=dsrxdCtNzLg&feature=youtu.be), 

Tons of speed improvements on default settings there.  Many games that were unplayable or not booting now work. For example Moonwalker and Wild West Cowboys of Moo Mesa in mame alone. 

With N64 I do have to cycle between emulators and turn down video resolutions but I am getting highly playable results. 
With your keyboard hit X when the game is booting up 
Try the different emulators.  For example Goldeneye and Killer Instinct gold I change from my default Rice to Glide. 
Try downscaling your resolution for games that are still lagggy.  640 X 480 16:9  is what I pushy both KI and Goldeneye to but get highly playable and good looking results. 


Other tuning footnotes.
Helpful Tricks to improve performance.

#Improving Input lag and delay
Modify the following in your /opt/retropie/configs/all/retroarch.cfg   
```
video_hard_sync = true
video_hard_sync_frames = 3
video_frame_delay = 5
```


#Displaying Framerate in your libretro emulators
Modify the following in your /opt/retropie/configs/all/retroarch.cfg   
```
fps_show = "true"
```


#Install application to test memory usage
```
sudo apt-get install htop
```

While playing games from a pc or laptop ssh to your machine
run the command htop
You can then monitor CPU usage as well as memory usage you can use this to tune how much gpu_mem you can allocate.  I am currently allocating 600 on my pi3 with great results. 


#Check GPU_MEM utilization on your retropie
```
 sudo vcdbg reloc
```

#Storage
Storage is an often overlooked component of emlator performance, while it may not effect lower end emulators like nes and snes  good performing storage is critical to performance of emulators like N64 , Dreamcast, and PSP
Make sure you have a class 10 sd-card with a min of 48mb/s that is a name brand not some generic clone.  Faster the better. 
Intresting stuff going on over here.  
http://www.jeffgeerling.com/blog/2016/how-overclock-microsd-card-reader-on-raspberry-pi-3
SDCard Benchmarks, performance tests and a method to overclock your SD card reader slot from 50Hz to 100Hz 





