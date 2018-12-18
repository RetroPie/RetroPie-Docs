# How to configure sound for RetroPie EmulationStation

In July 2018, the range of audio configuration options for Linux and RPi EmulationStation users was greatly enhanced. Prior to July 2018, users could only select the audio card (known as an AudioCard in EmulationStation), and were unable to select which audio mixer to use on that audio card. EmulationStation only looked for the 'default' audio mixer, which was too restrictive when used with unusual hardware, or Rpi Audio HATs. The July 2018 change added the ability to choose the audio mixer name from a far greater range of options, as well as allowing custom options to be set in the es_settings.cfg file. More details on how that works is below. The hope was that it would give people the flexibility that they needed to avoid the many sound issues that people with people were having with USB Audio devices and aftermarket Linux and RPi audio cards.

NOTE: Windows uses a different audio subsystem, so the changes below do not apply to a Windows version of EmulationStation... only the Linux and RPi versions.

## Choosing Audio from the new EmulationStation selectable audio options

### Step 1: Configuring the Operating System

EmulationStation does not configure the operating system at all. You need to have a working ALSA setup in order for EmulationStation to make use of it. The rest of this document goes into some detail regarding configuring your operating system to get your sound working, so we won't go into too much detail here. But we will cover some standard functionality.

#### Raspberry Pi Sound in Raspbian

If you have a Raspberry Pi, this will cover the basic sound configuration in Raspbian to get the platform working.

##### Using the built-in 3.5mm headphone jack

If you have a standard RPi and want to use the 3.5mm headphone jack then you are in luck. You're pretty much ready to go without any real modification, as the RPi will automatically use the headphone jack when it senses a plug in the socket. 

In some instances though, you will need to manually modify the raspberry pi boot config file (/boot/config.txt) and ADD the following lines to those already there: 

````
# This line should already be in the file, but if it's not then make sure to add it.
dtparam=audio=on

# Pretends no audio formats are supported by HDMI display, forcing all sound out the 3.5mm headphone jack.
# May not be needed for all HDMI devices
hdmi_ignore_edid_audio=1		
````

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.


##### Using the built-in HDMI Audio
If you have a standard RPi and want to send audio over the HDMI connector then it should just work. In some instances though, you will need to manually modify the raspberry pi boot config file (/boot/config.txt) and ADD the following lines to those already there: 

````
# forces HDMI mode
hdmi_drive=2   			

# Setting hdmi_force_hotplug to 1 pretends that the HDMI hotplug signal is asserted, so it appears that a HDMI display is attached. In other words, HDMI output mode will be used, even if no HDMI monitor is detected.
hdmi_force_hotplug=1   			


# Pretends all audio formats are supported by display, allowing passthrough of DTS/AC even when not reported as supported.
# May not be needed for all HDMI devices
hdmi_force_edid_audio=1		
````

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.


##### Using a USB Audio Device

If you want better sound than the standard on-board sound chip can provide, then the next level up is an external USB Audio dongle. These plug into a USB port on the RPi and allow you have better quality sound.  

You don't need to disable the on-board sound if you don't want to, but I would recommend it as can simply ALSA configuration and avoid some configuration issues later. The commands to enable USB audio and disable the on-board sound card are below:

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and comment out the `dtparam=audio=on` line by putting a `#` in front of it like this: 
````
#dtparam=audio=on
````

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and ADD the following lines to those already there: 
````
dtparam=audio=off
````

This simply will turn off the on-board sound card during boot up. This in turn will allow the USB Audio Card to register as the first sound card, meaning that it will be assigned the as the "default" Audio Card. This in turn will make it much simpler when configuring the sound within EmulationStation.

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.

> :exclamation: If the above doesn't work, then you can use some other instructions on this page to [get USB Audio set up](https://github.com/RetroPie/RetroPie-Setup/wiki/Sound-Issues#usb-audio).


##### Using a Raspberry Pi Audio HAT (e.g. Justboom, Hifiberry)

If you want better sound than the standard on-board sound chip can provide, then you can look at something like a Justboom or a Hifiberry RPi HAT. These add on cards connect to the RPi GPIO port and allow you have audiophile quality sound. They really provide excellent sound and are the option you should choose if you are building a top quality arcade machine.

