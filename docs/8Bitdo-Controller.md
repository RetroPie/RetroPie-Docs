# Setting up an 8bitdo Bluetooth controller
![8bitdo Logo](http://www.8bitdo.com/images/logo.png)

![FC30](https://s21.postimg.cc/nvr2zk54j/fc30.png)
![FC30 Pro](https://s21.postimg.cc/muquafo4z/FC30_Pro.jpg)
![NES30](https://s21.postimg.cc/3qxiu3bar/nes30_1.jpg)

![NES30 Pro](https://s21.postimg.cc/vsbk7sgkz/NES30_Pro.jpg)
![SFC30](https://s21.postimg.cc/tp1504gs3/sfc30_1.jpg)
![SNES30](https://s21.postimg.cc/q6p53qfw3/snes30_1.jpg)

This guide will show how to use an 8bitdo controller with RetroPie.
Please make sure you are using at least RetroPie v4.0, and the **controller firmware versions listed below** (newer versions shouldn't cause an issue). It is not recommended to use beta firmware versions.

Please see the [8bitdo support page](http://support.8bitdo.com) for details on how to upgrade the firmware. Before you upgrade your firmware or attempt to register your controller, please make sure your controller is fully charged.  

#  A quick note about the 8bitdo Zero controller.

**PLEASE MAKE SURE IF YOU ARE USING AN 8BITDO ZERO YOU START THE CONTROLLER WITH R1+START WHEN YOU ARE COMPLETING THESE STEPS FOR AT LEAST THE FIRST TIME.**

It also may help to reset the controller by holding down the select button for 8 seconds if this does not work. Please note that using the R+START mode does result in different values for the buttons themselves so it may or may not function properly if started under any different mode in the future aside from R1+START. Also, ignore step 4 and turn the hack option on.

***

# Guide to add your controller

**1)** Run the RetroPie setup script, either through the Emulation Station menu option or via the command line.  
If you want to run this via the command line, quit Emulation Station by pressing F4 on the keyboard and type this at the command line: `sudo /home/pi/RetroPie-Setup/retropie_setup.sh`

**2)** Choose the "Configuration / Tools" menu choice
![Config / Tools Menu](https://s22.postimg.cc/7043daech/1_Config_Tools.jpg)

**3)** Choose the "bluetooth - Configure Bluetooth Devices" menu choice
![Bluetooth Menu](https://s22.postimg.cc/ofy9ezdb5/2_Bluetooth_Menu.jpg)

**4)** **Make sure the hack option is turned "off"**  
You need to make sure your controller is running the relevant [firmware](https://github.com/RetroPie/RetroPie-Setup/wiki/8Bitdo-Controller#firmware-versions-for-8bitdo-controllers) for this to work correctly, the versions are shown in this wiki article.
![Hack Off](https://s22.postimg.cc/df349yl29/2_5_Turn_hack_off.jpg)

**5)** Make sure your controller is powered on and searching for a connection.
With the FC30 Pro, this is done by holding the power button (left-hand side of the base of the controller) on until the side blue lights illuminate. With the SFC30/SN30/SF30 (with [firmware](https://github.com/RetroPie/RetroPie-Setup/wiki/8Bitdo-Controller#firmware-versions-for-8bitdo-controllers) v4.0+), this is done by first powering on the controller by holding the Start button for one second until the blue LED flashes, then hold the Select button for 3 seconds. The blue LED will flash rapidly to indicate pairing mode.

**6)** Choose the "Register and Connect to Bluetooth Device"
![Main Bluetooth Menu](https://s22.postimg.cc/lai92ik2p/3_Main_Bluetooth_Menu.jpg)

**7)** You will then see the "Searching" screen. If you have issues with the detection of the controller, you may find it helps to press some buttons on the controller when this screen is showing.
![Searching](https://s22.postimg.cc/3lqiaw8bl/4_Searching.jpg)

**8)** It may be the case that the first time the results are returned, the name of the controller doesn't show, or that the MAC address doesn't show at all. If that's the case, you can either select the device if you know the MAC or simply search again.
![No Name](https://s22.postimg.cc/g1n84n1nl/5_Search_Results_No_Name.jpg)

**9)** Here it has successfully detected the name of the controller, select OK here.
![Name](https://s22.postimg.cc/tju4gxdsx/6_Search_Results_Name.jpg)

**10)** Choose the "DisplayYesNo" optin to complete the registration process.
![Pairing](https://s22.postimg.cc/v05mz2gpt/7_Pairing.jpg)

**11)** Registration of the 8bitdo controller is complete and your blue LED lights should now be solid on (the FC30 Pro will glow).
![Connection Success](https://s22.postimg.cc/jp2zap9up/8_Connection_Success.jpg)

**12)** You must now setup the udev rule in order for Emulation Station to "see" the controller when you restart your Raspberry Pi.
![udev rule](https://s22.postimg.cc/ksn3mnuht/9_Setup_Udev_Menu.jpg)

**13)** Select your controller from the list.
![Select controller](https://s22.postimg.cc/tc6hkf2u9/10_Choose_device_for_udev.jpg)

**14)** This then adds the rule to the file specified, you don't need to manually take any extra steps here.
As indicated, you will need to reboot after completing these steps to make sure all the changes have taken effect.
![udev added](https://s22.postimg.cc/w7jkra6u9/11_Udev_rule_added.jpg)

**15)** The menu "Configure bluetooth connect mode" is optional, but using this can be very useful.
![Optional Settings](https://s22.postimg.cc/cqyv4rbq9/12_Optional_settings.jpg)

**16)** If your controller won't connect (LED change from flashing to solid) when restarting, change the mode to "boot". In most cases this should also enable the "background" option automatically, so you don't have to select this. If you have issues with the controller not auto connecting after waking from sleep/off mode, then try "background".
![Bluetooth connect modes](https://s22.postimg.cc/7gyhr7gv5/13_Bluetooth_connect_modes.jpg)

**17)** When this has been set, please reboot the Raspberry Pi.
Either during boot up or once in Emulation Station, when you turn the controller on it should connect without issue.

**18)** Configure the controller for Emulation Station and the emulators. Press Start in Emulation Station using your non-8bitdo controller and choose the "Configure Input" option.
![Configure Input](https://s22.postimg.cc/9msslpkbl/14_Configure_Input_ES.jpg)

**19)** You should see that Emulation Station can now see your 8bitdo controller
![ES see controller](https://s22.postimg.cc/vahqw5kpt/15_Game_Pads_Detected.jpg)

**20)** When you hold a button on your controller you should see its name appear at the bottom of the screen.
![ES shows name](https://s22.postimg.cc/4qp5u0k69/16_Game_Pads_Detected_FC30_Pro.jpg)

**21)** Follow the instructions as given here. If you make a mistake, just run the "Configure Input" process again.
![Add buttons to controller](https://s22.postimg.cc/dmzxxyash/17_Configuring_Game_Pad.jpg)

**22)** When that is complete your 8bitdo controller is ready to use!

The process will have written various controller configuration files for you.
The main RetroArch controller file will now be in:
`/opt/retropie/configs/all/retroarch-joypads/`

Here are some examples of the file that should be written. 

**FC30**

[FC30 Pro RetroArch config file](http://pastebin.com/raw/YCj3NW0h) (Firmware 1.69 - 8BitdoFC30Pro.cfg) 

**SFC30**

[SFC30 RetroArch config file](http://pastebin.com/raw/ZKbDkCBt) (Firmware 2.68 - 8BitdoSFC30GamePad.cfg)

**SNES30**

[SNES30 RetroArch config file](https://pastebin.com/raw/pfRyAk9s) (Firmware 3.00 - 8Bitdo SNES30 GamePad.cfg)

## Video Guide:
<div class="video-wrapper">
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/e2We6AElqg8" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
</div>

### Firmware Versions for 8bitdo controllers (June 2017)
![8bitdo controllers firmware](https://s3.postimg.cc/j47k633fn/8bitdo-firmware.png)  

You can download new firmware [here.](http://support.8bitdo.com)

### Troubleshooting
Please confirm your firmware version before raising a support ticket

### Some useful links
http://support.8bitdo.com  
https://github.com/libretro/retroarch-joypad-autoconfig/tree/master/udev