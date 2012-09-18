# ES-scraper
ES-scraper is a quick script written in Python that uses various online sources ([thegamesdb.net](http://thegamesdb.net) and [archive.vg](http://archive.vg) so far) to scrape artwork and game info and save it as XML files to be read by EmulationStation. The repository can be found [here](https://github.com/elpendor/ES-scraper).

If you're using ES-scraper as a standalone script, you will need to install PIL (for image resizing):

`sudo apt-get install python-imaging`

RetroPie-Setup already installs the necessary dependencies so if you're using it you can skip this step.

# Usage
* Open your systems config file ($HOME/.emulationstation/es_systems.cfg) and append the corresponding [platform ID](Available-Platforms) to each system:
```
NAME=NES
PATH=~/ROMS/NES/
EXTENSION=.nes
COMMAND=retroarch -L /path/to/core %ROM%
PLATFORMID=7
```

* Run the script.
```
python scraper.py
```

# Parameters
```
usage: scraper.py [-h] [-w value] [-noimg] [-v] [-f] [-crc]

ES-scraper, a scraper for EmulationStation

optional arguments:
  -h, --help  show this help message and exit
  -w value    defines a maximum width (in pixels) for boxarts (anything above
              that will be resized to that value)
  -noimg      disables boxart downloading
  -v          verbose output
  -f          force re-scraping
  -crc        CRC scraping
```

# ES-scraper in the RetroPie setup script

ES-scraper can be started from the "setup" menu of the RetroPie setup script. In the scraper menu you can run a normal (re-) scrape of the ROMs (first option) or a forced re-scrape of the ROMs (second option). In all cases the scraper is started with boxart downloading. CRC scraping is used when the third option is chosen. The maximum width (in pixels) for boxarts is set to 350 px. You can change this width with the fourth option.

When the scraper is finished it returns to the setup script.

# Troubleshooting
### The scraper won't find any games (or just a few)
Scraping accuracy really depends on **properly named files and specifying the correct platform ID** in the config file. **Cowering's GoodTools** should be enough to mass rename most of these files.

If everything else fails (and assuming your ROMs and/or other images are untouched), **CRC scraping** is available. CRC scraping uses a different source instead: the archive.vg database. I'll eventually add regular scraping for this db as well, depending on when they update the API to support multiple parameters (or maybe if I come up with a clever way to do it using the current version). Bear in mind that bigger files will take longer as it needs to read the whole file to generate the checksum.