You don't need to disable the on-board sound if you don't want to, but I would recommend it as can simply ALSA configuration and avoid some configuration issues later. The list below is a list of settings for common cards:

**For the JustBoom Amp, Amp Zero, DAC and DAC Zero**

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and comment out the `dtparam=audio=on` line by putting a `#` in front of it like this: 
````
#dtparam=audio=on
````

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and ADD the following lines to those already there: 
````
dtparam=audio=off
dtoverlay=justboom-dac
````

If you are using Raspbian 8 (Jessie) or earlier, then you need to also add the following line too. NOTE - If you are on Raspbian 9 (Stretch) or later you should NOT add this line:
````
dtoverlay=i2s-mmap
````

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.

**For the JustBoom Digi and Digi Zero**

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and comment out the `dtparam=audio=on` line by putting a `#` in front of it like this: 
````
#dtparam=audio=on
````

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and ADD the following lines to those already there: 
````
dtparam=audio=off
dtoverlay=justboom-digi
````

If you are using Raspbian 8 (Jessie) or earlier, then you need to also add the following line too. NOTE - If you are on Raspbian 9 (Stretch) or later you should NOT add this line:
````
dtoverlay=i2s-mmap
````

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.

**For the Hifiberry DAC FOR RASPBERRY PI 1/DAC+ LIGHT/DAC ZERO/MINIAMP/BEOCREATE/DAC+ DSP**

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and comment out the `dtparam=audio=on` line by putting a `#` in front of it like this: 
````
#dtparam=audio=on
````

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and ADD the following lines to those already there: 
````
dtparam=audio=off
dtoverlay=hifiberry-dac
````

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.

**For the Hifiberry DAC+ STANDARD/PRO/AMP2**

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and comment out the `dtparam=audio=on` line by putting a `#` in front of it like this: 
````
#dtparam=audio=on
````

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and ADD the following lines to those already there: 
````
dtparam=audio=off
dtoverlay=hifiberry-dacplus
````

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.

**For the Hifiberry DIGI/DIGI+ ALL MODELS**

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and comment out the `dtparam=audio=on` line by putting a `#` in front of it like this: 
````
#dtparam=audio=on
````

Modify the raspberry pi boot config file (/boot/config.txt) and ADD the following lines to those already there: 
````
dtparam=audio=off
dtoverlay=hifiberry-digi
````

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.

**For the Hifiberry AMP+ (NOT AMP2!)**

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and comment out the `dtparam=audio=on` line by putting a `#` in front of it like this: 
````
#dtparam=audio=on
````

Modify the raspberry pi boot config file (`nano /boot/config.txt`) and ADD the following lines to those already there: 
````
dtparam=audio=off
dtoverlay=hifiberry-amp
````

Once you've made the change, save the file, restart your Raspberry Pi, and move onto Step 2.

### Step 2: Choosing the Audio Card in EmulationStation

Once you've made sure the operating system configuration has been made correctly, then the next step is to configure EmulationStation. You can select which ALSA Audio Card you want EmulationStation to use, by choosing the relevant AUDIO CARD option from the SOUND SETTINGS menu. You can choose from one of the following options:

* **local**: (RPi specific) This sets the sound output to the 3.5mm Onboard Audio Card. This is the 2nd most common option for RPi Systems.
* **hdmi**: (RPi specific) This sets the sound output to the HDMI Audio Card. This is the most common option for RPi Systems.
* **both**: (RPi specific) This sets the sound output to both the HDMI Audio Card and the 3.5mm Onboard Audio Card. 
* **default**: This sets the sound output to the ALSA "default" audio card. This is the most common option for Linux Operating Systems.
* **sysdefault**: This sets the sound output to the ALSA "default" audio card. This is the 2nd most common option for Linux Operating Systems.
* **dmix**: This sets the sound output to the ALSA dmix plugin, which allows direct mixing of multiple audio streams. This option is unlikely to be used.
* **hw**: This sets the sound output to the ALSA hw plugin, which talks directly to the ALSA kernel. This option is unlikely to be used.
* **plughw**: This sets the sound output to the ALSA plughw plugin, which talks directly to the ALSA kernel but allows you to set things like the sample rate, sample format and number of channels. This option is unlikely to be used.
* **null**: This sets the sound output to the ALSA "null" audio card, which effectively plays no sound anywhere. This option is unlikely to be used.

