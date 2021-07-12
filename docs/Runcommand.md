# runcommand

The runcommand is the script responsible to launch your emulators/games. This page shows the runcommand's configurations and features.

## Runcommand Launch Menu

Each time you load a ROM there is an option to open what is called the Runcommand Launch Menu. This is accessed by pressing any button on a controller (the bottom face button is recommended as to not accidentally change anything) or pressing any key on a keyboard, while the prompt in the image below is displayed or right after a launching image disappears, if you have those set up.

<img src="https://user-images.githubusercontent.com/31816814/85049757-ccab9480-b19d-11ea-984e-27941838440e.png" width="80%" title="Runcommand launch dialog">

Once you press any button on a controller or any key on a keyboard, it will open up into this menu. The menu options will vary depending on the system you are running and version of RetroPie you are using:

<img src="https://user-images.githubusercontent.com/31816814/85049707-c1586900-b19d-11ea-98a9-35752f39108d.png" width="80%" title="Runcommand launch menu">

The first two options control which emulator is used for the current system or ROM, if there is more than one emulator available:

<img src="https://user-images.githubusercontent.com/31816814/85049729-c7e6e080-b19d-11ea-88ec-74d32981239d.png" width="80%" title="Choosing an Emulator">

This preference is saved in `/opt/retropie/configs/all/emulators.cfg`

The second two options select video modes for the current system or ROM. This preference is saved in `/opt/retropie/configs/all/videomodes.cfg`.

### Configuring Runcommand

You can enable and disable different functions of the Runcommand Launch Menu. This is configured via RetroPie-Setup or via the runcommand configuration option in the RetroPie area of Emulation Station. 

<img title="Runcommand configuration options" src="https://user-images.githubusercontent.com/31816814/85050776-43955d00-b19f-11ea-98a1-279faded0f3d.png" width="80%">


- **Launch Menu:** Enable or disable the runcommand launch menu
- **Launch Menu Art:** If enabled, any scraped box art you have for a game will show up as a splashscreen while your game loads up.
- **Launch Menu Joystick Control:** You can disable the joystick support so that your kids don't accidentally mess up settings. Note that this only disables the joystick, not the keyboard so if you have joysticks that act like a keyboard then of course disabling this option will not work.
- **Launch image delay in seconds:** Set how many seconds the [launching image](#adding-custom-launching-images) will be displayed before start the game.
- **CPU Configuration:** Allows setting the CPU governor (default is ondemand on RetroPie on the Raspberry Pi). You can use this to set the CPU governor - ie to "performance", which will be set on launching a game, and reset after. More information regarding CPU governors can be found in the Linux Kernel documentation - https://www.kernel.org/doc/Documentation/cpu-freq/governors.txt

These options are saved in `/opt/retropie/configs/all/runcommand.cfg`

### Launch with verbose logging

When launching Libretro cores (those prefixed by **lr-**) the Runcommand launch menu presents the option to **Launch with verbose logging**. This outputs more information to the log file found in `/dev/shm/runcommand.log` which is useful, and often necessary, when diagnosing problems. Once the game is exited, the log file can be downloaded via [SFTP](Transferring-Roms#sftp) or viewed directly via the command line.

**Note:** If launching a non-Libretro ("standalone") core, the option will not be available, but they typically will still write useful diagnostic information to `/dev/shm/runcommand.log`.

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

- <https://retropie.org.uk/forum/topic/7193/runcommand-launching-images-for-any-theme>
- <https://retropie.org.uk/forum/topic/4611/runcommand-system-splashscreens>
- <https://retropie.org.uk/forum/topic/36/splashscreens/97>
- <https://retropie.org.uk/forum/topic/13580/arcade-games-launching-images-collection>

## <a name='runcommand-onstart-and-runcommand-onend-scripts'></a>Runcommand scripts

Runcommand can execute an user script before the game launching (`runcommand-onstart.sh` and `runcommand-onlaunch.sh`) and after exiting the emulator (`runcommand-onend.sh`). Scripts must be placed at `/opt/retropie/configs/all/`.

The startup scripts are run as follows:

 - `runcommand-onstart.sh` is executed before any runcommand actions are performed and before the launch menu is displayed.
 - `runcommand-onlaunch.sh` is executed after any runnncomand actions and right before the emulator/game is started.

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