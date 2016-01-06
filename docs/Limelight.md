# Quickguide for configuring limelight with Retropie and Emulation Station

This guide will enable your Raspberry PI to work with NVIDIA Gamestream to stream Steam games to your Raspberry pi. To use this Guide you must have a Gamestream ready PC with a Gamestream enabled NVIDIA GPU. Geforce experience app should be version 2.2.2 or newer!

With this guide you get limelight integrated to Emulation station for quick access and the games will run 1080p / 30FPS with basically zero input lag (tested with a wired connection and Raspberry pi 2)

This guide is intended for Rasperry Pi 2 with Retropie, but should also work on a Pi B+

I strongly suggest you configure your host PC to use a static IP-address, before you start!

In the shell with the PI-user

install limelight:

pi@retropie ~ $ **mkdir limelight**

pi@retropie ~ $ **cd limelight**

pi@retropie ~/limelight $ **sudo apt-get update && sudo apt-get install oracle-java8-jdk** 
﻿
pi@retropie ~/limelight $ **wget https://github.com/irtimmer/limelight-embedded/releases/download/v1.2.1/libopus.so**

pi@retropie ~/limelight $ **wget https://github.com/irtimmer/limelight-embedded/releases/download/v1.2.1/limelight.jar**

Next pair your computer with limelight

Lookup your Nvidia Gamestream PC:s IP address

pi@retropie ~/limelight $ **java -jar limelight.jar discover**

pi@retropie ~/limelight $ **java -jar limelight.jar pair XXX.XXX.XXX.XXX**

(for xxx.xxx.xxx.xxx use the ip-address found with discover)

**Now input the displayed number on the host PC**

Next we configure a key map for the USB-controller used with limelight (if event0 does not give you the proper device you can try next event1-event3)

pi@retropie ~/limelight $ **java -jar limelight.jar map -input /dev/input/event0 mapfile.map**

Add limelight to the ports section of Emulation station for easy access

pi@retropie ~ $ **cd /home/pi/RetroPie/roms/ports/**

pi@retropie ~/RetroPie/roms/ports $ **nano limelight.sh**

in nano add this text:

`#!/bin/bash`

`cd /home/pi/limelight/ && java -jar limelight.jar stream -1080 -30fps XXX.XXX.XXX.XXX -app Steam -mapping mapfile.map`

_(for xxx.xxx.xxx.xxx use the ip-address from before)_

press ctrl+x and press y and enter

pi@retropie ~/RetroPie/roms/ports $ **chmod +x limelight.sh**

restart the raspberry pi and limelight will be available from the ports section.


***

**Extra Tip!**

Alternatively you can also try 60fps with 720p by modifying the limelight.sh with this command

cd /home/pi/limelight/ && java -jar limelight.jar stream -720 -60fps XXX.XXX.XXX.XXX -app Steam -mapping mapfile.map

(sadly 1080 and 60fps causes unplayable input lag, and mostly crashes without returning to emulation station on exit)

**Extra Tip2!**

Create two .sh files named limelight720.sh and limelight1080.sh in the ports folder with both setups for fast access to both resolutions and framerates


***

**Advanced configuration**

To get 1080p 60FPS streaming running without lag on the PI2 you can try these overclock settings that resolved the issues:

arm_freq=1100
core_freq=500
sdram_freq=500
h264_freq=500
over_voltage=8
force_turbo=1
temp_limit=80

DISCLAIMER: Force_turbo will void your warranty since its keeps the clock on 100% without throttling, so you should use a heatsink with these settings.


***

The Guide is quite outdated in a few days, I made an installer script to make things really easy to anyone wanting to try this out:

https://github.com/stsfin/RetropieLimelightInstaller

Please use the script its a turnkey solution