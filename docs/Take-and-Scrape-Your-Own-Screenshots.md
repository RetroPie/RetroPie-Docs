# Taking your  own screenshots and creating your own gamelists

Sometimes the boxarts and other sources for scraping can be low quality and inconsistent in sizes, whereas in game screenshots are standardised to the same size. The following is a simple guide with a script that will help automate the process of taking and scraping your own screenshots.

A few disclaimers first:

- **MAKE A BACKUP AND USE AT YOUR OWN RISK!**

- You have to be comfortable with basic Linux commands and simple file editing.

- You need to have an updated version of RetroPie-Setup scripts (version 4+) ([updating instructions here](Updating-RetroPie)).

- You can only create one screenshot per game

- This only works with RetroArch emulators

- If using the methods described here, the [Runcommand's Launch Menu Art option](Runcommand#configuring-runcommand) won't show the scraped screenshot image.

### Take a Screenshot

Before talk about the "scraping your own screenshots" trick, we need to know how to take screenshots in RetroArch. If you already know how to do it, you can go to the [next section](#runcommand).

#### via RGUI

Access the RGUI using [Hotkey Combination](Controller-Configuration#hotkey) **Hotkey+X** and go to **Quick Menu** > **Take Screenshot**.

#### via Hotkeys
 
The default screenshot button is **F8** which means if you've configured your keyboard through emulationstation you have to hold the [Hotkey](Controller-Configuration#hotkey) button and then press F8. If you want to have it so that you can take a screenshot with your controller you'll change the screenshot button to a button that isn't already being used for Hotkey behaviour via [RetroArch Configuration](RetroArch-Configuration#default-joypad-hotkeys)

The line to change is:
```
# Take screenshot
# input_screenshot = f8
```
So in my case I changed it to my right analogue thumb on my xbox controller (number values vary with diff controllers)
```
# Take screenshot
input_screenshot_btn = "12"
```

This results in a new Hotkey combination of **Hotkey+Right Thumb** = **Take Screenshot**.

## runcommand

The runcommand menu is what is run every time you play a game, It is what allows you to change emulators, set video resolutions, among other things. One lesser known function is the ability to add customised scripts to be executed on the start and/or on the end of the game.

The `runcommand-onstart.sh` script is executed (if exists) before the game starts, and `runcommand-onend.sh` is executed (if exists) after you exit the emulator. Both files must be at `/opt/retropie/configs/all/` directory.

The two methods described here take advantage from these features.

## scraping methods

Here we have two methods to scrape your own screenshots:

**[Method 1](#method-1)**: uses the `runcommand-onstart.sh` to automatically set some screenshot related configs in system specifics `retroarch.cfg` files. And after you take some screenshots from the games, you use the SSelph scraper to create a `gamelist.xml` with them.

**[Method 2](#method-2)**: uses the `runcommand-onend.sh` to automatically set the most recent screenshot from a game to be the emulationstation image for the respective game.

The main difference between them is:

- [Method 1](#method-1): automates the `retroarch.cfg` configs but you have to use SSelph scraper tool from command line every time you want to update the `gamelist.xml` with your screenshots.

- [Method 2](#method-2): you have to manually edit `retroarch.cfg` configs, but automates the placement of your screenshots as the respective emulationstation game images.

Now you have to choose which one you want to follow (or read about both):

[Method 1](#method-1):

- [runcommand-onstart.sh](#runcommand-onstartsh)
- [Create gamelist with Sselphs scraper](#create-gamelist-with-sselphs-scraper)
- [Behind the Code](#behind-the-code)


[Method 2](#method-2):

- [retroarch.cfg](#retroarchcfg)
- [runcommand-onend.sh](#runcommand-onendsh)
- ["I didn't like how it looks! I want my old images back and disable this stuff!"](#i-didnt-like-how-it-looks-i-want-my-old-images-back-and-disable-this-stuff)

## METHOD 1

### runcommand-onstart.sh
You need to create a file called `runcommand-onstart.sh` in the folder `/opt/retropie/configs/all/`

copy the following contents:

```
#!/usr/bin/env bash

system="$1"
imgdir="$HOME/RetroPie/roms/$system/images"
configdir="/opt/retropie/configs" 

mainretroarch="$configdir/all/retroarch.cfg"
systemretroarch="$configdir/$system/retroarch.cfg"

source "/opt/retropie/lib/inifuncs.sh"

iniConfig " = " '"'

# Create images folder in each respective rom folder
mkdir -p "$imgdir"

# If there is no auto screenshot setting in the main retroarch.cfg add it
if ! grep -q "auto_screenshot_filename" "$mainretroarch"; then
    iniSet "auto_screenshot_filename" "false" "$mainretroarch"
fi

# If there is no system based screenshot directory defined then define it in the system based retroarch.cfg
if ! grep -q "screenshot_directory" "$systemretroarch"; then
    iniSet "screenshot_directory" "$imgdir" "$systemretroarch"
fi
```
Now you can play your games and take your screenshots and it will fill your images folder with your screenshots. 

### Create gamelist with Sselphs scraper

If you haven't already, download sselphs scraper from the setup script

Now that you've got your screenshots ready all you have to do is use sselph's scraper to generate a gamelist for your screenshots- this will effectually link your roms to their respective screenshots.

**You need to exit emulationstation first**

so again using the snes as an example

```
cd /home/pi/RetroPie/roms/snes
/opt/retropie/supplementary/scraper/scraper -img_format=png -add_not_found=true -download_images=false -image_suffix=
```
_For more information on the options for sselphs scraper see [here](https://github.com/sselph/scraper/wiki/Flags)_

it will create a gamelist.xml file in `/home/pi/RetroPie/roms/snes` which takes precedence over the gamelist.xml in `/home/pi/.emulationstation/gamelists/snes`

and if all went according to plan, when you boot emulationstation back up your images will be the screenshots that you took! TADA!

Also if you want to only add images and leave metadata out entirely you can tell it not to scrape from any databases with `-use_gdb=false -use_ovgdb=false`

### Behind the Code

The following is all taken care of by the aforementioned script but if you're interested this explains essentially what the code is doing (and how you can set it up manually without a script)

#### Overall retroarch.cfg

You need to add the following line to `/opt/retropie/configs/all/retroarch.cfg`
```
auto_screenshot_filename = "false"
```
This will tell retroarch to name any screenshots taken after the rom name you are playing

#### System Specific retroarch.cfg

You need create an `images` folder in each rom folder you want screenshots for and then set the system based retroarch.cfg screenshot path to each respective `images` folder so that the images can be easily joined with sselphs scraper,  unlike the default retropie behaviour this will keep your images and gamelists in each system folder with your roms; the pattern is as follows:

`/home/pi/RetroPie/roms/<system>/images`

so for example if I'm adding screenshots to the snes I would create:

`/home/pi/RetroPie/roms/snes/images`

Then I would add that screenshot path to:

`/opt/retropie/configs/snes/retroarch.cfg` 

```
# Settings made here will only override settings in the global retroarch.cfg if placed above the #include line

input_remapping_directory = "/opt/retropie/configs/snes/"
screenshot_directory = "/home/pi/RetroPie/roms/snes/images/"

#include "/opt/retropie/configs/all/retroarch.cfg"
```
then we would take our screenshots and use sselphs scraper to generate our gamelist.xml's as above.

## METHOD 2

### What exactly this method do

If you take a screenshot during a gaming session, the most recent screenshot will be the emulationstation image for this game. This task is done by a `runcommand-onend.sh` script.

Obviously, there are some conditions to make it happen, in order to let the user easily turn on/off this functionality.

**Limitation: This method doesn't work if the emulationstation "save metadata on exit" option is turned on, because it makes emulationstation overwrite the changes made by the `runcommand-onend.sh`.** Turn it off in the emulationstation Main Menu -> Other Settings -> Save Metadata On Exit.

### retroarch.cfg

There are two conditions related to RetroArch configuration in order to make it works: 

- `auto_screenshot_filename = "false"`
- `screenshot_directory = "/some/path/to/screenshots"`

The `auto_screenshot_filename = "false"` means that your screenshots will **NOT** be named automatically, they will always be named as `ROM file name.png`. Therefore your most recent screenshot will always overwrite the previous one.

Remember this to avoid confusion: `auto_screenshot_filename = false` means ON for this "scrape screenshots" method. If `auto_screenshot_filename` is true (or absent), it means OFF.

The directory assigned to `screenshot_directory` **MUST** exist, otherwise RetroArch won't be able to save the screenshots.

Those options can be set in global or system specific `retroarch.cfg`.

#### global config (easy way)

Edit your `/opt/retropie/configs/all/retroarch.cfg` and put the option `auto_screenshot_filename = "false"`. This option isn't present in the default `retroarch.cfg`, so put it in the beginning of the file is good idea (easy to edit it later).

And then put another line to the option `screenshot_directory = "/path/to/screenshots"` (I use `/home/pi/screenshots`, but you can set any other valid path). Remember: the directory **MUST** exist, otherwise RetroArch won't be able to save the screenshots.

#### system specific config

If you are happy with the global config, you can jump to the next section. If you want system specific customizations, go on with the reading.

Edit your `/opt/retropie/configs/SYSTEM_NAME/retroarch.cfg` (replace SYSTEM_NAME with the obvious) and configure it like in the global config above.

The system specific configs take precedence over the global ones. So if you want to explicitly turn on/off this functionality for a specific system, you can set `auto_screenshot_filename` to `false` or `true`, respectively. Note that you have to explicitly set it to `true` to turn off the scrape screenshots for a specific system. If it is absent, the script will look for this config in the global `retroarch.cfg`.

If you want to use system specific folders for screenshots, set the `screenshot_directory` option in the system specific `retroarch.cfg`. If it is absent, the script will look for this config in the global file.

### runcommand-onend.sh

Here we will add a script to be executed when the game ends. If you took a screenshot in a gaming session, the script will automatically set the most recent screenshot as the emulationstation image for the game you've just played.

Get the script that makes it happen here: https://raw.githubusercontent.com/meleu/share/master/screeper.sh

From the command line:

```
wget https://raw.githubusercontent.com/meleu/share/master/screeper.sh
mv screeper.sh /opt/retropie/configs/all/runcommand-onend.sh
```

(If you are a shell script guy, maybe you like to read the code. It's well commented.)

Now you can play your game and take your screenshots. The most recent screenshot will be put in your screenshots folder and will be the emulationstation image for this game.

### Restart emulationstation

You have to restart emulationstation in order to see the changes. If all went according to plan, your screenshots will be the game images!

### "I didn't like how it looks! I want my old images back and disable this stuff!"

Easy, only two steps:

1. Change the `auto_screenshot_filename` to true in `retroarch.cfg` (the `runcommand-onend.sh` will do nothing if this option is true).
2. Delete the system specific `gamelist.xml` that is at the system roms directory (example for SNES: `~/RetroPie/roms/snes/gamelist.xml`). It makes the emulationstation get the configs from the original `gamelist.xml` (more details on how gamelists works [here](https://github.com/RetroPie/EmulationStation/blob/master/GAMELISTS.md)).

Restart emulationstation and done!, you have your old scrapes back!

## References

https://retropie.org.uk/forum/topic/3353/take-and-scrape-your-own-screenshots/

https://github.com/RetroPie/EmulationStation/blob/master/GAMELISTS.md

[Scraper](Scraper)

https://github.com/sselph/scraper/wiki/Flags

https://retropie.org.uk/forum/topic/1975/taking-an-actual-screenshot/

https://retropie.org.uk/forum/topic/2483/screenshot-with-rom-name/

https://github.com/RetroPie/RetroPie-Setup/issues/1242
