*IN PROCESS*

You did the steps in [First Installation](First-Installation), basically everything works, but some things could just run better. This tutorial is intended to describe the next steps after a successful installation, to give RetroPie the necessary finishing touches.

First things first. If you have an HDTV and the Raspberry Pi is connected via HDMI to it, I highly recommend you switch to VGA Mode. This is for a better performance (1080p/720p vs. 480p) in _emulationstation_ and the emulators run anyway in 480p. HDMI Group 1 stands for CEA and Mode 1 is VGA. More Infos [here](http://elinux.org/RPiconfig#Video_mode_options). You should also set the overscan scale to one. Otherwise emulationstation doesn't start or the scaling is incorrect. 

**/boot/config.txt**
```
hdmi_group=1
hdmi_mode=1
overscan_scale=1
```
---
Some games have a crackling sound? The only way to get rid of this, is overclocking. For overclocking there aren't "THE BEST SETTINGS". You have to test your overclocking settings, how far you can go. To push the Raspberry Pi to the limits, I recommend you buy a heat sink. The crackling sound disappared, after I set _arm_freq_ to _950_, _core_freq_ to _450_, _sdram_freq_ to _450_ and _gpu_mem_ to _384_.

-- MasteRehm (initial 10/12/13)