NOTE: If you do not  see any of these options when you run aplay -L on your system, do not despair. You can [add your own custom audio card using these instructions](#adding-custom-audio-card-audio-device-or-omx-player-audio-device) and everything will work!

In order to figure out what the name of your Audio Card is on your device, open a terminal window and run 'aplay -L'. This will generate a list of Audio Cards similar to the one below:

````
pi@raspberrypi:~ $ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=sndrpijustboomd
    snd_rpi_justboom_dac,
    Default Audio Device
sysdefault:CARD=sndrpijustboomd
    snd_rpi_justboom_dac,
    Default Audio Device
dmix:CARD=sndrpijustboomd,DEV=0
    snd_rpi_justboom_dac,
    Direct sample mixing device
dsnoop:CARD=sndrpijustboomd,DEV=0
    snd_rpi_justboom_dac,
    Direct sample snooping device
hw:CARD=sndrpijustboomd,DEV=0
    snd_rpi_justboom_dac,
    Direct hardware device without any conversions
plughw:CARD=sndrpijustboomd,DEV=0
    snd_rpi_justboom_dac,
    Hardware device with all software conversions
````
	
As you can see from the list above, I have a justboom RPi HAT, and the justboom sound driver has configured itself as the "default" Audio Card, meaning that I have disabled the on-board built-in sound card, and the Justboom RPi HAT has been assigned as the default Audio Card in Raspbian. I would need to select the "default" AUDIO CARD option from within EmulationStation in order to use my JustBoom Audio HAT.

## Step 3: Choosing the Audio Device (Mixer)

Third step is to select which Audio Mixer you want EmulationStation to use on the ALSA Audio Card you selected in Step 2, by choosing the relevant AUDIO DEVICE option from the SOUND SETTINGS menu. You can choose from one of the following options:

* **PCM**: This controls the volume of the sound going into the audio device from the Operating System. This is a common audio mixer option for the standard RPi.
* **Speaker**: This is another mixer option, but I'm unsure what it selects as I've never used it.
* **Master**: This is typically the main volume control and is the most common audio mixer option. This is the option that you should use for most devices (including Hifiberry Audio RPi HATs). 
* **Digital**: This audio mixer controls the volume levels when it's still digital. This is the option that you should use for Justboom Audio RPi HATs. 
* **Analogue**: This is another option for use for sound cards that use the Analogue mixer to control the main volume.

NOTE: If you do not see any of these options when you run 'amixer scontrols -D <AudioCard>' on your system, do not despair. You can [add your own custom audio device mixer using these instructions](#adding-custom-audio-card-audio-device-or-omx-player-audio-device) and everything will work!

In order to figure out what the name of your Audio Device (mixer) is on your selected Audio Card, open a terminal window and running 'amixer scontrols -D <AudioCard>', where <AudioCard> is replaced with the name of your Audio Card that you
found in Step 1. This will generate a list of Audio Cards similar to the one below:

````
pi@raspberrypi:~ $ amixer scontrols -D default
Simple mixer control 'DSP Program',0
Simple mixer control 'Analogue',0
Simple mixer control 'Analogue Playback Boost',0
Simple mixer control 'Auto Mute',0
Simple mixer control 'Auto Mute Mono',0
Simple mixer control 'Auto Mute Time Left',0
Simple mixer control 'Auto Mute Time Right',0
Simple mixer control 'Clock Missing Period',0
Simple mixer control 'Deemphasis',0
Simple mixer control 'Digital',0
Simple mixer control 'Max Overclock DAC',0
Simple mixer control 'Max Overclock DSP',0
Simple mixer control 'Max Overclock PLL',0
Simple mixer control 'Volume Ramp Down Emergency Rate',0
Simple mixer control 'Volume Ramp Down Emergency Step',0
Simple mixer control 'Volume Ramp Down Rate',0
Simple mixer control 'Volume Ramp Down Step',0
Simple mixer control 'Volume Ramp Up Rate',0
Simple mixer control 'Volume Ramp Up Step',0
````

As you can see, I don't have a "Master" audio mixer, or a "PCM" audio mixer, but I do have a "Digital" audio mixer. So I select "Digital" as the AUDIO DEVICE option in EmulationStation SOUND SETTINGS menu. 

### Step 4: Choosing the OMX Player Audio Device

The last step is to select which Audio Device that OMXPlayer will use to play videos. EmulationStation uses OMX Player to play videos, and it doesn't use the ALSA settings we set earlier - it has it's own OMX PLAYER AUDIO DEVICE setting within the EmulationStation SOUND SETTINGS menu. You can choose from one of the following options:

* **local**: (RPi specific) This sets the OMX Player sound output to the 3.5mm Onboard Audio Card. This is the 2nd most common option for RPi Systems.
* **hdmi**: (RPi specific) This sets the OMX Player sound output to the HDMI Audio Card. This is the most common option for RPi Systems.
* **both: (RPi specific) This sets the OMX Player sound output to both the HDMI Audio Card and the 3.5mm Onboard Audio Card. 
* **alsa:hw:0,0**: This sets the OMX Player sound output to the first Audio Mixer on the first Audio Card on the system. For the RPi this is the onboard audio (unless you've disabled it, in which case this is the RPi Audio HAT or USB Audio Device you've added)
* **alsa:hw:1,0**: This sets the OMX Player sound output to the first Audio Mixer on the second Audio Card on the system. For the RPi this is the RPi Audio HAT or USB Audio Device you've added (only if you have NOT disabled the onboard audio!).

NOTE: If you do not see any of these options when you run aplay -L on your system, do not despair. You can [add your own custom OMX Audio Device using these instructions](#adding-custom-audio-card-audio-device-or-omx-player-audio-device) and everything will work!

I had disabled the RPi onboard audio on my device, so I selected "alsa:hw:0,0" for the OMX PLAYER AUDIO DEVICE within EmulationStation SOUND SETTINGS. This was the final bit of configuration required, and I was able to play video games with sound coming out the right places, and watch the preview videos with sound. 

## Adding custom Audio Card, Audio Device or OMX Player Audio Device

EmulationStation now has the ability to use custom settings entered into the es_settings.cfg file manually. You can add any custom cards, mixers and OMX players that you want. This will give even the most advanced users enough extra power that should avoid even the most strange setups.

### Adding a Custom Audio Card

To add a custom Audio Card, edit the "AudioCard" setting in the es_settings.cfg file and replace the value with the name of your Audio Card. You can find this out by opening a terminal window and running 'aplay -L'. This will generate a list of Audio Cards similar to the one below:

````
pi@raspberrypi:~ $ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=sndrpijustboomd
    snd_rpi_justboom_dac,
    Default Audio Device
sysdefault:CARD=sndrpijustboomd
    snd_rpi_justboom_dac,
    Default Audio Device
dmix:CARD=sndrpijustboomd,DEV=0
    snd_rpi_justboom_dac,
    Direct sample mixing device
dsnoop:CARD=sndrpijustboomd,DEV=0
    snd_rpi_justboom_dac,
    Direct sample snooping device
hw:CARD=sndrpijustboomd,DEV=0
    snd_rpi_justboom_dac,
    Direct hardware device without any conversions
plughw:CARD=sndrpijustboomd,DEV=0
    snd_rpi_justboom_dac,
    Hardware device with all software conversions
````

Select any one of the Audio Cards listed by using the first word on the line in your AudioCard settings in the es_settings.cfg, e.g.

````
<string name="AudioCard" value="default" />
````

NOTE: If the AudioCard value is not listed, please either close and reopen EmulationStation (the settings is created upon close if it doesn't exist), or add it manually to the es_settings.cfg file.

### Adding a Custom Audio Device (Audio Mixer)

To add a custom Audio Device (mixer), edit the "AudioDevice" setting and replace the value with the name of your Audio Device. You can get a list off avilable Audio Devices on the Audio Card by opening a terminal window and running 'amixer scontrols -D <AudioCard>', where <AudioCard> is replaced with the name of your Audio Card that you found in Step 1.  This command will generate a list of Audio Devices (mixers) that you can use in the AudioDevice setting in the es_settings.cfg file, e.g.

````
pi@raspberrypi:~ $ amixer scontrols -D default
Simple mixer control 'DSP Program',0
Simple mixer control 'Analogue',0
Simple mixer control 'Analogue Playback Boost',0
Simple mixer control 'Auto Mute',0
Simple mixer control 'Auto Mute Mono',0
Simple mixer control 'Auto Mute Time Left',0
Simple mixer control 'Auto Mute Time Right',0
Simple mixer control 'Clock Missing Period',0
Simple mixer control 'Deemphasis',0
Simple mixer control 'Digital',0
Simple mixer control 'Max Overclock DAC',0
Simple mixer control 'Max Overclock DSP',0
Simple mixer control 'Max Overclock PLL',0
Simple mixer control 'Volume Ramp Down Emergency Rate',0
Simple mixer control 'Volume Ramp Down Emergency Step',0
Simple mixer control 'Volume Ramp Down Rate',0
Simple mixer control 'Volume Ramp Down Step',0
Simple mixer control 'Volume Ramp Up Rate',0
Simple mixer control 'Volume Ramp Up Step',0
````

Select any one of the Simple mixer controls listed by using the name within the quotes within the AudioDevice setting in your es_settings.cfg file, e.g.

````
<string name="AudioDevice" value="Digital" />`
````

Using the above example as a starting point, changing the AudoCard and AudioDevice settings within the es_settings.cfg file to the following values will use the 'default' Audio Card to play sounds, and will use the 'Digital' mixer (Audio Device) to control the volume.

````
<string name="AudioCard" value="default" />
<string name="AudioDevice" value="Digital" />
````

NOTE: Any custom manually used settings will be overwritten if you select any of the other options in the GUI and exit the Sound Settings window, as the Sound Settings GUI window overwrites the es_settings.cfg options when you exit the window.

### Adding a Custom OMX Player Audio Card

To add a custom OMX Player Audio Card, edit the "OMXAudioDev" setting and replace the value with the name of your Audio Card. You can get a list off available Audio Card by opening a terminal window and running 'aplay -L', command will generate a list of Audio Devices (mixers) that you can use in the AudioDevice setting in the es_settings.cfg file, e.g.

````
pi@raspberrypi:~ $ amixer scontrols -D default
Simple mixer control 'DSP Program',0
Simple mixer control 'Analogue',0
Simple mixer control 'Analogue Playback Boost',0
Simple mixer control 'Auto Mute',0
Simple mixer control 'Auto Mute Mono',0
Simple mixer control 'Auto Mute Time Left',0
Simple mixer control 'Auto Mute Time Right',0
Simple mixer control 'Clock Missing Period',0
Simple mixer control 'Deemphasis',0
Simple mixer control 'Digital',0
Simple mixer control 'Max Overclock DAC',0
Simple mixer control 'Max Overclock DSP',0
Simple mixer control 'Max Overclock PLL',0
Simple mixer control 'Volume Ramp Down Emergency Rate',0
Simple mixer control 'Volume Ramp Down Emergency Step',0
Simple mixer control 'Volume Ramp Down Rate',0
Simple mixer control 'Volume Ramp Down Step',0
Simple mixer control 'Volume Ramp Up Rate',0
Simple mixer control 'Volume Ramp Up Step',0
````

Select any one of the Simple mixer controls listed by using the name within the quotes within the OMXAudioDev setting in your es_settings.cfg file, or you can use the "alsa:hw:x,y" format, where the x is the number of the AudioCard (0 = first audio card, 1 = 2nd audio card ...) and y is the number of the audio mixer device on that card (0 = first audio mixer device, 1 = 2nd audio mixer device ...) e.g.

````
<string name="OMXAudioDev" value="alsa:hw:1,2" />
````

The above example will tell OMX Player to use the third mixer on the second Audio Card to play video sounds.


NOTE: Any custom manually used settings will be overwritten if you select any of the other options in the GUI and exit the Sound Settings window, as the Sound Settings GUI window overwrites the es_settings.cfg options when you exit the window.

# Sound Troubleshooting

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
