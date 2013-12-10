*IN PROCESS*

You did the steps in [First Installation](First-Installation), basically everything works, but some things could just run better. This tutorial is intended to describe the next steps after a successful installation, to give RetroPie the necessary finishing touches.

### VGA mode and overscan
First things first. If you have an HDTV and the Raspberry Pi is connected via HDMI to it, I highly recommend you switch to VGA Mode. This is for a better performance (1080p/720p vs. 480p) in _emulationstation_ and the emulators run anyway in 480p. HDMI Group 1 stands for CEA and Mode 1 is VGA. More Infos [here](http://elinux.org/RPiconfig#Video_mode_options). You should also set the overscan scale to one. Otherwise emulationstation doesn't start or the scaling is incorrect. 

**/boot/config.txt**
```
hdmi_group=1
hdmi_mode=1
overscan_scale=1
```
***
### Sound issues and overclocking
Some games have a crackling sound? The only way to get rid of this, is overclocking. For overclocking there aren't "THE BEST SETTINGS". You have to test your overclocking settings, how far you can go. To push the Raspberry Pi to the limits, I recommend you buy a heat sink. The crackling sound disappared, after I set _armfreq_ to _950_, _corefreq_ to _450_, _sdramfreq_ to _450_ and _gpumem_ to _384_. My settings with additional heat sinks:

**/boot/config.txt**
```
arm_freq=1050
gpu_mem_512=384
core_freq=550
h264_freq=0
isp_freq=0
avoid_pwm_pll=1
sdram_freq=600
over_voltage=6
avoid_safe_mode=1
force_turbo=0
```
If your Rapberry Pi crashes (freezes etc.), please use lower settings. Sometimes it seems to run stable, but crashes in emulationstation or running a game. To test the stability and a possible SD Card corruption, I recommend to you use a stresstest Skript. e.g. from [elinux.org](http://elinux.org/RPi_config.txt#Overclock_stability_test):

**/home/pi/stresstest.sh**
`sudo chmod +x /home/pi/stresstest.sh`
content (I've changed the iterations):
```
stresstest.sh
#!/bin/bash
#Simple stress test for system. If it survives this, it's probably stable.
#Free software, GPL2+

echo "Testing overclock stability..."

#Max out the CPU in the background (one core). Heats it up, loads the power-supply. 
nice yes >/dev/null &

#Read the entire SD card 10x. Tests RAM and I/O
for i in {1..2}; do echo reading: $i; sudo dd if=/dev/mmcblk0 of=/dev/null bs=4M; done

#Writes 512 MB test file,  10x.
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

***


-- MasteRehm (initial 10/12/13)