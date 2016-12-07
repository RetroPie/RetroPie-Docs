# runcommand

The runcommand is the script responsible to launch your emulators/games. This wiki shows the runcommand's configurations and features.

- [Runcommand Launch Menu](#runcommand-launch-menu)
- [Adding custom launching images](#adding-custom-launching-images)
- [runcommand-onstart and runcommand-onend scripts](#runcommand-onstart-and-runcommand-onend-scripts)


## Runcommand Launch Menu

Each time you load a ROM there is an option to open what is called the Runcommand Launch Menu. This is accessed by pressing any key on the keyboard or js0 (button 0 on your first connected joypad - it will vary depending on the gamepad used)


![runcommandlaunch](https://cloud.githubusercontent.com/assets/10035308/12870184/99acb464-ccf6-11e5-9f32-7f2ef3c17b3a.png)


Once you press js0 or a button on your keyboard, it will open up into this menu (this menu may vary depending on the emulator you are running and version of retropie you are using- this image is for the super nintendo):

![runcommandmenu](https://cloud.githubusercontent.com/assets/10035308/10265893/b65c94ee-69ff-11e5-9195-f6a996f4b35b.png)

If you select the first option, if there is more than one emulator, you can swap which emulator is used:

![defaultemulator](https://cloud.githubusercontent.com/assets/10035308/10265899/de7127ec-69ff-11e5-99b6-aa2df9247da6.png)

There are also varying options to change video settings, RetroArch configs for that system, etc. 

In the past there were multiple rom folders for each emulator but they got confusing so now there is only one rom folder for each system and the emulator used can be loaded dynamically so there is no longer a need for multiple rom folders for each system. 

### Configuring Runcommand:

You can enable and disable different functions of the Runcommand Launch Menu. This is configured via RetroPie-Setup or via the runcommand configuration option in the RetroPie area of Emulation Station. 

![runcommand](https://cloud.githubusercontent.com/assets/10035308/12870161/2608ac8a-ccf5-11e5-8d78-97cf5650cee4.png)

- **Launch Menu:** Enable or disable the runcommand launch menu
- **Launch Menu Art:** If enabled, any scraped box art you have for a game with show up as a splashscreen while your game loads up.
- **Launch Menu Joystick Control:** You can disable the joystick support so that your kids don't accidentally mess up settings. Note that this only disables the joystick, not the keyboard so if you have joysticks that act like a keyboard then of course disabling this option will not work. 
- **CPU Configuration:** Allows setting the CPU governor (default is ondemand on RetroPie on the Raspberry Pi). You can use this to set the CPU governor - ie to "performance", which will be set on launching a game, and reset after. More information regarding CPU governors can be found in the Linux Kernel documentation - https://www.kernel.org/doc/Documentation/cpu-freq/governors.txt


## Adding custom launching images

Since 4.0.3 the runcommand can show a custom "launching" image instead of the traditional dialog infobox. The custom launching images must be placed at `/opt/retropie/configs/SYSTEM_NAME/` and named as "launching.jpg" or "launching.png". But be aware that if "Launch Menu Art" is enabled, the scaped box art image takes precedence.

Example: if you have a cool NES related image and want to show it right before launching a NES game, you have to name the image file as `/opt/retropie/configs/nes/launching.jpg`.

A more general launching image (not related to a specific system) can be named as `/opt/retropie/configs/all/launching.jpg`.

You can get some cool launching images in these forum topics:
- https://retropie.org.uk/forum/topic/36/splashscreens/97
- https://retropie.org.uk/forum/topic/4611/runcommand-system-splashscreens

## runcommand-onstart and runcommand-onend scripts

Since 4.0.2 the runcommand can execute a user script before the game launching (`runcommand-onstart.sh`) and after exiting the emulator (`runcommand-onend.sh`). Both scripts must be placed at `/opt/retropie/configs/all/`.

Useful data are passed as arguments to these scripts:

- `$1` - the system (eg: atari2600, nes, snes, megadrive, fba, etc).
- `$2` - the emulator (eg: lr-stella, lr-fceumm, lr-picodrive, pifba, etc).
- `$3` - the full path to the rom file.
- `$4` - the full command line used to launch the emulator.

All the error messages from these scripts will be logged in `runcommand.log`. If you want to log something to this file you have to redirect the output to the standard error. This way:

```sh
echo "message to log" >&2
```

Some examples of what can be done with these scripts:

- In the [Take and Scrape Your Own Screenshots wiki](https://github.com/RetroPie/RetroPie-Setup/wiki/Take-and-Scrape-Your-Own-Screenshots) there are two methods to achieve the same goal. In method 1 the `runcommand-onstart.sh` is used to automatically set some configurations in the system specific retroarch.cfg file. In method 2 the `runcommand-onend.sh` is used to check if you have a screenshot for the game you are leaving, and if yes, it will make the most recent screenshot be the emulationstation image for this game.
- In [RetroPie-joystick-selection tool](https://github.com/meleu/RetroPie-joystick-selection) the joystick selection by name method uses the `runcommand-onstart.sh` to get the joystick name, look for its index and set the index in the proper retroarch.cfg file.
