Scraping is a way to get metadata and boxart for your games from the internet. The scrapers RetroPie uses pull primarily from thegamesdb.net. If the scraper isn't working either you are not connected to the Internet or thegamesdb.net is down (which happens quite frequently) and in that case you'll just have to wait until it comes back up.

![](https://cloud.githubusercontent.com/assets/10035308/10357565/b97b4ec4-6d40-11e5-9f44-6b27ae31ebc3.png)


# Steven Selph's Scraper

Steven Selph's scraper is probably the simplest way of scraping roms (provided that the systems are supported.) It can be installed and used from the setup menu (menu 3)

![sselph](https://cloud.githubusercontent.com/assets/10035308/14407045/1bdd040e-fe78-11e5-9778-626c216a6498.PNG)

- **Scrape All Systems:** This will scrape all the systems the scraper supports

- **Scrape Chosen Systems:** You can choose to only scrape the systems you choose (press the **spacebar** to select each system) and select ok to start scraping.

![systems](https://cloud.githubusercontent.com/assets/10035308/10713183/98a7ad9a-7a70-11e5-8e24-92d9a4a767b8.png)

- **Thumbnails Only:** When enabled it will load lower resolution images to save space (enabled by default).

- **Max Image Width:** Specify the max image width to scrape.

- **Scraper:** Choose which database to scrape from - thegamesdb is default, but when thegamesdb is down you can specify to use OpenVGBD instead.

- **Update scraper to the latest version:** This updates the scraper to the latest version.

Note that while scraping you have to kill EmulationStation processes so that the gamelists are created properly. It may take some time for the xml files to build.

#### Where are my scraped images and metadata saved?

Once your games have been scraped they will be located in two parts: `Downloaded Images` and `Gamelists`
```
/home/pi/.emulationstation/downloaded_images
or
/opt/retropie/configs/all/emulationstation/downloaded_images
```
and
```
/home/pi/.emulationstation/gamelists
or
/opt/retropie/configs/all/emulationstation/gamelists
```

They can also be accessed over [samba shares](https://github.com/retropie/retropie-setup/wiki/First-Installation#samba-shares-needs-an-active-internet-connection)
```
\\retropie\configs\all\emulationstation
```
# EmulationStation Built-In Scraper:

EmulationStation has a built in scraper that pulls from [thegamesdb](http://thegamesdb.net/). It can be accessed from the start menu in emulationstation.

![srapermenu](https://cloud.githubusercontent.com/assets/10035308/10713271/534a0560-7a73-11e5-8076-90131881c054.png)

![srapermenu2](https://cloud.githubusercontent.com/assets/10035308/10713277/92462faa-7a73-11e5-86d4-34e49ca93d14.png)

![srapermenu3](https://cloud.githubusercontent.com/assets/10035308/10713295/3b237434-7a74-11e5-8c30-68d76b67388e.png)

![srapermenu4](https://cloud.githubusercontent.com/assets/10035308/10713292/0f9360cc-7a74-11e5-8784-b1f2555a785f.png) 

![srapermenu5](https://cloud.githubusercontent.com/assets/10035308/10713306/b89d2d56-7a74-11e5-9415-485b1b5dbc0f.png)


### Scraper Not Saving Manual Edits

If you are having issues with your metadata changes not being saved, you need to select Quit EmulationStation from the quit menu rather than shutdown or restart system. Then your changes will be saved.

Note that this issue was fixed with RetroPie 3.4

# ES-scraper
ES-scraper is a quick script written in Python that uses various online sources ([thegamesdb](http://thegamesdb.net/) and [archive.vg](http://archive.vg) so far) to scrape artwork and game info and save it as XML files to be read by EmulationStation. ~~The repository can be found [here](https://github.com/elpendor/ES-scraper)~~

**The code currently in the repository is not compatible with the current version of EmulationStation**

A fork of this repository has been modified to handle the newer XML style configuration [here](https://github.com/jmschultz/ES-scraper)

If you're using ES-scraper as a standalone script, you will need to install PIL (for image resizing):

`sudo apt-get install python-imaging`

RetroPie-Setup already installs the necessary dependencies so if you're using it you can skip this step.

# Usage
* Open your systems config file (/etc/emulationstation/es_systems.cfg) and append the corresponding platform ID to each system:
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
usage: scraper.py [-h] [-w value] [-noimg] [-v] [-f] [-crc] [-p]

ES-scraper, a scraper for EmulationStation

optional arguments:
  -h, --help  show this help message and exit
  -w value    defines a maximum width (in pixels) for boxarts (anything above
              that will be resized to that value)
  -noimg      disables boxart downloading
  -v          verbose output
  -f          force re-scraping (ignores and overwrites the current gamelist)
  -crc        CRC scraping
  -p          partial scraping (per console)
  -m          manual mode (choose from multiple results)
```

# Troubleshooting
### The scraper won't find any games (or just a few)
Scraping accuracy really depends on **properly named files and specifying the correct platform ID** in the config file. **Cowering's GoodTools** should be enough to mass rename most of these files.

If everything else fails (and assuming your ROMs and/or other images are untouched), **CRC scraping** is available. CRC scraping uses a different source instead: the archive.vg database. I'll eventually add regular scraping for this db as well, depending on when they update the API to support multiple parameters (or maybe if I come up with a clever way to do it using the current version). Bear in mind that bigger files will take longer as it needs to read the whole file to generate the checksum.
