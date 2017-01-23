> :exclamation: If you want to know how to get USB Audio set up [click here](https://github.com/RetroPie/RetroPie-Setup/wiki/Sound-Issues#usb-audio).

Sound still is a problem child with the Raspberry Pi. Currently, there does not seem to be a best solution for all the sound issues. General information about sound issues can be found at http://elinux.org/R-Pi_Troubleshooting#Sound.

First and foremost try forcing hdmi by adding the following to `/boot/config.txt` then restarting the Raspberry Pi:
```
hdmi_drive=2
```

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

[A post on the Raspberry Pi forums with a list basic troubleshooting options for getting the Pi to play a test sound file.](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=234358#p234358)

[Another potentially helpful post about configuring ALSA.](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=245126#p245126)

***

DGEN sound configuration (according to [this post](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=207923#p207923)):

> if anyone has sound issues with DGen - try changing the int_soundrate to 44100

> worked for me.

***
Emulation is faster when disabling rewind in retroarch.cfg

***
I use a TV Monitor with HDMI input for video and audio. I went to the Raspberry Pi configuration menu and chose “force audio out of HDMI”. Also did the same thing through the “Configure Audio Settings” option on the Retropie main menu in Emulation Station and it did not work.

I had to go into the `/boot/config.txt` Raspberry PI config file and add in the following lines…

      # forces HDMI mode
      hdmi_drive=2   			

      # Pretends all audio formats are supported by display, allowing passthrough of DTS/AC even when not reported as supported.
      hdmi_force_edid_audio=1		

I didn't change any other sound parameters in the config files. 

***
### White Noise Fix

To remove hiss or static or white noise when using the 3.5mm headphone jack:

1. Run at the command line: `sudo nano /boot/config.txt` and insert at the bottom of the file: `disable_audio_dither=1`
1. turn up Retropie volume to 100% in the settings menu in the program.
1. get an inline volume control: http://www.amazon.com/Koss-155954-VC20-Volume-Control/dp/B00001P4XH/ref=pd_bxgy_23_img_y
1. Another option is to set audio_pwm_mode=2 in the same config - this is a new audio driver that should significantly improve the sound quality - see https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=136445

## USB Audio

There's a lot of **old** documentation on how to set this up.  To fix this, especially if you are using a **USB Audio** dongle in leu of the Raspberry Pi's scratchy 3.5 mm audio jack. (Blame the manufacturer of that part. Hopefully the foundation will fix it when the next Pi comes out.)

So instead of using one of those large shield with the RCA jacks on it, a small [USB Audio Dongle](http://www.amazon.com/gp/product/B003UBKR4U) and a few commands.

1.    At startup, press <kbd>F4</kbd> to exit EmulationStation and go to the console.
2.    Assuiming the USB Audio dongle is plugged in, type `lsusb`, and look for some device with "C-Media Electronics, Inc. Audio Adapter" in it.
3.   Not a necessary step but one that you should note. Type, `amixer`.  You'll see the default bcm2835 set up. Our device is not set up yet. Knowing about this command is still helpful.
4.    Find our card number.  More than likely, the "C-Media USB Headphone Set" will be set to `Card 1`.  You will need to remember this number for the next step.
5.    Use `nano` to create `/etc/asound.conf` with this content.  Press <kbd>Ctrl</kbd>+<kbd>X</kbd> followed by <kbd>Y</kbd> when finished.  Replace the card number in the code below with the correct card number if it is other than `1`.

     ```
    pcm.!default {
     type hw card 1
    }
    ctl.!default {
     type hw card 1
    }
    ```

6.    `sudo reboot`.  When EmulationStation or a video game is played, you will start to notice sound.

7.    If you want to test stereo, <kbd>F4</kbd> again to do a speaker test using `speaker-test -c2 hw:Set,0` where `-c2` indicates the number of channels. If you have just one speaker, use `-c1` instead.  You should hear a hiss in each speaker separately.  This test will go on continuously until you press <kbd>Ctrl</kbd>+<kbd>C</kbd>.

> :warning: **Note:** There is a pitfall with these instructions, and that is I (@jrcharney) don't know what will happen if you plug this into HDMI later.  If anybody knows, append that information to this section.