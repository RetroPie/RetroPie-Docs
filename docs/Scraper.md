Scraping is a way to get metadata and boxart for your games from the internet. The scrapers RetroPie uses pull primarily from thegamesdb.net. If the scraper isn't working either you are not connected to the Internet or thegamesdb.net is down (which happens quite frequently) and in that case you'll just have to wait until it comes back up.

![](https://cloud.githubusercontent.com/assets/10035308/10357565/b97b4ec4-6d40-11e5-9f44-6b27ae31ebc3.png)


# Steven Selph's Scraper

Steven Selph's scraper is the simplest and best way of scraping roms (provided that the systems are supported.) It can be installed and used from the setup menu (menu 3)

**Note that before you can use this scraper you have to exit EmulationStation by pressing f4 or quit from the start menu so that the gamelists are created properly. It may take some time for the xml files to build.**

then to access the setup script from the terminal you can type
```
sudo /home/pi/RetroPie-Setup/retropie_setup.sh
```



![sselph](https://cloud.githubusercontent.com/assets/10035308/14407045/1bdd040e-fe78-11e5-9778-626c216a6498.PNG)

- **Scrape All Systems:** This will scrape all the systems the scraper supports

- **Scrape Chosen Systems:** You can choose to only scrape the systems you choose (press the **spacebar** to select each system) and select ok to start scraping.

![systems](https://cloud.githubusercontent.com/assets/10035308/10713183/98a7ad9a-7a70-11e5-8e24-92d9a4a767b8.png)

- **Thumbnails Only:** When enabled it will load lower resolution images to save space (enabled by default).

- **Max Image Width:** Specify the max image width to scrape.

- **Scraper:** Choose which database to scrape from - thegamesdb is default, but when thegamesdb is down you can specify to use OpenVGBD instead.

- **Update scraper to the latest version:** This updates the scraper to the latest version.

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

