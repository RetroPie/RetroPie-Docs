This guide will enable your Raspberry PI to work with NVIDIA Gamestream to stream Steam games to your Raspberry pi. To use this Guide you must have a Gamestream ready PC with a Gamestream enabled NVIDIA GPU.

With this guid you get limelight integrated to Emulation station for quick access and the games will run 1080p / 30FPS with basically zero input lag (tested with a wired connection and Raspberry pi 2)

This guide is intended for Rasperry Pi 2 with Retropie, but should also work on a Pi B+

I strongly suggest you configure your host PC to use a static IP-address, before you start!

In the shell with the PI-user

install limelight:

pi@retropie ~ $ **mkdir limelight**

pi@retropie ~ $ **cd limelight**

pi@retropie ~/limelight $ **sudo apt-get update && sudo apt-get install oracle-java8-jdk** ﻿
pi@retropie ~/limelight $ **wget https://github.com/irtimmer/limelight-embedded/releases/download/v1.2.1/libopus.so**
pi@retropie ~/limelight $ **wget https://github.com/irtimmer/limelight-embedded/releases/download/v1.2.1/limelight.jar**

Next pair your computer with limelight

Lookup your Nvidia Gamestream PC:s IP address

pi@retropie ~/limelight $ **java -jar limelight.jar discover**

pi@retropie ~/limelight $ **java -jar limelight.jar pair XXX.XXX.XXX.XXX**

**_(for xxx.xxx.xxx.xxx use the ip-address found with discover)_**

Configuring a key map for the USB-controller used with limelight (if event0 does not give you the proper device you can try next event1-event3)

pi@retropie ~/limelight $ **java -jar limelight.jar map -input /dev/input/event0 mapfile.map**

Add limelight to the ports section of Emulation station for easy access

pi@retropie ~ $ **cd /home/pi/RetroPie/roms/ports/**
pi@retropie ~/RetroPie/roms/ports $ **nano limelight.sh**

in nano add this text:

`#!/bin/bash`
`cd /home/pi/limelight/ && java -jar limelight.jar stream -1080 -30fps XXX.XXX.XXX.XXX -app Steam -mapping mapfile.map`

(for xxx.xxx.xxx.xxx use the ip-address from before)

press ctrl+x and press y and enter

pi@retropie ~/RetroPie/roms/ports $ **chmod +x limelight.sh**

restart the raspberry pi and limelight will be available from the ports section