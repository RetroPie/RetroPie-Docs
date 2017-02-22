This tutorial is intended for those who wish to add a new system in EmulationStation. For example if you are looking to create a system for favourite games across different platforms or a separate system for roms hacks. 

If you are looking to create a favourites lists **within** a system, then you may wish to consider the [child-friendly version of EmulationStation](https://github.com/retropie/retropie-setup/wiki/Child-friendly-EmulationStation#favorites****) which has this feature.

Before you begin, it is recommended that you back up your image, at least making a copy of the `/opt/retropie/configs` folder.

###Step 1. Edit es_systems.cfg

Each system in EmulationStation is defined in the file `es_system.cfg`. The default version resides in the `/etc/emulationstation` folder. It is recommended that you make a copy of this file into the `/opt/retropie/configs/all/emulationstation` folder. The default version will be overwritten whenever you make updates to your RetroPie system so any manual changes such as a new system will be lost. Remember if you do make any updates to RetroPie then you should add any updates to `/etc/emulationstationes_systems.cfg` to the custom version in the `/opt/retropie/configs/all/emulationstation` folder.

You can create a custom copy with the following command:

	sudo cp /etc/emulationstation/es_systems.cfg /opt/retropie/configs/all/emulationstation/es_systems.cfg.

To appreciate how this process works, it is worth becoming familiar with the contents of the `es_systems.cfg` file. Each system will have an entry like the example for NES below.

    <system>
        <name>nes</name>
        <fullname>Nintendo Entertainment System</fullname>
        <path>/home/pi/RetroPie/roms/nes</path>
        <extension>.nes .zip .NES .ZIP</extension>
        <command>/opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ nes %ROM%</command>
        <platform>nes</platform>
        <theme>nes</theme>
    </system>


To add a new system to EmulationStation, you will need to create a new entry beginning with a `<system>` tag and ending with a `</system>` tag in `/opt/retropie/configs/all/emulationstation/es_systems.cfg`. Before you make any changes, you should exit EmulationStation first by pressing F4 on a keyboard or using the Quit EmulationStation option in the start menu.

The simplest way of adding a new system in your custom `es_systems.cfg` file is to open it in a text editor, copy an existing system and replace the contents of each tag.

**<name>**

This is the short name used by ES internally as well as the text used in the EmulationStation UI unless replaced by an image or logo in the theme. It is advised to choose something short and descriptive, e.g. favourites, hacks. 

**<fullname>**

This is the long name used in menus. This tag is optional so it may be best to omit it unless you are not using a theme for the new section.

**<path>**

This is the folder where the roms in your new system will be located. This folder, e.g. `/home/pi/RetroPie/roms/favorites`, may need to be created if it does not already exist. Multiple paths are not currently permitted.

**<extension> and <command>**

These define the list of extensions that EmulationStation will look for in the rom folder defined in `<path>` and the shell command executed when a game is selected. 

Roms can be launched using shell scripts or the runcommand script. Both methods are involved so it is your choice how you wish to proceed. The entries for these tags are covered [below](https://github.com/RetroPie/RetroPie-Setup/wiki/Add-a-New-System-in-EmulationStation#step-31-launch-roms-with-the-runcommand-script) so check the steps required if you are unsure which is best for you.

**<platform>**

This information is used for scraping. This tag is optional so it may be best to  omit it. If you intend to use multiple emulators, for a favourites section for instance, then you can use existing gamelists to manually create a new gamelist. If you are creating a section for mods or hacks, then it's unlikely you'll be able scrape metadata.

**<theme>**

This is the theme EmulationStation loads from the current theme set. You can use an existing theme, e.g. `<theme>nes</theme>`, or you can create a new one. If you do the latter, then it may an idea to make it the same as the `<name>` tag.

Here is an example entry for a section for rom hacks in a custom `es_systems.cfg` file that will run on a number of emulators, Atari 2600, NES, Megadrive, and SNES.

```
<system>
	<name>hacks</name>
	<path>~/RetroPie/roms/hacks</path>
	<extension>.bin .gen .int .nes .rom .smc .BIN .GEN .INT .NES .ROM .SMC</extension>
	<command>/opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ hacks %ROM%</command>
	<theme>hacks</theme>
</system> 
```
Once you have completed your entry for the new system, then save your custom `es_system.cfg` file and place your roms in the folder specified in the `<path>` tag.

**Tip** If you are creating a favourites section where you have roms in two folders, then, to save space, you can use symbolic links. For example, if you wish to have Contra available in the NES system and a new Favorites section, then you can create a symbolic link with the command:

	ln -s /home/pi/RetroPie/roms/nes/Contra.nes /home/pi/RetroPie/roms/favorites/Contra.nes

Contra will now appear in the favorites section and launch as normal once you've completed tutorial.

When you restart EmulationStation, the new system will be added together with your roms. (See below for [troubleshooting](https://github.com/RetroPie/RetroPie-Setup/wiki/Add-a-New-System-in-EmulationStation#troubleshooting))

###Step 2. Create a Theme for the New System

If you are not using an existing theme for your system and have not created a theme for your new system, then once you have restarted EmulationStation, the new system will appear like this.

![ES System View Unthemed](https://cloud.githubusercontent.com/assets/8166945/22026883/f5106b3c-dcc9-11e6-8d89-e1d5dc323fc5.png)

If your system appears as above, then a theme needs to be defined for the new system. It is recommended that you copy your current theme from `/etc/emulationstation/themes` to the `/opt/retropie/configs/all/emulationstation/themes` folder for the similar reasons why the `es_systems.cfg` file was copied. It's a good idea to rename the copied folder, e.g. `carbon-custom`, so that the default and customised themes can be differentiated in the EmulationStation UI.

In the hacks example above, EmulationStation looks for a theme in the `hacks` folder of the current theme as defined in the `<theme>` tag in your custom `es_systems.cfg` file. The simplest way to do this is to copy an existing folder in the themes folder and rename it to `hacks`. You can then add or replace images or logos to the `art` folder and edit the `theme.xml` file to incorporate them.

Here is the Hacks system using the Carbon theme where only a new vector logo has been added.

![ES System View Unthemed](https://cloud.githubusercontent.com/assets/8166945/22027062/825e06fc-dcca-11e6-8e7e-8479517dcdae.png)

You can find more information on creating themes and images or logos at the following links:

[Creating Your Own Emulation Theme](https://github.com/retropie/retropie-setup/wiki/Creating-Your-Own-EmulationStation-Theme)

[Video Tutorial on creating Vector (svg) logos from Bitmaps (png)](https://www.youtube.com/watch?v=q9Fk6OzX86U)

###Step 3.1. Launch roms with the Runcommand script
*This is recommended for console games, especially those that use libretro emulators such as those for NES, SNES, Megadrive/Genesis.*

For the `<command>` tag in your custom `es_systems.cfg` file, the simplest thing to do is change the line in an existing system, for example `nes`, to the new one, e.g. `hacks`, as below:

    <command>/opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ hacks %ROM%</command>

The `<command>` tag tells the runcommand script to look for a `emulators.cfg` file in the `hacks` folder in  `/opt/retropie/configs` for launch commands. The `hacks` folder does not exist by default so will need to be created as well as the `emulators.cfg` file in that folder. The simplest way to do this is to copy an existing folder in `/opt/retropie/configs/` and rename it.

For example, to launch the NES rom hack [Mario Adventure](http://www.romhacking.net/hacks/70), make a copy of the `nes` folder in `/opt/retropie/configs` and rename it `hacks`. The folder will already include an `emulators.cfg` file with appropriate commands to launch NES roms.

In your custom `es_systems.cfg` file, the `<extension>` tag should read:

		<extension>.nes .NES</extension>

Update your custom `es_systems.cfg` file and restart EmulationStation. It will now be possible to launch Mario Adventure from your newly created Hacks system in EmulationStation.

Say that you now want to add the SNES rom hack [Super Metroid: Redesign](http://www.romhacking.net/hacks/131/) to your hacks section. Open `/opt/retropie/configs/snes/emulators.cfg` and copy the line for the emulator you wish to use, eg lr-snes9x2010, into the `emulators.cfg` file in the `hacks` folder. This file will now read as follows:

	lr-fceumm = "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-fceumm/fceumm_libretro.so --config /opt/retropie/configs/nes/retroarch.cfg %ROM%"
	default = "lr-fceumm"
	lr-snes9x2010 = "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-snes9x2010/snes9x2010_libretro.so --config /opt/retropie/configs/snes/retroarch.cfg %ROM%"

Add .smc and .SMC (or any relevant extensions) to the `<extension>` tag in your custom `es_systems.cfg file `and restart EmulationStation.

To launch Super Metroid: Redesign from EmulationStation, you will need to bring up the [runcommand menu](https://github.com/retropie/retropie-setup/wiki/runcommand) by pressing any key on a keyboard or button 0 on your controller before the game begins. In the menu, choose the lr-snes9x2010 as the emulator for your rom and then launch.

This process can be repeated for more systems by adding launch commands to `emulators.cfg` and using the runcommand menu to select the appropriate emulator for each rom. Make sure to add the extensions for your roms to the `<extension>` entry in your custom `es_systems.cfg` file.

**Tip:** Before you begin editing files, it may be an idea to make a list of emulators you wish to use, find their launch commands and then add them to the `emulators.cfg` file in one go. You can do similar for the accepted extensions.

###Step 3.2. Launch roms with the shell scripts
*This is recommended for games that already launch from shell scripts such as ports.*

If you wish to launch your games using shell scripts, then the `<extension>` and `<command>` entries in your custom `es_systems.cfg` file can read:

	<extension>.sh .SH</extension>
	<command>%ROM%</command>


For each game, a shell script will need to be created in the roms folder as defined in the `<path>` tag  in in your custom `es_systems.cfg` file. 

Using the example from the [Doom Mods](https://github.com/retropie/retropie-setup/wiki/Doom#to-launch-doom-mods-pwads) page, the shell script to launch the Batman Doom mod in pr-boom would be:

	#!/bin/bash
	/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/doom/batman/doom2.wad" "lr-prboom"

Note: please check the link above as there is more to do to get Batman Doom running than creating a shell script.

You can ensure the script is executable by running the command:

	sudo chmod +x "~/RetroPie/roms/hacks/Batman Doom.sh"

You can create individual shell scripts for each game in your new system. When you restart EmulationStation, the scripts should appear in your new system.

**Tip:** If you're not sure what the launch command for a system is, then check the `emulators.cfg` file for that system and copy the launch command replacing `%ROM%` with the full path and name of the rom.

###Troubleshooting

* After making changes to your custom `es_systems.cfg` file, if EmulationStation fails to load or your system does not appear then check the EmulationStation log at `/opt/retropie/configs/all/emulationstation/es_log.txt` for any errors. 

* You can use an [online XML validator](https://www.xmlvalidation.com/) to check for errors in your custom `es_systems.cfg` file though this won't pick up on errors such as incorrect rom paths.

* After restarting EmulationStation, if your new system does not include the roms you were expecting, then check that the extensions are included in the `<extension>` tag in your custom `es_systems.cfg` file. Remember Linux is case-sensitve.

* If a rom doesn't run, then check the runcommand log at `/dev/shm/runcommand.log` for errors. 