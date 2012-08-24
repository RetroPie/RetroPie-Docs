# ES-scraper
ES-scraper is a quick script written in Python that uses various online sources ([thegamesdb.net](http://thegamesdb.net) and [archive.vg](http://archive.vg) so far) to scrape artwork and game info and save it as XML files to be read by EmulationStation.

For image resizing to work, you will need to install PIL:

`sudo apt-get install python-imaging`

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