## Introduction

[EmulationStation](http://emulationstation.org/) is the official graphical frontend of the RetroPie project. 

| ![firstboot](https://cloud.githubusercontent.com/assets/10035308/16217874/c6bbdb3a-3734-11e6-998f-8cc714a320ce.png)|
| :---: | 

EmulationStation is not an emulator, rather it is a polished game launcher that includes:

- Controller and keyboard support
- Custom themes
- Scraper for box art and game metadata

### Configuration Files

There are different configuration files for the different aspects of EmulationStation:

#### es_systems.cfg

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

#### Scraper (gamelist.xml)

There are two scrapers for RetroPie: the built in EmulationStation scraper and Sselphs scraper. More information [HERE](Scraper)

The gamelist.xml file for a system defines metadata for a system's games, such as a name, image (like a screenshot or box art), description, release date, and rating.

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

#### Themes

The RetroPie community has developed many themes for ES. See Themes page [HERE](themes)

ES will check two places for a theme in the following order, using the first one it finds:

- `~/.emulationstation/themes`
- `/etc/emulationstation/themes`

Themes installed from the RetroPie-Setup script will be installed in `/etc/emulationstation/themes`

See more information [HERE](https://github.com/Aloshi/EmulationStation#themes)

See here for a tutorial on [Creating Your Own EmulationStation Theme](Creating-Your-Own-EmulationStation-Theme)

#### Command Line Arguments

EmulationStation has a few command line arguments that could be helpful to you for various customisation.  Let's say you wanted to setup a kiosk but did not want to give access to the builtin scraper function or you didn't want the end user to be able to exit EmulationStation, you can simply edit `/opt/retropie/configs/all/autostart.sh` and append the corresponding command line argument.

For example, to disable the Exit option from inside the Quit menu, edit `/opt/retropie/configs/all/autostart.sh` with
```
emulationstation --no-exit #auto
```

To see a complete list of the supported command line arguments
```
emulationstation --help
```

### Editing ES Configs

ES uses xml files for its database and caches them on loading and exit, so any edits to the configuration files will need to be changed when ES is closed.

Because of the way the RetroPie-Setup script works custom configurations will need to be copied and edited in specific places.

Note that any configs in `~/.emulationstation/` are symlinked to `/opt/retropie/configs/all/emulationstation/` which means both paths will work.

#### Editing es_systems.cfg (Systems)

Custom es_systems.cfg should be in `~/.emulationstation/es_systems.cfg`

copy `es_systems.cfg` from `/etc/emulationstation` to `~/.emulationstation`

```
cp /etc/emulationstation/es_systems.cfg ~/.emulationstation/es_systems.cfg
```

Note that anytime you add a new system from the RetroPie-Setup Script you will need to manually copy over the new system to the new location in order to keep parity.

#### Editing Themes

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

#### Editing es_input.cfg (Controller Input)

EmulationStation controller configurations are found in `~/.emulationstation/es_input.cfg`

RetroPie uses custom generation scripts that will generate controller configurations for many emulators through the initial ES controller configuration, so if you remove or make any edits to this configuration you need to regenerate that hook 

```
Retropie Setup Script >> Manage Packages >> Manage Core Packages >> EmulationStation >> Configuration / Options >> Clear / Reset EmulationStation Input Configuration 
```

#### Editing gamelist.xml (Scraped data)

If you use the built in ES Scraper your gamelist.xml and images folder will be in 

- `~/.emulationstation/gamelists/[SYSTEM_NAME]/gamelist.xml`

If you use Sselph's Scraper you can choose whether your scraped data goes in 

- `[SYSTEM_PATH]/gamelist.xml` (the rom folder) or
- `~/.emulationstation/gamelists/[SYSTEM_NAME]/gamelist.xml`

## Development Status

ES was originally developed by Aloshi (code) and Nils Bonenberger (UI) but they have since moved on to other projects. There is no longer any maintained upstream project so any modifications done to ES are on uofficial/partially maintained forks of the project. 

RetroPie's fork of EmulationStation has made some improvements like video support, faster load times, and controller integration among others.  


### Experimental ES Forks

There are a few experimental forks of ES that are worth checking out if you enjoy customising your system USE AT YOUR OWN RISK!

#### Child Friendly 

A RetroPie user known as Zigurana created a child friendly version of ES that is great for parents looking to simplify their builds against accidental modifications from their young ones. It is also great for when friends come by or if your build is in a public place.

It can be installed from the experimental menu of the setup script

More information [HERE](Child-friendly-EmulationStation)

#### Grid View 

A RetroPie user known as Jacobfk20 created a fork of ES that incorporates a grid view, it also includes wifi integration, an on screen keyboard, and some system diagnostics.

a basic install module can be found [HERE](https://gist.github.com/PokeEngineer/e319fbe347f2da23239e2eefbe93c5a8)

More discussion on the forum [HERE](https://retropie.org.uk/forum/topic/3121/emulationstation-mod)

### Alternative Frontends

Because of the development hiatus, there has been some attention towards other front-ends. The following alternate frontends can be installed from experimental packages of the RetroPie Setup-Script but support is currently only preliminary.

-  Attract-Mode ([site](http://attractmode.org/)) 
-  mehstation ([site](https://remy.io/mehstation))
