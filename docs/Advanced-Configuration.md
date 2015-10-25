You did the steps in [First Installation](First-Installation), basically everything works, but some things could run better. This tutorial is intended to describe the next steps after a successful installation, to give RetroPie some finishing touches.  

## Sound issues

There are a few things that can cause sound issues- one is the hardware (typically audio through the 3.5 mm jack causes a buzzing noise.) Other issues can be incorrect settings or a lack of processing power which can be mitigated somewhat potentially by overclocking which is discussed in the next section. See [This Page](https://github.com/RetroPie/RetroPie-Setup/wiki/Sound-Issues) for more details on resolving sound issues. Sound settings can also be changed from the retropie menu in emulationstation.

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

### CPU/GPU Split

Since the raspberry pi is a SoC the cpu and gpu share the same amount of RAM. The following option allows you to choose how much RAM you allocate to the GPU compared to the CPU. This will typically resolve emulationstation being laggy/ freezing with too many systems as well as kodi freezing, among other things.

![advanced](https://cloud.githubusercontent.com/assets/10035308/10713851/061f690e-7a93-11e5-9ed1-86981e7c9325.png)

![advanced2](https://cloud.githubusercontent.com/assets/10035308/10713853/290b82cc-7a93-11e5-92ec-0b94aaa60185.png)

You can choose a split from 16/32/64/128/256 (the settings may be different depending on the version of pi you have)

![gpu](https://cloud.githubusercontent.com/assets/10035308/10713855/53c539b8-7a93-11e5-9016-2117e8a890ad.png)

### BIOS files
The BIOS files are necessary for some emulators in order to get games to work. For more information on which BIOS files are needed see the each emulator page on the wiki or [this page.](https://github.com/RetroPie/RetroPie-Setup/wiki/BIOS-setup-for-RetroPie) 

***

```
### Misc
the following sets the _core provided_ aspect ratio (4:3), the _video scale integer_ and disable the help rgui screen:

**`/home/pi/RetroPie/configs/all/retroarch.cfg`**

`aspect_ratio_index = "6"`  
`video_scale_integer = true`  
`rgui_show_start_screen = false`

some aliases can be set in _.bashrc_  
**`/home/pi/.bashrc`**
bash
alias l='ls -alhF'
alias ..='cd ..'
alias roms='cd /home/pi/RetroPie/roms/'
alias es='/usr/bin/emulationstation'
alias rpies='sudo /home/pi/RetroPie-Setup/retropie_setup.sh'
alias scraper='python /home/pi/RetroPie/supplementary/ES-scraper/scraper.py -w 280 -m -p'
alias temp='vcgencmd measure_temp'

***

-- MasteRehm (initial 10/12/13)
```