With a custom firmware such as the pro CFW and ME CFW and thanks to the natural flexibility of the PSP with the help of FuSa gamepad (a homebrew app for the PSP) you canget one of the best SNES gamepads for your Raspberry Pi

# What we need?

* A **PSP** model 1xxx 2xxx or 3xxx (PSP Go and street are not supported)
* A 1GB+ memory stick pro duo
* A mini USB to USB A cable
* A custom firmware
* The [FuSa gamepad](http://foosa.do.am/load/fusa_gamepad_version_03/3-1-0-33) app

# How to get started

Downliad the FuSa gamepad zip and then turn your PSP on with your memory stick allready inside your console and if it is a model 3000 run your CFW (older models do not need to run it because those models allready boots with the CFW loaded) plug your USB cable to your PSP and PC now uncompress your zip inside > /PSP/GAMES/ and safely unplug it from your PC, now run the app and connect it to your pi, the screen of your PSP sould be turned off and a LED should be lighted, the final result is this one

![FuSa gamepad working](http://i.imgur.com/cUnEP0O.jpg)

To configure it follow the RetroPie input configuration.

# FuSa with Kodi

To make it work on kodi take your keyboard and go to settings > advanced > input and chose the gamepad configuration, inside that dialog go to the keys and push enter, now configure it at your style, do not press anything in the moments it asks for a key you do not have and a little sugestion I can do to be able to change the volume inside Kodi with your PSP's volume buttons is to configure the right stick,right stick up = volume +, right stick right = d-pad up (temporaly) right stick down = volume - and right stick left let  the countdown go to zero, now go back to D-Pad up and set it agin to D-Pad up, let the countdown reach zero in the next item and press ok