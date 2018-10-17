## Introduction

EmulationStation is the official graphical frontend of the RetroPie project. 

| ![firstboot](https://cloud.githubusercontent.com/assets/10035308/16217874/c6bbdb3a-3734-11e6-998f-8cc714a320ce.png)|
| :---: | 

EmulationStation is not an emulator, rather it is a polished game launcher that includes:

- Controller and keyboard support
- Custom themes
- Scraper for box art and game metadata

ES was originally developed by Aloshi (code) and Nils Bonenberger (UI) but, since they have moved on to other projects, the RetroPie project keeps [its own fork](https://github.com/RetroPie/EmulationStation/). That fork has made some improvements like [video support](../Scraper#scraping-videos), faster load times, favorites, and controller integration among others. Any reference for versions in this doc is related to the [RetroPie's fork](https://github.com/RetroPie/EmulationStation/).


## Enabling Favorites, All Games, and Last Played systems

Since ES version 2.4.0 you can create a list of your favorite games. You can also have a list of all games, and your last played games. These lists are all optional and in the example below we'll see how to enable them.

**Note: In order to use this feature, the theme you're using MUST support it**.

1. press `Start` to access the ES main menu and then select "**GAME COLLECTIONS SETTINGS**".

| ![es-main-menu](https://user-images.githubusercontent.com/8508804/31517232-a9998532-af71-11e7-83bf-85973b96a1f8.png) |
| :---: |

2. Next, select the first option: "**AUTOMATIC GAME COLLECTIONS**".

| ![es-game-collection-settings](https://user-images.githubusercontent.com/8508804/31517231-a967c09c-af71-11e7-8a22-f8aba2a84073.png) |
| :---: |

3. And then mark those you want to enable.

| ![es-select-collections](https://user-images.githubusercontent.com/8508804/31517233-a9c60cce-af71-11e7-84be-8d67bef4004d.png) |
| :---: |

4. After marking those you want, go back to the default ES user interface. Note that now you have more systems, like in the example below:

| ![es-favorites-lastplayed](https://user-images.githubusercontent.com/8508804/31517230-a9422364-af71-11e7-9157-5943dbd45bb7.png) |
| :---: |

### Adding games to Favorites

It's pretty simple: just move to the game you want to add and press the button you set to be `Y`. Pressing `Y` when the cursor is on a game already present in the Favorites, removes it from the list.


## Custom collections

Since ES version 2.6.0 you can create a custom list of games. You can group games by any category you want. Examples: shoot'em ups, beat'em ups, Street Fighter, RPGs, Batman, TMNT, Mega Man or any other category you can think.

If the name of the collection you're creating matches an unused theme folder, it will be shown in the main carousel as a new system entry. If there's no matching theme folder for the name you selected, it will be grouped under a new "Collections" carousel system entry.

In the example below we'll create a custom collection to group Mega Man games. **Note: You can either choose to create a collection based on an unused theme folder, or if creating from scratch you'll need a keyboard to type the name of your custom collection**.

1. press `Start` to access the ES main menu and then select "**GAME COLLECTIONS SETTINGS**".

2. Select the option "**CREATE NEW CUSTOM COLLECTION**".

| ![es-create-new-custom-collection](https://user-images.githubusercontent.com/8508804/31518386-7443b3ea-af75-11e7-9873-fc9339ab6a1f.png) |
| :---: |

3. An input box will be shown. Type the name of your custom collection.

| ![es-new-collection-name](https://user-images.githubusercontent.com/8508804/31518302-2ab0ec2a-af75-11e7-917b-557a28a1f87f.png) |
| :---: |

4. After typing the name and pressing OK, you're now in a mode where the button you set to be `Y` adds a game to the collection. Look the message on top of the image below. (**Note: while in this mode you can't add games to your favorites**).

| ![es-editing-custom-collection](https://user-images.githubusercontent.com/8508804/31518300-2a6180ae-af75-11e7-9919-baec90244166.png) |
| :---: |

5. Move the cursor to the game you want to add to your collection and press `Y`, just like you do to add/remove a game to Favorites. After adding a game you'll see a message on the top of screen, like in the image below.

| ![es-added-to-custom-collection](https://user-images.githubusercontent.com/8508804/31518291-29af22ce-af75-11e7-8b02-947eb1765e09.png) |
| :---: |

6. After adding the games you want in your collection, you can finish editing the collection by either:
a) going to any game list, pressing `Select` and selecting "**FINISH EDITING 'YOUR CUSTOM' COLLECTION**", or
b) going to "**GAME COLLECTIONS SETTINGS**" menu and then select "**FINISH EDITING 'YOUR CUSTOM' COLLECTION**".

| ![es-finish-editing-custom-collection](https://user-images.githubusercontent.com/8508804/31546747-fdde5b20-affa-11e7-86ae-970427d84a2c.png) |
| :---: |


7. Now go to the "collections system" and you'll see your custom collection.

| ![es-collections](https://user-images.githubusercontent.com/8508804/31518292-29d7d5e8-af75-11e7-9c0a-857f7a2acf07.png) |
| :---: |

| ![es-collections2](https://user-images.githubusercontent.com/8508804/31518296-2a03acf4-af75-11e7-9b15-342a8c6845f9.png) |
| :---: |

| ![es-megaman-custom-collection](https://user-images.githubusercontent.com/8508804/31518301-2a8557b8-af75-11e7-87b0-b363ced3d0c2.png) |
| :---: |

8. Once you "**FINISH EDITING 'YOUR CUSTOM' COLLECTION**", the `Y` button recover the behavior of adding/removing games to the favorites list. If you want to put ES on "editing custom collection mode" again, go the custom collection game list, press `Select` and then choose "**ADD/REMOVE GAMES TO THIS GAME COLLECTION**".

| ![es-addremove-games-to-collection](https://user-images.githubusercontent.com/8508804/31560129-8264bcc6-b029-11e7-949a-b6eec79a98fa.png) |
| :---: |

## Editing ES Configs

ES uses xml files for its database and caches them on loading and exit, so **any edits to the configuration files will need to be changed when ES is closed.**

Because of the way the RetroPie-Setup script works custom configurations will need to be copied and edited in specific places, otherwise your custom edits would be overwritten anytime a system was updated from the RetroPie setup script.

Note that any configs in `~/.emulationstation/` are symlinked to `/opt/retropie/configs/all/emulationstation/` which means both paths will work.

## Configuration Files

There are different configuration files for the different aspects of EmulationStation:

### Systems

`es_systems.cfg` defines the systems that show up in ES. The RetroPie-Setup script will automatically generate this config file alphabetically when you install any new systems. ES will check two places for an es_systems.cfg file, in the following order, stopping after it finds one that works:

- `~/.emulationstation/es_systems.cfg`
- `/etc/emulationstation/es_systems.cfg`

Example config:

```
<?xml version="1.0"?>
<systemList>
  <system>
    <name>nes</name>
    <fullname>Nintendo Entertainment System</fullname>
    <path>/home/pi/RetroPie/roms/nes</path>
    <extension>.nes .zip .NES .ZIP</extension>
    <command>/opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ nes %ROM%</command>
    <platform>nes</platform>
    <theme>nes</theme>
  </system>
</systemList>
```

More information [HERE](https://github.com/Aloshi/EmulationStation/blob/master/README.md#writing-an-es_systemscfg)

#### es_systems.cfg edits

Custom es_systems.cfg should be in `~/.emulationstation/es_systems.cfg`

copy `es_systems.cfg` from `/etc/emulationstation` to `~/.emulationstation`

```
cp /etc/emulationstation/es_systems.cfg ~/.emulationstation/es_systems.cfg
```

Note that anytime you add a new system from the RetroPie-Setup Script you will need to manually copy over the new system to the new location in order to keep parity.

#### platforms.cfg edits

Retropie uses a file called `platforms.cfg` to generate the system configurations for `es_systems.cfg` you can create a custom platforms.cfg to override the default system for regional variants such as the Sega Genesis instead of Megadrive, Turbografx instead of PC-Engine, and the Magnavox Odyssey instead of the Videopac.

Create a `platforms.cfg` in 

```
/opt/retropie/configs/all/platforms.cfg
```

name, extensions, platform (used by es for scraping), and the theme can be overriden, see [HERE](https://github.com/RetroPie/RetroPie-Setup/blob/master/platforms.cfg) for the default platforms.cfg

The following is an example of a custom platforms.cfg

```
megadrive_theme="genesis"
megadrive_platform="genesis"

pcengine_theme="tg16"
pcengine_platform="tg16"

videopac_theme="odyssey2"
videopac_platform="odyssey2"
```

**Note that with any custom platforms.cfg you create you'll need to update all systems from the setup script to generate a new es_systems.cfg with your changes.**

### Controller Configs

After configuring your controller in ES, your controller configurations will be saved to 
```
~/.emulationstation/es_input.cfg
```

#### es_input.cfg edits

RetroPie uses custom generation scripts that will generate controller configurations for many emulators through the initial ES controller configuration, so if you remove or make any edits to this configuration you need to regenerate that hook 

Retropie Setup Script >> Manage Packages >> Manage Core Packages >> EmulationStation >> Configuration / Options >> Clear / Reset EmulationStation Input Configuration 

### Scraper

There are several scrapers available in RetroPie: the built in EmulationStation scraper, Steven Selph's `scraper` and Lars Muldjord's `Skyscraper`. More information [HERE](Scraper).

The `gamelist.xml` file for a system defines metadata for a system's games, such as a name, image (like a screenshot or box art), description, release date, and rating.

ES will check three places for a `gamelist.xml` in the following order, using the first one it finds:

- `[SYSTEM_PATH]/gamelist.xml`
- `~/.emulationstation/gamelists/[SYSTEM_NAME]/gamelist.xml`
- `/etc/emulationstation/gamelists/[SYSTEM_NAME]/gamelist.xml`

An example gamelist.xml:
```xml
<gameList>
	<game>
		<path>/home/pi/ROMs/nes/mm2.nes</path>
		<name>Mega Man 2</name>
		<desc>Mega Man 2 is a classic NES game which follows Mega Man as he murders eight robot masters in cold blood.</desc>
		<image>~/.emulationstation/downloaded_images/nes/Mega Man 2-image.png</image>
	</game>
</gameList>
```

See more information [HERE](https://github.com/Aloshi/EmulationStation#gamelistxml)

#### gamelist.xml edits

If you use the built in ES Scraper your gamelist.xml and images folder will be in 

- `~/.emulationstation/gamelists/[SYSTEM_NAME]/gamelist.xml`

If you use another scraper (Steven Sselph's `scraper` or Lars Muldjord's `Skyscraper) you can choose whether your scraped data goes in 

- `[SYSTEM_PATH]/gamelist.xml` (the rom folder) or
- `~/.emulationstation/gamelists/[SYSTEM_NAME]/gamelist.xml`

### Themes

The RetroPie community has developed many themes for ES. See Themes page [HERE](themes)

ES will check two places for a theme in the following order, using the first one it finds:

- `~/.emulationstation/themes`
- `/etc/emulationstation/themes`

Themes installed from the RetroPie-Setup script will be installed in `/etc/emulationstation/themes`

See more information [HERE](https://github.com/Aloshi/EmulationStation#themes)

See here for a tutorial on [Creating Your Own EmulationStation Theme](Creating-Your-Own-EmulationStation-Theme)

#### Theme edits

Custom themes should be in `~/.emulationstation/themes`

if you want to make custom themes or edit an existing theme:

First make a themes directory if it doesn't exist

```
mkdir ~/.emulationstation/themes
```

add your theme to the themes folder or if you are copying an existing theme to edit, we'll use carbon as an example:

```
cp -R /etc/emulationstation/themes/carbon ~/.emulationstation/themes/carbon_custom
```

### Command Line Arguments

EmulationStation has a few command line arguments that could be helpful to you for various customisation.  Let's say you wanted to setup a kiosk but did not want to give access to the builtin scraper function or you didn't want the end user to be able to exit EmulationStation, you can simply edit `/opt/retropie/configs/all/autostart.sh` and append the corresponding command line argument.

For example, to disable the Exit option from inside the Quit menu, edit `/opt/retropie/configs/all/autostart.sh` with
```
emulationstation --no-exit #auto
```

To see a complete list of the supported command line arguments
```
emulationstation --help
```

### Alternative Frontends

Because of the development hiatus, there has been some attention towards other front-ends. The following alternate frontends can be installed from experimental packages of the RetroPie Setup-Script but support is currently only preliminary.

-  Attract-Mode ([site](http://attractmode.org/)) 
-  mehstation ([site](https://remy.io/mehstation))
