# RetroPie 2.6

Congratulations! You have discovered the wonderful world of RetroPie- your entire childhood is within reach! This page is for people just getting started on RetroPie 2.6. You can install RetroPie manually but for simplicity's sake this page will focus on installing the RetroPie SD card image. This page will give you the very basics to get you up and running from a blank SD card to first boot into Emulationstation. There will be separate pages for learning how to [transfer ROMs](https://github.com/petrockblog/RetroPie-Setup/wiki/How-to-get-ROMs-on-the-SD-card) and [set up controllers](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration).

If you hate reading then see this video. Otherwise read on! 

(There will also be videos for each individual step if you don't want to watch the whole thing all at once.)

<a href="https://www.youtube.com/watch?v=ySoTQhQqZdI
" target="_blank"><img src="https://i.ytimg.com/vi_webp/ySoTQhQqZdI/mqdefault.webp" 
alt="Ps1 Configuration Video" width="300" height="190" border="10" /></a>

## Hardware Needed:

 * Raspberry Pi (A, A+, B, B+,) or for best results: **Raspberry Pi 2 Model B**
 * Raspberry Pi Case (optional but recommended)
 * MicroSD Card (see compatible SD card list [**here**)](http://elinux.org/RPi_SD_cards)
 * MicroSD Card Reader (For installing retropie from your computer)
 * HDMI cable or 4 Pole RCA to 3.5mm Cable (HDMI works best)
 * Television or Computer Monitor- really any screen with HDMI or RCA ports
 * Wifi Dongle or Ethernet Cable (Wifi Dongle is more convenient- see compatible list [**here**)](http://elinux.org/RPi_USB_Wi-Fi_Adapters)
 * 5V 2A Micro USB Power Supply
 * USB Keyboard and Mouse (to get things set up or you can use SSH)
 * USB Game Controller of your choice (or you can get the [Control Block](http://blog.petrockblock.com/2014/12/29/controlblock-power-switch-and-io-for-the-raspberry-pi/) to use original controllers)

## Installation

### SD Images

There are currently two versions of RetroPie 2.6. There is one version for Raspberry Pi 1 (Model A, A+, B, B+) and there is a version for Raspberry Pi 2. Download the SD image for your version of Raspberry Pi:

**[Raspberry Pi 1](http://blog.petrockblock.com/retropie/retropie-downloads/retropie-project-sd-card-image-for-raspberry-pi-1/)**

**[Raspberry Pi 2](http://blog.petrockblock.com/retropie/retropie-downloads/download-info/retropie-sd-card-image-for-rpi-version-2/)**

(If these links become outdated see the downloads page [here](http://blog.petrockblock.com/retropie/retropie-downloads/).)

### Extract

Once you have downloaded your SD card image you need to extract it using a program such as [7-Zip](http://www.7-zip.org/). You will extract the downloaded .gz file and the extracted file will be a .img file.

### Format SD Card

Use a program such as [SD-Formatter](https://www.sdcard.org/downloads/formatter_4/) to format your SD card. (Note that this will erase all of the data on the SD card)

See this video for help:

<a href="https://www.youtube.com/watch?v=YdCzn4kTTO0
" target="_blank"><img src="https://i.ytimg.com/vi_webp/YdCzn4kTTO0/mqdefault.webp" 
alt="Ps1 Configuration Video" width="250" height="150" border="10" /></a>

### Install 2.6 Image on SD Card

You will use a program called [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/) to install the RetroPie 2.6 SD image on your MicroSD card. (You may need a MicroSD card reader to plug it into your computer)

See this video for help:

<a href="https://www.youtube.com/watch?v=gr52HC3V_Lg
" target="_blank"><img src="https://i.ytimg.com/vi_webp/gr52HC3V_Lg/mqdefault.webp" 
alt="Ps1 Configuration Video" width="250" height="150" border="10" /></a>

### Configurations

You'll need to make a few configurations before you can transfer your ROMs over. For these you will either need a keyboard or an internet connection to your Pi either through [Wifi](https://github.com/petrockblog/RetroPie-Setup/wiki/Setting-Up-Wifi) or Ethernet. 

Need help setting up your Wifi? See this video for help:

<a href="https://www.youtube.com/watch?v=hXzPJMAJAac
" target="_blank"><img src="https://i.ytimg.com/vi_webp/gr52HC3V_Lg/mqdefault.webp" 
alt="Set up your Wifi Dongle" width="250" height="150" border="10" /></a>

Want to connect to your Pi through your home computer rather than plugging a keyboard directly into it? See here:

<a href="https://www.youtube.com/watch?v=RyNii3UcHPw
" target="_blank"><img src="https://i.ytimg.com/vi_webp/gr52HC3V_Lg/mqdefault.webp" 
alt="Connect to your Pi with SSH" width="250" height="150" border="10" /></a>

### Expand Filesystem

`sudo raspi-config`

then select expand filesystem

and then reboot

See this video for help:

<a href="https://www.youtube.com/watch?v=ujYsnm-Zr4o
" target="_blank"><img src="https://i.ytimg.com/vi_webp/ujYsnm-Zr4o/mqdefault.webp" 
alt="Ps1 Configuration Video" width="250" height="150" border="10" /></a>

You should now be all ready to [configure your controllers](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration) and [transfer ROMs](https://github.com/petrockblog/RetroPie-Setup/wiki/How-to-get-ROMs-on-the-SD-card).