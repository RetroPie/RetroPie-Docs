Sound still is a problem child with the Raspberry Pi. Currently, there does not seem to be a best solution for all the sound issues. General information about sound issues can be found at http://elinux.org/R-Pi_Troubleshooting#Sound.

This place re-cites some posts (or parts of them) from different forum threads that might increase the sound quality:

* Update the retroarch.cfg file with audio_out_rate = 44100
Using that config the ALSA sound coming from the headphone jack is a lot clearer and has a lot less static.

## Users Configurations

You can post your configuration here to give other people an idea about what kind of audio they can expect with certain settings. Interesting parameters might be 
* HDMI/analog
* ARM frequency
* emulator core
* eventually parameters set in /etc/retroarch.cfg
* perceived audio quality, problems

***

From [puncrathod](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=159708#p159708):
> I managed to get perfect sound with retroarch+pocketsnes core by defining sdl as the audio backend with 44100 samplerate. However I never managed to get the thing run faster than 70% speed during actual gameplay.
I tested it with lostvikings and when you pause the game the game runs fullspeed and the sound is perfect. But while playing the speed goes below 80% and the sound and music gets this echoing sound. I'll see if I can make it run at full speed by a little overclock and some addinational video settings.

* The only /boot/config.txt setting I had was sdtv_mode=2 "I have a pal tv that I use for the pi"
I did try increasing the cpu_freq to 900 and core_freq to 450 and that helped a little but still were not getting full speed.
* The only settings i changed in the /etc/retroarch.cfg was  

        audio_out_rate=44100
        audio_driver=sdl
* (alsa works perfect too if the game is running at full speed but even with 1% drop in speed and starts making a static noise)
* I'm running a fresh rasbian installed from http://archive.raspbian.org/installer/rpi_installer_08-19-12.zip with nothing more extra installed than retroarch+pocketsnes+sdl and the libraries needed to run them. I don't have DE installed and run everything from the console
* I realize that the sdl audio is a bit slower than alsa and makes the snes run even slower but atleast it doesn't turn the audio into a garbled mess when the emulator doesn't run at full speed.

***