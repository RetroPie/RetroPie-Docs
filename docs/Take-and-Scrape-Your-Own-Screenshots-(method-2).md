# Taking your  own screenshots and creating your own gamelists - Method #2

Sometimes the boxarts and other sources for scraping can be low quality and inconsistent in sizes, whereas in game screenshots are standardised to the same size. The following is a simple guide with a script that will help automate the process of taking and scraping your own screenshots.

A few disclaimers first:

- You have to be comfortable with basic Linux commands and simple file editing.

- **MAKE BACKUP USE AT YOUR OWN RISK!** (What exactly to backup: If you already have a customized `runcommand-onend.sh` file, you need to backup it first. If you don't even know what it is, no worries, just go on.)

- You need to have an updated version of RetroPie-Setup scripts (version 4+) ([updating instructions here](https://retropie.org.uk/download/)).

- This only works with retroarch emulators

- Before using this method you have to [scrape your ROMs](https://github.com/RetroPie/RetroPie-Setup/wiki/scraper). It was not made to start a `gamelist.xml` file from scratch. (About backups again: it will create a copy of your already filled system's `gamelist.xml` and then edit the copied version, so **there's no need to backup the original `gamelist.xml` files**.)


## What exactly this method do

If you take a screenshot during a gaming session, the most recent screenshot will be the emulationstation image for this game. This task is done by a `runcommand-onend.sh` script.

Obviously, there are some conditions to make it happen, in order to let the user easily turn on/off this functionality.


## LETS BEGIN!

### retroarch.cfg

There are two conditions related to RetroArch configuration in order to make it works: 

- `auto_screenshot_filename = "false"`
- `screenshot_directory = "/some/path/to/screenshots"`

The `auto_screenshot_filename = "false"` means that your screenshots will **NOT** be named automatically, they will always be named as `ROM file name.png`. Therefore your most recent screenshot will always overwrite the previous one.

Remember this to avoid confusion: `auto_screenshot_filename = false` means ON for this "scrape screenshots" method. If `auto_screenshot_filename` is true (or absent), it means OFF.

The directory assigned to `screenshot_directory` **MUST** exist, otherwise RetroArch won't be able to save the screenshots.

It doesn't matter if those options are set in global or system specific `retroarch.cfg`.

#### global config (easy way)

Edit your `/opt/retropie/configs/all/retroarch.cfg` and put the option `auto_screenshot_filename = "false"` (suggestion: put it in the beggining of the file). And then put another line to the option `screenshot_directory = "/path/to/screenshots"` (I use `/home/pi/screenshots`, but you can set any other valid path).

#### system specific config

If you are happy with the global config, you can jump to the next section. If you want system specific customizations, go on with the reading.

Edit your `/opt/retropie/configs/SYSTEM_NAME/retroarch.cfg` (replace SYSTEM_NAME with the obvious) and configure it like in the global config above.

The system specific configs take precedence over the global ones. So if you want to explicitly turn on/off this functionality for a specific system, you can set `auto_screenshot_filename` to `false` or `true`, respectively. Note that you have to explicitly set it to `true` to turn off the scrape screenshots for a specific system. If it is absent, the script will look for this config in the global `retroarch.cfg`.

If you want to use system specific folders for screenshots, set the `screenshot_directory` option in the system specific `retroarch.cfg`. If it is absent, the script will look for this config in the global file.

### runcommand

The runcommand menu is what is run every time you play a game, It is what allows you to change emulators, set video resolutions, among other things. One lesser known function is the ability to add customised scripts to be executed before and after the emulator execution.

Here we will add a script to be executed when the game ends. If you took a screenshot in a gaming session, the script will set the most recent screenshot as the emulationstation image for the game you've just played.

Get the script that makes it happen here: https://raw.githubusercontent.com/meleu/src/master/screep.sh

From the command line:

```
wget https://raw.githubusercontent.com/meleu/src/master/screep.sh
mv screep.sh /opt/retropie/configs/all/runcommand-onend.sh
```

Now you can play your game and take your screenshots. The most recent screenshot will be put in your screenshots folder and will be the emulationstation image for this game.


### Take a Screenshot

#### via RGUI

Access the RGUI (usually with Select+X) and go to `Quick Menu` -> `Take Screenshot`.


#### via hotkeys
 
The default screenshot button is `F8` which means if you've configured your keyboard through emulationstation you have to hold the hotkey button (by default the button you configured as select) and then press F8. If you want to have it so that you can take a screenshot with your controller you'll change the screenshot button to a button that isn't already being used for hotkey behaviour. To do this you'll edit the overall or global `retroarch.cfg` at
`/opt/retropie/configs/all/retroarch.cfg`

The key line you want to change is ~line 580
```
# Take screenshot
# input_screenshot = f8
```
So in my case I changed it to my right analogue thumb on my xbox controller (number values vary with diff controllers)
```
# Take screenshot
input_screenshot_btn = "12"
```

So in game when I want to take a screenshot I hold select (or rather the back button on the xbox controller) and press the right analogue thumb.


### Restart emulationstation

The files with the emulationstation configs are read when it is launching, so you have to restart emulationstation. If all went according to plan, your screenshots will be the game images! TADA!


## "I didn't like how it looks! I want my old images back!"

Easy, only two steps:

1. Change the `auto_screenshot_filename` to true in `retroarch.cfg`, it disables the "scrape your screenshots" method.
2. Delete the system specific `gamelist.xml` that is at the system roms directory (example for SNES: `~/RetroPie/roms/snes/gamelist.xml`). It makes the emulationstation get the configs from the original `gamelist.xml` (more details on how gamelists works [here](https://github.com/RetroPie/EmulationStation/blob/master/GAMELISTS.md)).

Restart emulationstation and done!, you have your old scrapes back!


**References:**

https://github.com/RetroPie/RetroPie-Setup/wiki/Take-and-Scrape-Your-Own-Screenshots

https://retropie.org.uk/forum/topic/3353/take-and-scrape-your-own-screenshots/

https://github.com/RetroPie/EmulationStation/blob/master/GAMELISTS.md

https://retropie.org.uk/forum/topic/1975/taking-an-actual-screenshot/

https://retropie.org.uk/forum/topic/2483/screenshot-with-rom-name/

https://github.com/RetroPie/RetroPie-Setup/issues/1242

https://github.com/retropie/retropie-setup/wiki/scraper
