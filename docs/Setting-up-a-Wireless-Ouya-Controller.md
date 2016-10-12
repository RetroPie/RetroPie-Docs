With the death of Ouya as an independent entity there are a number of wireless Ouya controllers running around, looking for a way to be productive.  In an attempt to help these poor lost souls (and because I have no money for new controllers thanks to a baby who goes through diapers as if he did not know how expensive those things are and a daughter who “needs” a new toy or outfit with every other commercial that she sees) I have taken the time and effort to figure out how to make these controllers play nicely with RetroPie.  This was a somewhat long and frustrating process, but the results were well worth the efforts.  All instructions are in relation to the current iteration of RetroPie, 4.0.2.  I have used these set-up instructions with a Raspberry Pi 3 and a Raspberry Pi 1 B+, so they should work just as well for the Zero and 2.

#Step 1 (Connecting the controller):

* First access the “Bluetooth” configuration menu from the “RetroPie” Menu of EmulationStation. It can also be accessed from **RetroPie-Setup Script >> Setup >> Configure Bluetooth Devices**
* Next press the center “U” button on your Ouya controller (the small black one, not the black and blue action button) until the two middle lights flash slowly.

* Next choose the "Register and Connect to Bluetooth Device"

![Main Bluetooth Menu](https://s22.postimg.org/lai92ik2p/3_Main_Bluetooth_Menu.jpg)


* The "Searching..." screen will pop up. If your controller is not detected then try again.  It may help to press some buttons on the controller when this screen pops up.

![Searching](https://s22.postimg.org/3lqiaw8bl/4_Searching.jpg)


* The first time that you search you may only see the MAC address of your controller displayed.  You can either select the correct MAC address or search again, usually the second time around you will see the device’s name listed (in this case, OUYA Game Controller).

![No Name](https://s22.postimg.org/g1n84n1nl/5_Search_Results_No_Name.jpg)


* Once you have selected your device, choose the "DisplayYesNo" option to complete the registration process.

![Pairing](https://s22.postimg.org/v05mz2gpt/7_Pairing.jpg)


* Once the pairing is complete you will see a succes message and the first light on the controller will remain steady.

![Connection Success](https://s22.postimg.org/jp2zap9up/8_Connection_Success.jpg)


* Next choose “Set up udev Rule for Joypad” so that EmulationStation is able to “see” the controller.

![udev rule](https://s22.postimg.org/ksn3mnuht/9_Setup_Udev_Menu.jpg)


* Choose your OUYA Game Controller from the list.  This will set up the basic rule for how RetroPie sees the controller, but will not configure it, that happens later.

![Select controller](https://s22.postimg.org/tc6hkf2u9/10_Choose_device_for_udev.jpg)


* Next is "Configure bluetooth connect mode" this is optional, but using this can save a lot of hassle.  Set this up however you like.

![Optional Settings](https://s22.postimg.org/cqyv4rbq9/12_Optional_settings.jpg)
![Bluetooth connect modes](https://s22.postimg.org/7gyhr7gv5/13_Bluetooth_connect_modes.jpg)


* Once all of this is done, reboot the Raspberry Pi and configure the controller in EmulationStation.


#Step 2 (The initial configuration of the controller):

Once RetroPie resets connect the Ouya controller by tapping the center “U” button.  When this is done EmulationStation will “see” your controller.  If a configuration window does not pop up then connect a different controller or keyboard and hit “start” to pull up the necessary menu.
![ES see controller](https://s22.postimg.org/vahqw5kpt/15_Game_Pads_Detected.jpg)
![Add buttons to controller](https://s22.postimg.org/dmzxxyash/17_Configuring_Game_Pad.jpg)


Unfortunately the initial configuration only allows the Ouya controller to work properly with EmulationStation, and not the actual emulators.  This issue is easily solved with a few further steps.  This is not a difficult process, but it does take some work, so bare with me, it will all be worth it in the end.

The next part of the process involves configuring the controller in RetroArch.  Because the Ouya controller is not mapped properly by EmulationStation this is easiest if you have a keyboard or another controller connected so that you can easily navigate through the RetroArch UI.

* First access “RetroArch” through the “RetroPie” menu in EmulationStation.  

* Next choose “Settings” and then “Configuration” and change the “Save Configuration on Exit” to “on”.  Once this is done, back out to the previous menu.

![RetroArch Settings](https://retroresolution.files.wordpress.com/2015/12/retroarch-playstation-libretro-menu-selecting-settings-menu_cropped_640w.png?w=639&h=480)
![RetroArch Configuration](https://delightlylinux.files.wordpress.com/2016/02/rgui7.png)

* Next choose “Input”

![RetroArch Input](https://delightlylinux.files.wordpress.com/2016/02/rgui3.png)

* Next choose “Input User 1 Binds”

![RetroArch User 1 Binds](https://delightlylinux.files.wordpress.com/2016/02/rgui4.png)

* Next use your keyboard/extra controller to help you navigate (until the binds have been set up) and change the inputs as desired.  Make sure that the “Device Index” is set to “OUYA Game Controller (#1)”.  I also like to change the “Device Type” to “Retropad w/ Analog” and the “Analog to Digital Type” to “Left Analog” as this allows me to use the left analog stick as a d-pad.  You will need the button numbers later, so make sure to write down how RetroArch numbers the buttons.  After configuring the controller make sure to also choose “Save Autoconfig” and then back out to the previous screen.

![RetroArch Binds](http://blog.andressm.org/content/images/2014/Jul/Screenshot-2014-07-22-01-40-39.png)

* Next choose “Input Hotkey Binds” I don’t do much here, but I highly suggest setting the “Save State” and “Load State” to a button.  The hotkeys are used by pressing the desired hotkey plus the enable hotkey at the same time.  The hotkeys (including the enable hotkey button) will need some further configuration, but that will happen in another area, for now it is enough to set this part up.

![RetroArch Input Hotkey Binds](https://delightlylinux.files.wordpress.com/2016/02/rgui4.png)

* Finally back out to the main RetroArch menu and choose “Quit RetroArch”


#Step 3 (Editing the config files):

Once the previous steps are done, either hit f4 on a connected keyboard to enter the terminal, or shut down the system, pull the MicroSD card and plug it into a computer that will allow you to use a text editor to edit the some .cfg, .ini, and .cfg.bak files (I use my Chromebook for this, but whatever works for you is fine).

![RetroPie Terminal](http://www.rootzilopochtli.com/wp-content/uploads/2015/02/Screenshot-from-2015-02-12-190851.png)

The first files that need to be edited are the OUYA Game Controller.cfg and OUYA Game Controller.cfg.bak files.  These are located at: opt/retropie/configs/all/retroarch-joypads/  
(If you are editing within the Retropie terminal then type: cd ..  to move up a directory, then type: cd .. once more.  Then type:  cd /opt/retropie/configs/all/retroarch-joypads/  Once there, type: sudo nano opt/retropie/configs/all/retroarch-joypads/OUYA\ Game\ Controller.cfg  This will allow you to edit this file.)

You may find that some of the buttons are mapped incorrectly, simply map them as you like.  These file use the numberings that are found in RetroArch, not jstest.  Once that is done you will need to add some lines to the end of the file (the numbers in quotation marks are my personal choices, you can make them whichever buttons that you like):

```
input_load_state_btn = "10"
input_save_state_btn = "9"
input_enable_hotkey_btn = "16"
input_exit_emulator_btn = "15"
```

Once you have the file the way you want it save it and do the same for the OUYA Game Controller.cfg.bak file.  The .bak file is not usually created right away, so if it is not there, it is easiest just to copy and paste the .cfg file and rename the resulting extra .cfg as: OUYA Game Controller.cfg.bak.  In any event, this file must be identical, in everything but name, to the .cfg file.

There will be a third file called OUYAGameController.cfg (all one word).  This file will interfere with our recently edited OUYA Game Controller.cfg file, and must be deleted.  An identically named, but different, file will be created once a second Ouya controller is configured, but that one will not be a problem and we will deal with it later.

Here is my OUYA Game Controller.cfg configuration:

```
input_driver = "udev"
input_device = "OUYA Game Controller"
input_vendor_id = "2652"
input_product_id = "8532"
input_b_btn = "3"
input_y_btn = "6"
input_select_btn = "10"
input_start_btn = "9"
input_up_btn = "11"
input_down_btn = "12"
input_left_btn = "13"
input_right_btn = "14"
input_a_btn = "4"
input_x_btn = "5"
input_l_btn = "7"
input_r_btn = "8"
input_l2_btn = "15"
input_r2_btn = "16"
input_l_x_plus_axis = "+0"
input_l_x_minus_axis = "-0"
input_l_y_plus_axis = "+1"
input_l_y_minus_axis = "-1"
input_r_x_plus_axis = "+3"
input_r_x_minus_axis = "-3"
input_r_y_plus_axis = "+4"
input_r_y_minus_axis = "-4"
input_save_state_btn = "9"
input_load_state_btn = "10"
input_enable_hotkey_btn = "16"
input_exit_emulator_btn = "15"
```

Once the files are edited/created and saved, pop the microSD card back into the Raspberry Pi (or if you are in the terminal, type: cd to change back to the main directory and then type: sudo reboot now to reboot the system).  The controller should be working properly in all emulators other than the non-RetroArch emulators (such as the N64).  If you only have one Ouya controller and do not use any of the non-RetroArch emulators, then you are now good to go.  If you would like to add a second Ouya controller, then read on.  As to the non-RetroArch configurations, there aren’t many non-RetroArch emulators, and the only one that I use is the mupen64plus emulator, so I will show you how to configure this a little further down the line, but for all the others you are on your own (at least until some helpful person comes along to add to this entry).



#Step 4 (Adding a second Ouya controller):

This is actually much easier, as the necessary files have already been set up, so there are really only a few short steps.

* Make sure that the first Ouya controller is connected so that the second one will configure properly as controller #2.  Once the second controller is set up whichever one is connected first will use controller #1’s settings, regardless of whether or not it was originally set up first.

* Connect the second Ouya controller just as you did the first.

* Configure the controller in EmulationStation.  This will create a new OUYAGameController.cfg, but this one does not interfere with the proper use of the controllers, so it gets to stay.

* Head into RetroArch and configure the second controller just as you did the first, but this time do so in “Input User 2 Binds”  and make sure that the “Device Index” is set to “OUYA Game Controller (#2)”.

* Once the second controller is configured in RetroArch you are good to go.  Keep in mind that the first controller will be the only one that will be able to exit or save/load state.



#Step 5 (Configuring the Ouya controller for mupen64plus):

The mupen64plus does not use RetroArch configurations, so in order to use the Ouya controller with the preinstalled N64 emulator you will need to configure this separately.

* The first step will be to run jstest to see how the non-RetroArch systems number the Ouya’s buttons.  While the Ouya controller is connected head into the terminal by typing f4 on a connected keyboard, then type jstest dev/input/js0 When jstest is running, tap each button on the Ouya controller to see how they are numbered, you will need this info to edit the config files.  Press ctrl + c to exit jstest.

* Next you will edit the config files.  Keep in mind that the hotkeys will generally be single buttons rather than combos, and the hotkeys will need to be otherwise unassigned buttons.

* First edit the autoconf.cfg file so that the hotkeys are turned off, which will allow you to edit mupen64plus.cfg (without editing this the mupen64plus.cfg file will be overwritten by the autoconf.cfg file, which will not work for us).  The autoconf.cfg file is located at opt/retropie/configs/all/ you will need to edit mupen64plus_hotkeys = "1" change the “1” to "0".  I was unabe to edit this file on my computer, but I had no issues doing so in terminal.

* Next edit the mupen64plus.cfg file located at opt/retropie/configs/n64/ You will need to edit the Joy Mapping Stop, Joy Mapping Save State, and Joy Mapping Load State entries to your prefered buttons.  Then add these lines to the end of the "Digital button configuration mappings":

Stop = "button(13)"
Save State = "button(6)"
Load State = "button(7)"
(Obviously the particular button numbers are going to depend on what you would like to map, but the above are my personal choices).

* Finally, edit the InputAutoCfg.ini and InputAutoCfg.ini.bak files, located at opt/retropie/configs/n64/  Map the buttons using the jstest numbers.  If you want to use the Left Shoulder button you will have to add this, as it is not included in the initial config.  As with the OUYA Game Controller.cfg.bak file, the InputAutoCfg.ini.bak file may not exist yet, so once you have the InputAutoCfg.ini edited properly you'll need to copy, paste and rename the file just as you did with the OUYA Game Controller.cfg file.  Once you have these files set up you will be good to go.

Here is my InputAutoCfg.ini configuration:

```
; InputAutoCfg.ini for Mupen64Plus SDL Input plugin

; OUYA Game Controller_START 
[OUYA Game Controller]
plugged = True
plugin = 2
mouse = False
AnalogDeadzone = 4096,4096
AnalogPeak = 32768,32768 
C Button D = axis(4+) 
C Button L = axis(3-) 
Z Trig = button(0) 
Start = button(12) 
Y Axis = axis(1-,1+)
DPad U = button(8) 
C Button U = button(2) axis(4-) 
A Button = button(1) 
DPad D = button(9) 
X Axis = axis(0-,0+)
L Trig = button(4)
R Trig = button(5) 
DPad R = button(11) 
B Button = button(2) 
DPad L = button(10) 
C Button R = axis(3+) 
; OUYA Game Controller_END 
```

That’s it, your Ouya controller should now be good to go with most emulators as well as the N64 emulator.  Enjoy retrogaming using your newly configured Ouya wireless controller!