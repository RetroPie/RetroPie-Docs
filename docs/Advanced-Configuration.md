You did the steps in [First Installation](First-Installation), basically everything works, but some things could just run better. This tutorial is intended to describe the next steps after a successful installation, to give RetroPie the necessary finishing touches. It's a personal view and not all points will fit to your configuration. The core components:
* HDTV and VGA mode
* Xbox 360 Controller
* Overclocking
* Emulationstation and emulators adjustments
* Bios files

### VGA mode and overscan
First things first. If you have an HDTV and the Raspberry Pi is connected via HDMI to it, I highly recommend you switch to VGA Mode. This is for a better performance (1080p/720p vs. 480p) in _emulationstation_ and the emulators run anyway in 480p. HDMI Group 1 stands for CEA and Mode 1 is VGA. More Infos [here](http://elinux.org/RPiconfig#Video_mode_options). You should also set the overscan scale to one. Otherwise emulationstation doesn't start or the scaling is incorrect. 

**`/boot/config.txt`**
```
hdmi_group=1
hdmi_mode=1
overscan_scale=1
```
***
### Sound issues and overclocking
Some games have a crackling sound? The only way to get rid of this, is overclocking. For overclocking there aren't "THE BEST SETTINGS". You have to test your overclocking settings, how far you can go. To push the Raspberry Pi to the limits, I recommend you buy a heat sink. The crackling sound disappared, after I set _armfreq_ to _950_, _corefreq_ to _450_, _sdramfreq_ to _450_ and _gpumem_ to _384_. My settings with additional heat sinks:

**`/boot/config.txt`**
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
If your Rapberry Pi crashes (freezes etc.), please use lower settings. Sometimes it seems to run stable, but crashes in emulationstation or running a game. To test the stability and a possible SD Card corruption, I recommend to use a stresstest script. e.g. from [elinux.org](http://elinux.org/RPi_config.txt#Overclock_stability_test):

**`/home/pi/stresstest.sh`**

`sudo chmod +x /home/pi/stresstest.sh`  
(I've changed the iterations):  
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
To get the current temperature in an human readable output try `vcgencmd measure_temp`. I don't know exactly, but on my experiences the Raspberry Pi freezes, if the temperature goes over 65 degrees celsius.

There are a lot of forum posts and configuration hints about several sound issues, which recommends to set _audio out rate_ to _44100_ and the _audio driver_ to _sdl_ in retroarch.cfg. To be honest, I can't see a difference to the default values. As I mentioned before, only the overclocking fixed the sound issues. For the sake of completeness, my retroarch.cfg audio lines:  
**`/home/pi/RetroPie/configs/all/retroarch.cfg`**
```
audio_out_rate = 44100
#audio_enable = true
#audio_driver = sdl
#audio_sync = true
```
As you can see, I've changed only the _audio out rate_. The default driver _alsathread_ works for me like a charm.
***
### Xbox 360 Controller
Setup and configuration see this [Wiki Page](Setting-up-the-XBox360-controller). The "third possibility" is from me. I wrote an _init.d_ script and I recommend to use xboxdrv with the daemon option, because of less use of CPU and RAM. Furthermore I had to set _dwc otg.speed_.
***
### Emulationstation adjustments
There are a few adjustments for emulationstation. In my case the input for my Xbox 360 Controller and some entries for the systems, aka emulators.  
**`/home/pi/.emulationstation/es_input.cfg`**
```
<?xml version="1.0"?>
<inputList>
    <inputConfig type="keyboard" />
    <inputConfig type="joystick" deviceName="Xbox Gamepad (userspace driver)">
        <input name="a" type="button" id="4" value="1" />
        <input name="b" type="button" id="5" value="1" />
        <input name="down" type="button" id="1" value="1" />
        <input name="left" type="button" id="2" value="1" />
        <input name="menu" type="button" id="13" value="1" />
        <input name="pagedown" type="button" id="11" value="1" />
        <input name="pageup" type="button" id="10" value="1" />
        <input name="right" type="button" id="3" value="1" />
        <input name="select" type="button" id="8" value="1" />
        <input name="up" type="button" id="0" value="1" />
    </inputConfig>
    <inputConfig type="keyboard">
        <input name="a" type="key" id="13" value="1" />
        <input name="b" type="key" id="8" value="1" />
        <input name="down" type="key" id="274" value="1" />
        <input name="left" type="key" id="276" value="1" />
        <input name="menu" type="key" id="109" value="1" />
        <input name="pagedown" type="key" id="281" value="1" />
        <input name="pageup" type="key" id="280" value="1" />
        <input name="right" type="key" id="275" value="1" />
        <input name="select" type="key" id="108" value="1" />
        <input name="up" type="key" id="273" value="1" />
    </inputConfig>
</inputList>
```

Button  | Configname
--------|-----------
A       | a
B       | b
DPdown  | down
DPup    | up
DPleft  | left
DPright | right
Start   | menu
LB      | select
LT      | pageup
RT      | pagedown

_DP = DigiPad_

**`/home/pi/.emulationstation/es_systems.cfg`**  
Hint: The order of the emulators in this file, are exactly the order in emulationstation.  
_Sega Master System_  
For the _Sega Master System II_ entry, I changed the command line and therefore the emulator to _retroarch_. Osmose seems to me the better one, but it lacks in this version of a controller button configuration for exiting the emulator (e.g. only the options -joy -joy1 4 -joy2 6-joystart 13 are possible). 
```
...
COMMAND=/home/pi/RetroPie/supplementary/runcommand/runcommand.sh 1 "/home/pi/RetroPie/emulators/RetroArch/installdir/bin/retroarch -L /home/pi/RetroPie/emulatorcores/picodrive/picodrive_libretro.so --config /home/pi/RetroPie/configs/all/retroarch.cfg --appendconfig /home/pi/RetroPie/configs/mastersystem/retroarch.cfg  %ROM%"
...
```
_Sega Mega Drive_  
If you want to play MegaCD games, you have to add the _bin_ prefix:
```
...
EXTENSION=.smd .SMD .bin .BIN .gen .GEN
...
```
_Neo Geo_  
I didn't get the Neo Geo running with _gngeo_. So, I use _pifba_:
```
...
COMMAND=/home/pi/RetroPie/supplementary/runcommand/runcommand.sh 1 "/home/pi/RetroPie/emulators/pifba/fba2x %ROM%"
...
```
***
### Xbox 360 Controller button configuration for retroarch and final burn alpha
**`/home/pi/RetroPie/configs/all/retroarch.cfg`**
```
#Player 1
input_player1_joypad_index = 0
input_player1_b_btn = 6
input_player1_a_btn = 4
input_player1_y_btn = 7
input_player1_x_btn = 5
input_player1_l_btn = 10
input_player1_r_btn = 11
input_player1_start_btn = 13
input_player1_select_btn = 12
input_player1_up_btn = 0
input_player1_down_btn = 1
input_player1_left_btn = 2
input_player1_right_btn = 3
input_exit_emulator_btn = 15
input_menu_toggle_btn = 16

#Player 2
input_player2_joypad_index = 1
input_player2_b_btn = 6
input_player2_a_btn = 4
input_player2_y_btn = 7
input_player2_x_btn = 5
input_player2_l_btn = 10
input_player2_r_btn = 11
input_player2_start_btn = 13
input_player2_select_btn = 12
input_player2_up_btn = 0
input_player2_down_btn = 1
input_player2_left_btn = 2
input_player2_right_btn = 3
```
_input exit emulator_ to exit the emulator and return to emulationstation._input menu toggle_ to show the retroarch menu (e.g. to set the aspect ratio, save/load the game, etc.)

**`/home/pi/RetroPie/emulators/pifba/fba2x.cfg`**
```
[Joystick]
A_1=4
B_1=5
X_1=6
Y_1=7
L_1=10
R_1=11
START_1=13
SELECT_1=12
#Joystick axis
JA_LR=0
JA_UD=1

#player 2 button configuration
A_2=4
B_2=5
X_2=6
Y_2=7
L_2=10
R_2=11
START_2=13
SELECT_2=12
#Joystick axis
JA_LR_2=0
JA_UD_2=1
```
Up to now, I didn't figure out, how to change the configuration from the analog sticks to the digipad. To exit the emulator, press START and SELECT together.
***
### Bios files
Neo Geo, Mega CD, PC Engine CD and Playstation need their BIOS. There are many suggestions out there and only a few will work. It's neccassary to put the bios files in the right directory and the file must have the correct name. There are some "bios options", which you can set on most emulators, but they didn't work for me.  
Create a directory called "bios" under /home/pi/RetroPie:  
`mkdir /home/pi/RetroPie/bios`  
Add the following line to retroarch.cfg  
**`/home/pi/RetroPie/configs/all/retroarch.cfg`**

`system_directory = /home/pi/RetroPie/bios`  

system | filename  | directory
-------|-----------|----------
Neo Geo | neogeo.zip | /home/pi/RetroPie/roms/neogeo
PC Engine | syscard3.pce | /home/pi/RetroPie/bios
Playstation | scph7502.bin | /home/pi/RetroPie/bios
Mega CD (EU) | eu_mcd1_9210.bin | /home/pi/RetroPie/bios
Mega CD (JP) | jp_mcd1_9112.bin | /home/pi/RetroPie/bios
Mega CD (USA) | us_scd1_9210.bin | /home/pi/RetroPie/bios

***
### Misc
For retroarch I set the _core provided_ aspect ratio (4:3):  
**`/home/pi/RetroPie/configs/all/retroarch.cfg`**
aspect_ratio_index = "6"

I set some aliases in _.bashrc_
**`/home/pi/.bashrc`**
```
alias l='ls -alhF'
alias ..='cd ..'
alias roms='cd /home/pi/RetroPie/roms/'
alias es='/usr/bin/emulationstation'
alias rpies='sudo RetroPie-Setup/retropie_setup.sh'
alias scraper='python /home/pi/RetroPie/supplementary/ES-scraper/scraper.py -w 280 -m -p'
alias temp='vcgencmd measure_temp'
```
***

-- MasteRehm (initial 10/12/13)