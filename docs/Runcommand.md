# Runcommand Launch Menu

|Version|
|---|
|3.7|

Each time you load a ROM there is an option to open what is called the Runcommand Launch Menu. This is accessed by pressing any key on the keyboard or js0 (button 0 on your joypad- it will vary depending on the gamepad used)


![runcommandlaunch](https://cloud.githubusercontent.com/assets/10035308/12870184/99acb464-ccf6-11e5-9f32-7f2ef3c17b3a.png)


Once you press Js0 or a button on your keyboard, it will open up into this menu (this menu may vary depending on the emulator you are running and version of retropie you are using- this image is for the super nintendo):

![runcommandmenu](https://cloud.githubusercontent.com/assets/10035308/10265893/b65c94ee-69ff-11e5-9195-f6a996f4b35b.png)

If you select the first option, if there is more than one emulator, you can swap which emulator is used:

![defaultemulator](https://cloud.githubusercontent.com/assets/10035308/10265899/de7127ec-69ff-11e5-99b6-aa2df9247da6.png)

There are also varying options to change video settings, RetroArch configs for that system, etc. 

In the past there were multiple rom folders for each emulator but they got confusing so now there is only one rom folder for each system and the emulator used can be loaded dynamically so there is no longer a need for multiple rom folders for each system. 

### Configuring Runcommand:

Starting with RetroPie 3.5 you can enable and disable different functions of the Runcommand Launch Menu. This is configured via RetroPie-Setup or via the runcommand configuration option in the RetroPie area of Emulation Station. 

![runcommand](https://cloud.githubusercontent.com/assets/10035308/12870161/2608ac8a-ccf5-11e5-8d78-97cf5650cee4.png)

- **Launch Menu:** Enable or disable the runcommand launch menu
- **Launch Menu Art:** If enabled, any scraped box art you have for a game with show up as a splashscreen while your game loads up.
- **Launch Menu Joystick Control:** You can disable the joystick support so that your kids don't accidentally mess up settings. Note that this only disables the joystick, not the keyboard so if you have joysticks that act like a keyboard then of course disabling this option will not work. 
- **CPU Configuration:** Allows setting the CPU governor (default is ondemand on RetroPie on the Raspberry Pi). You can use this to set the CPU governor - ie to "performance", which will be set on launching a game, and reset after. More information regarding CPU governors can be found in the Linux Kernel documentation - https://www.kernel.org/doc/Documentation/cpu-freq/governors.txt