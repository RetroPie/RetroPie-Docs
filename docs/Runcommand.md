# runcommand

The runcommand is the script responsible to launch your emulators/games. This wiki shows the runcommand's configurations and features.

- [Runcommand Launch Menu](#runcommand-launch-menu)
- [Adding custom launching images](#adding-custom-launching-images)
- [runcommand-onstart and runcommand-onend scripts](#runcommand-onstart-and-runcommand-onend-scripts)
- [runcommand-menu custom scripts](#runcommand-menu-custom-scripts)

## Runcommand Launch Menu

Each time you load a ROM there is an option to open what is called the Runcommand Launch Menu. This is accessed by pressing any button on a controller (the bottom face button is recommended as to not accidentally change anything) or pressing any key on a keyboard, while the prompt in the image below is displayed or right after a launching image disappears if you have those setup.

![runcommandlaunch](https://cloud.githubusercontent.com/assets/10035308/12870184/99acb464-ccf6-11e5-9f32-7f2ef3c17b3a.png)

Once you press any button on a gamepad or any key on a keyboard, it will open up into this menu (the menu options will vary depending on the system you are running and version of RetroPie you are using:

![runcommandmenu](https://cloud.githubusercontent.com/assets/10035308/10265893/b65c94ee-69ff-11e5-9195-f6a996f4b35b.png)

If you select the first option, you can swap which emulator is used if there is more than one emulator:

![defaultemulator](https://cloud.githubusercontent.com/assets/10035308/10265899/de7127ec-69ff-11e5-99b6-aa2df9247da6.png)

There are also varying options to change video settings, RetroArch configs for that system, etc. 

### Configuring Runcommand:

You can enable and disable different functions of the Runcommand Launch Menu. This is configured via RetroPie-Setup or via the runcommand configuration option in the RetroPie area of Emulation Station. 

![runcommand_config](https://retropie.org.uk/forum/assets/uploads/files/1490801740403-runcommand_config-resized.png)

- **Launch Menu:** Enable or disable the runcommand launch menu
- **Launch Menu Art:** If enabled, any scraped box art you have for a game will show up as a splashscreen while your game loads up.
- **Launch Menu Joystick Control:** You can disable the joystick support so that your kids don't accidentally mess up settings. Note that this only disables the joystick, not the keyboard so if you have joysticks that act like a keyboard then of course disabling this option will not work.
- **Launch image delay in seconds:** Set how many seconds the [launching image](#adding-custom-launching-images) will be displayed before start the game.
- **CPU Configuration:** Allows setting the CPU governor (default is ondemand on RetroPie on the Raspberry Pi). You can use this to set the CPU governor - ie to "performance", which will be set on launching a game, and reset after. More information regarding CPU governors can be found in the Linux Kernel documentation - https://www.kernel.org/doc/Documentation/cpu-freq/governors.txt


## Adding custom launching images

Runcommand can show a custom "launching" image instead of the traditional dialog infobox. The images must be placed at `/opt/retropie/configs/SYSTEM_NAME/` and named as `launching.png` (or `.jpg`). But be aware that if "Launch Menu Art" is enabled, the scraped box art image takes precedence.

**Example:** if you have a cool NES related image and want to show it right before launching a NES game, you have to name the image file as `/opt/retropie/configs/nes/launching.jpg`.

A more general launching image (not related to a specific system) can be named as `/opt/retropie/configs/all/launching.jpg`.

You can also automatically generate launching images based on emulationstation themes you have installed. To install the tool that generates the images go to RetroPie-Setup and choose

**"Manage packages" >> "Manage experimental packages" >> "launchingimages" >> "Install from binary"**

After installing you can use the tool going to RetroPie-Setup main menu and choose **Configuration / tools >> launchingimages** and then follow the instructions on screen. [Here is a nice video tutorial about this tool](https://www.youtube.com/watch?v=3wc4daHBLNE).

The launching images can also be used in a per game basis. The image must be placed at `$HOME/RetroPie/roms/SYSTEM_NAME/images/` and named as `RomName-launching.png` (or `.jpg`), where `RomName` must be the exact name of the ROM minus the trailing extension.

**Example:** if you have a launching image for the "Mega Man" NES game and the ROM is named `Mega Man (USA).nes`, you have to name the image file as `RetroPie/roms/nes/images/Mega Man (USA)-launching.png`.

**Once these images are installed, the timing to activate the runcommand menu differs, in that pressing a button will not register successfully until just after the image has disappeared.**

You can get some cool launching images in these forum topics:

- https://retropie.org.uk/forum/topic/7193/runcommand-launching-images-for-any-theme
- https://retropie.org.uk/forum/topic/4611/runcommand-system-splashscreens
- https://retropie.org.uk/forum/topic/36/splashscreens/97
- https://retropie.org.uk/forum/topic/13580/arcade-games-launching-images-collection

## runcommand-onstart and runcommand-onend scripts

Runcommand can execute an user script before the game launching (`runcommand-onstart.sh`) and after exiting the emulator (`runcommand-onend.sh`). Both scripts must be placed at `/opt/retropie/configs/all/`.

Useful data are passed as arguments to these scripts:

- `$1` - the system (eg: atari2600, nes, snes, megadrive, fba, etc).
- `$2` - the emulator (eg: lr-stella, lr-fceumm, lr-picodrive, pifba, etc).
- `$3` - the full path to the rom file.
- `$4` - the full command line used to launch the emulator.

All the error messages from these scripts will be logged in `/dev/shm/runcommand.log`. If you want to log something to this file you have to redirect the output to the standard error. This way:

```sh
echo "message to log" >&2
```

Some examples of what can be done with these scripts:

- In the [Take and Scrape Your Own Screenshots wiki](Take-and-Scrape-Your-Own-Screenshots) there are two methods to achieve the same goal. In method 1 the `runcommand-onstart.sh` is used to automatically set some configurations in the system specific retroarch.cfg file. In method 2 the `runcommand-onend.sh` is used to check if you have a screenshot for the game you are leaving, and if yes, it will make the most recent screenshot be the emulationstation image for this game.
- In [RetroPie-joystick-selection tool](https://github.com/meleu/RetroPie-joystick-selection) the joystick selection by name method uses the `runcommand-onstart.sh` to get the joystick name, look for its index and set the index in the proper retroarch.cfg file.


## runcommand-menu custom scripts

Since version 4.2.8 runcommand menu creates an option named **User Menu** where is possible to choose a custom script to launch. The custom scripts must be placed at `/opt/retropie/configs/all/runcommand-menu` and file name must end with `.sh`.

Useful data are passed as arguments to the custom scripts in the same way they are passed for [runcommand-onstart/onend scripts](#runcommand-onstart-and-runcommand-onend-scripts).

What happens after the end of a custom script execution depends on the exit status:

- exit status 0, returns to user menu (script list).
- exit status 1, exits runcommand without launching the game.
- exit status 2, launch the game.
- any other exit status, returns to user menu (script list).