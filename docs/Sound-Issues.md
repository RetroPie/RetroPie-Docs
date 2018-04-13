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
> I managed to get perfect sound with retroarch+ lr-snes9x2002 core by defining sdl as the audio backend with 44100 samplerate. However I never managed to get the thing run faster than 70% speed during actual gameplay.
I tested it with lostvikings and when you pause the game the game runs fullspeed and the sound is perfect. But while playing the speed goes below 80% and the sound and music gets this echoing sound. I'll see if I can make it run at full speed by a little overclock and some additional video settings.

* The only /boot/config.txt setting I had was sdtv_mode=2 "I have a pal tv that I use for the pi"
I did try increasing the cpu_freq to 900 and core_freq to 450 and that helped a little but still were not getting full speed.
* The only settings i changed in the /etc/retroarch.cfg was  

        audio_out_rate=44100
        audio_driver=sdl
* (alsa works perfect too if the game is running at full speed but even with 1% drop in speed and starts making a static noise)
* I'm running a fresh Raspbian installed from http://archive.raspbian.org/installer/rpi_installer_08-19-12.zip with nothing more extra installed than retroarch+lr-snes9x2002+sdl and the libraries needed to run them. I don't have DE installed and run everything from the console
* I realize that the sdl audio is a bit slower than alsa and makes the snes run even slower but atleast it doesn't turn the audio into a garbled mess when the emulator doesn't run at full speed.

***

[A post on the Raspberry Pi forums with a list basic troubleshooting options for getting the Pi to play a test sound file.](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=234358#p234358)

[Another potentially helpful post about configuring ALSA.](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=245126#p245126)

***
To reset ALSA, run the following from the command line:

    alsactl restore -P

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
1. Turn up Retropie volume to 100% in the settings menu in the program.
1. Get an inline volume control: http://www.amazon.com/Koss-155954-VC20-Volume-Control/dp/B00001P4XH
1. Another option is to set audio_pwm_mode=2 in the same config - this is a new audio driver that should significantly improve the sound quality - see [this topic on Analogue audio testing](https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=136445).

### aplay: audio open error: Device or resource busy

You must do the following from command line:
To extract info on the application hogging the sound device, do:

    lsof | grep snd
This displayed:

    xmms2d  31732  patrick   7u    CHR  116,9  0t0  3885 /dev/snd/controlC0
I could see evidence of the app that was blocking access. I had nothing obvious running, so I killed the process.

    killall xmms2d OR kill -9 31732 (which is the PID)
Then checked again.

    lsof | grep snd
Nothing. Its clear.
Done.

**Original credit to:**
[aplay-device-or-resource-busy](http://stray-notes.blogspot.com/2010/12/aplay-device-or-resource-busy.html)
## USB Audio

There's a lot of **old** documentation on how to set this up.  To fix this, especially if you are using a **USB Audio** dongle in lieu of the Raspberry Pi's scratchy 3.5 mm audio jack. (Blame the manufacturer of that part. Hopefully the foundation will fix it when the next Pi comes out.)

So instead of using one of those large shield with the RCA jacks on it, a small [USB Audio Dongle](http://www.amazon.com/gp/product/B003UBKR4U) and a few commands.

1.    At startup, press <kbd>F4</kbd> to exit EmulationStation and go to the console.
2.    Assuming the USB Audio dongle is plugged in, type `lsusb`, and look for some device with "C-Media Electronics, Inc. Audio Adapter" in it.
3.   Not a necessary step but one that you should note. Type, `amixer`.  You'll see the default bcm2835 set up. Our device is not set up yet. Knowing about this command is still helpful.
4.    Find our card number.  More than likely, the "C-Media USB Headphone Set" will be set to `Card 1`.  You will need to remember this number for the next step.
5.    Use `nano` to create `/etc/asound.conf` with this content.  Press <kbd>Ctrl</kbd>+<kbd>X</kbd> followed by <kbd>Y</kbd> when finished.  Replace the card number in the code below with the correct card number if it is other than `1`.


    pcm.!default {
     type hw card 1
    }
    ctl.!default {
     type hw card 1
    }


6.    `sudo reboot`.  When EmulationStation or a video game is played, you will start to notice sound.

7.    If you want to test stereo, <kbd>F4</kbd> again to do a speaker test using `speaker-test -c2 hw:Set,0` where `-c2` indicates the number of channels. If you have just one speaker, use `-c1` instead.  You should hear a hiss in each speaker separately.  This test will go on continuously until you press <kbd>Ctrl</kbd>+<kbd>C</kbd>.

> :warning: **Note:** There is a pitfall with these instructions, and that is I (@jrcharney) don't know what will happen if you plug this into HDMI later.  If anybody knows, append that information to this section.

## Alternate USB Audio Method
This method was originally documented on the [sudomod forum](http://www.sudomod.com/forum/viewtopic.php?t=144)

1. Attach the USB audio dongle into one of the USB ports connected the RPi. Reboot the system.

2. Once EmulationStation has loaded, exit from it by pressing <kbd>F4</kbd>. This will take you to the terminal.

3. Check if your USB audio has been detected by Raspbian Jessie by typing the command below:

       lsusb

Output should be:

       Bus 001 Device 007: ID 0d8c:0014 C-Media Electronics, Inc.
       Bus 001 Device 004: ID 0424:2517 Standard Microsystems Corp. Hub
       Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. SMSC9512/9514 Fast Ethernet Adapter
       Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp.
       Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The C-Media Electronics, Inc line shows that the USB audio device is detected.

4. Once we're sure the USB audio device is detected, let's check the order of priority of the sound cards being used by the system. Do so by typing this command:

       cat /proc/asound/modules

Output should be:

        0 snd_bcm2835
        1 snd_usb_audio

As you can see from the output above, the snd_bcm2835 is the built-in sound card but we want the system to use snd_usb_audio

5. We can change and force the system to load the sound cards in a different order by creating a sound configuration file. Create the file by using the command below:

       sudo nano /etc/modprobe.d/alsa-base.conf

You will then enter the Nano editor environment and type the following lines:

       options snd_usb_audio index=0
       options snd_bcm2835 index=1
       options snd slots=snd-usb-audio,snd-bcm2835

Afterwards, press Ctrl+X to exit and answer Yes when prompted to save.

6. Reboot the system, exit EmulationStation once again to go to the terminal.

7. If you've successfully completed all the above steps, you should see the output below when you type the command:

       cat /proc/asound/modules

Output should be:

       0 snd_usb_audio
       1 snd_bcm2835

Notice that the order has changed and it's now the snd_usb_audio that's on top of the list with an index of 0

8. Test the sound by going to EmulationStation and playing a game. You should immediately hear EmulationStation sounds when you go select from the list of games.

Load EmulationStation by typing the following command:

       emulationstation

