# Taking your  own screenshots and creating your own gamelists

Sometimes the boxarts and other sources for scraping can be low quality and inconsistent in sizes, whereas in game screenshots are standardised to the same size. The following is a simple guide with a script that will help automate the process of taking and scraping your own screenshots.

A few disclaimers first:

- **MAKE A BACKUP AND USE AT YOUR OWN RISK!**

- You need to be on [RetroPie 4.0](https://retropie.org.uk/download/) or be fully [updated](https://github.com/retropie/retropie-setup/wiki/Updating-RetroPie) to the latest version

- You can only create one screenshot per game

- This only works with retroarch emulators

## LETS BEGIN!

### Runcommand

The runcommand menu is what is run every time you play a game, It is what allows you to change emulators, set video resolutions, among other things. One lesser known function is the ability to add customised scripts. We can add a script that will run when a game starts- so in the following example the script will make sure you have the setting in retroarch that names the screenshot after the filename being played, it will create an images folder in the rom directory of the system you're playing games in, and it will set the retroarch.cfg screenshot directory to that images folder. 

you need to create a file called `runcommand-onstart.sh` in the folder `/opt/retropie/configs/all/`

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
if ! grep -q "screenshot_directory" $systemretroarch; then
    iniSet "screenshot_directory" "$imgdir" "$systemretroarch"
fi
```

Now you can play your games and take your screenshots and it will fill your images folder with your screenshots. 

### Take a Screenshot
 
The default screenshot button is `F8` which means if you've configured your keyboard through emulationstation you have to hold the hotkey button (by default the button you configured as select) and then press F8. If you want to have it so that you can take a screenshot with your controller you'll change the screenshot button to a button that isn't already being used for hotkey behaviour. To do this you'll edit the overall or master retroarch.cfg at
`/opt/retropie/configs/all/retroarch.cfg`

the key line you want to change is ~line 580
```
# Take screenshot
# input_screenshot = f8
```
so in my case I changed it to my right analogue thumb on my xbox controller (number values vary with diff controllers)
```
# Take screenshot
input_screenshot_btn = "12"
```

so in game when I want to take a screenshot I hold select (or rather the back button on the xbox controller) and press the right analogue thumb.

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

### Behind the Code

The following is all taken care of by the aformentioned script but if you're interested this explains essentially what the code is doing (and how you can set it up manually without a script)

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

**References:**

https://retropie.org.uk/forum/topic/3353/take-and-scrape-your-own-screenshots/

https://retropie.org.uk/forum/topic/1975/taking-an-actual-screenshot/

https://retropie.org.uk/forum/topic/2483/screenshot-with-rom-name/

https://github.com/RetroPie/RetroPie-Setup/issues/1242

https://github.com/retropie/retropie-setup/wiki/scraper