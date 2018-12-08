With a custom firmware such as the pro CFW and ME CFW, and thanks to the natural flexibility of the PSP and the semi open hardware with the help of FuSa gamepad (a homebrew app for the PSP) you can get one of the best SNES gamepads for your Raspberry Pi

# What we need?

* A **PSP** model 1xxx 2xxx or 3xxx (models 2xxx & 3xxx preffered)
* A 1GB+ memory stick pro duo
* A mini USB to USB A cable
* A custom firmware
* A PC or your Pi to transfer the files
* The [FuSa gamepad](http://foosa.do.am/load/fusa_gamepad_version_03/3-1-0-33) app

# How to get started

Downliad the FuSa gamepad zip and then turn your PSP on with your memory stick allready inside your console and if it is a model 3000 or Go run your CFW (older models do not need to run it because those models allready boots with the CFW loaded) plug your USB cable to your PSP and PC now uncompress your zip inside > /PSP/GAMES/ and safely unplug it from your PC, now run the app and connect it to your pi, the screen of your PSP should be turned off and the power light should stay on the final result is this one

![FuSa gamepad working](http://i.imgur.com/cUnEP0O.jpg)

To configure it follow the RetroPie input configuration.

# FuSa with Kodi

To make it work on kodi take your keyboard and go to settings > advanced > input and chose the gamepad configuration, inside that dialog go to the keys and push enter, now configure it at your style, do not press anything in the moments it asks for a key you do not have and a little sugestion I can do to be able to change the volume inside Kodi with your PSP's volume buttons is to configure the right stick, right stick up = volume +, right stick right = d-pad up (temporaly) right stick down = volume - and right stick left let  the countdown go to zero, now go back to D-Pad up and set it agin to D-Pad up, let the countdown reach zero in the next item and press ok

# Recomended layout

For a consistent experience inside and outside Emulationstation includibg in Kodi and all the ReteoArch cores and because all the PS gamepads in Japan uses the same layout as a SNES gamepad but with diferent symbols I suggest use this buttons map plus my little suggestion for the volume buttons and the home button inside Kodi

![PSP layout](https://cloud.githubusercontent.com/assets/10035308/16599632/7f34c9ec-42c0-11e6-8988-0b2d6e795d10.png)

# Considerations

- The PSP street is not supported
. In FuSa gamepad the wireless switch works as an analogue stick switch
- If your PSP is in a good condition, this is much better than a generic controller or a 360 gamepad. The buttons are really responsive and the D Pad ideal for retro gaming
- The pi is NOT capable to fully charge a PSP
- The volume buttons do not work in emulationstation or RetroArch
- You can access to a more in depth configuration in the FuSa's ini files