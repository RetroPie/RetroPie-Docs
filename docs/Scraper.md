Scraping is a way to get metadata and boxart for your games from the internet. The scrapers RetroPie uses pull primarily from thegamesdb.net. If the scraper isn't working either you are not connected to the Internet or thegamesdb.net is down (which happens quite frequently) and in that case you'll just have to wait until it comes back up.

![](https://cloud.githubusercontent.com/assets/10035308/10357565/b97b4ec4-6d40-11e5-9f44-6b27ae31ebc3.png)


## Steven Selph's Scraper

Steven Selph's scraper is the simplest and best way of scraping roms (provided that the systems are supported.) It can be installed and used from the setup menu using the following steps:

1. (Optional)If you are remotely running this script you must be logged in with pi otherwise it will confuse the scraper
2. Quit EmulationStation (from the start menu or press F4) and type `sudo ~/RetroPie-Setup/retropie_setup.sh`
3. In 3.x Choose 'Setup'. In 4.x Choose 'Manage Packages' then 'Manage Optional Packages'.
4. Select Scraper
5. Wait for the installation to complete (it may take some time as it has to install various software libraries)

**It may take some time for the xml files to build. This will also only work if your roms are located in the local roms folder and not on an external device.**

If your roms are located on another source than the default one you can download the stand alone releases.
[sselph's scraper releases](https://github.com/sselph/scraper/releases)
Please refer to [Sselphs Scraper Advanced Configuration](Scraper#sselphs-scraper-advanced-configuration) when using this method.

Make sure to update to the latest version of Retropie-Setup script if you're missing any options mentioned below!

<img src="https://raw.githubusercontent.com/UncleRus/__crap/master/sselph_scraper_shot.png" width="400">

- **Scrape All Systems:** This will scrape all the systems the scraper supports

- **Scrape Chosen Systems:** You can choose to only scrape the systems you choose (press the **spacebar** to select each system) and select ok to start scraping.

![systems](https://cloud.githubusercontent.com/assets/10035308/10713183/98a7ad9a-7a70-11e5-8e24-92d9a4a767b8.png)

- **Thumbnails Only:** When enabled it will load lower resolution images to save space (enabled by default).

- **Prefer screenshots:** When enabled it will load screenshots of the games instead of box art.

- **Max Image Width/Height:** Specify the max image width or height to scrape.

- **Console Source:** Choose which database to scrape for console games: 
  * thegamesdb.net (default)
  * ScreenScraper.fr
  * OpenVGDB

- **Arcade Source:** Choose which database to scrape for arcade/mame games: 
  * mamedb.blu-ferret.co.uk (default)
  * ScreenScraper.fr

- **ROM Names:** Choose what name to display:
  * No-Intro: Rom Name (USA) (Rev 1)
  * theGamesDB: Rom Name
  * FileName: Rom Name [U] [!]

- **Gamelist:** Choose to overwrite the existing gamelist.xml or append to it.

- **Update scraper to the latest version:** This updates the scraper to the latest version.

### Scraping videos

Since EmulationStation 2.1.0 you can have a video preview as scraped art. Here is a video showing how to scrape videos using the Steven Selph's Scraper

<a href="https://youtube.com/watch?v=rj1841sL8ro
" target="_blank"><img src="https://i.ytimg.com/vi/rj1841sL8ro/maxresdefault.jpg" 
alt="Scraping Videos"/></a>

### Slow Boot and Shutdown Times

You'll notice after adding lots of ROMs and scraping them that your boot and shutdown time can increase substantially- some solutions to speed up your boot and shutdown times are described [**HERE**](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-does-shut-down-and-reboot-take-ages)

### Where are my scraped images and metadata saved?

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

They can also be accessed over [samba shares](First-Installation#samba-shares)
```
\\retropie\configs\all\emulationstation
```

**Note** if you are going to make edits to any `gamelist.xml` you need to have exited EmulationStation first

## EmulationStation Built-In Scraper:

EmulationStation has a built in scraper that pulls from [thegamesdb](http://thegamesdb.net/). It can be accessed from the start menu in EmulationStation.

![srapermenu](https://cloud.githubusercontent.com/assets/10035308/10713271/534a0560-7a73-11e5-8076-90131881c054.png)

![srapermenu2](https://cloud.githubusercontent.com/assets/10035308/10713277/92462faa-7a73-11e5-86d4-34e49ca93d14.png)

![srapermenu3](https://cloud.githubusercontent.com/assets/10035308/10713295/3b237434-7a74-11e5-8c30-68d76b67388e.png)

![srapermenu4](https://cloud.githubusercontent.com/assets/10035308/10713292/0f9360cc-7a74-11e5-8784-b1f2555a785f.png) 

![srapermenu5](https://cloud.githubusercontent.com/assets/10035308/10713306/b89d2d56-7a74-11e5-9415-485b1b5dbc0f.png)


### Scraper Not Saving Manual Edits

If you are having issues with your metadata changes not being saved, you need to select Quit EmulationStation from the quit menu rather than shutdown or restart system. Then your changes will be saved.

Note that this issue was fixed with RetroPie 3.4

## Sselphs Scraper Advanced Configuration:

#### Scraping your own images

If you have your own images, you can create XML's with Sselph's scraper:

As a template in my snes folder I had my rom name:

`Super Mario World (USA).sfc`

and an images folder with:

`Super Mario World (USA)-image.png`
(If you dont want to append the -image part on the filename you can use `-image_suffix=`)

and I ran 

`/opt/retropie/supplementary/scraper/scraper -img_format=png -add_not_found=true -download_images=false`

And this was the resulting gamelist.xml:

```
<?xml version="1.0" encoding="UTF-8"?>
  <gameList>
      <game id="136" source="theGamesDB.net">
          <path>./Super Mario World (USA).sfc</path>
          <name>Super Mario World (USA)</name>
          <desc>Mario&#39;s off on his biggest adventure ever, and this time he&#39;s brought along a friend.  Yoshi the dinosaur teams up with Mario to battle Bowser, who has kidnapped Princess Toadstool once again.  Guide Mario and Yoshi through nine peril-filled worlds to the final showdown in Bowser&#39;s castle.&#xA;&#xA;Use Mario&#39;s new powers and Yoshi&#39;s voracious monster-gobbling appetite as you explore 96 levels filled with dangerous new monsters and traps.  Climb mountains and cross rivers, and descend into subterranean depths.  Destroy the seven Koopa castles and find keys to gain entrance to hidden levels.  Discover more warps and thrilling bonus worlds than ever before!&#xA;&#xA;Mario&#39;s back, and this time he&#39;s better than ever!</desc>
          <image>./images/Super Mario World (USA)-image.png</image>
          <rating>0.73704</rating>
          <releasedate>19901121T000000</releasedate>
          <developer>Nintendo</developer>
          <publisher>Nintendo</publisher>
          <genre>Platform</genre>
          <players>2</players>
      </game>
  </gameList>
```

### Parameter list:
```
Usage of /opt/retropie/supplementary/scraper/scraper:
  -add_not_found
    	If true, add roms that are not found as an empty gamelist entry.
  -append
    	If the gamelist file already exist skip files that are already listed and only append new files.
  -console_img string
    	Comma seperated order to prefer images, s=snapshot, b=boxart, f=fanart, a=banner, l=logo, 3b=3D boxart, cart=cartridge, clabel=cartridge label, mix3=Standard 3 mix, mix4=Standard 4 mix. (default "b")
  -console_src string
    	Comma seperated order to prefer console sources, ss=screenscraper, ovgdb=OpenVGDB, gdb=theGamesDB (default "gdb")
  -convert_videos
    	If true, convert videos for the Raspberry Pi (e.g. 320x240@30fps) NOTE: This needs HandBrakeCLI installed
  -download_images
    	If false, don't download any images, instead see if the expected file is stored locally already. (default true)
  -download_marquees
    	If true, download marquees.
  -download_videos
    	If true, download videos.
  -extra_ext string
    	Comma separated list of extensions to also include in the scraper.
  -hash_file file
    	The file containing hash information.
  -image_dir directory
    	The directory to place downloaded images to locally. (default "images")
  -image_path path
    	The path to use for images in gamelist.xml. If scrape_all is used, only image_dir is used. (default "images")
  -image_suffix suffix
    	The suffix added after rom name when creating image files. (default "-image")
  -img_format jpg or png
    	jpg or png, the format to write the images. (default "jpg")
  -img_workers N
    	Use N worker threads to process images. If 0, then use the same value as workers.
  -lang string
    	The order to choose for language if there is more than one for a value. (en, fr, es, de, pt) (default "en")
  -mame
    	If true we want to run in MAME mode.
  -mame_img string
    	Comma separated order to prefer images, s=snap, t=title, m=marquee, c=cabniet, b=boxart, 3b=3D-boxart, fly=flyer. (default "t,m,s,c")
  -mame_src string
    	Comma seperated order to prefer mame sources, ss=screenscraper, adb=arcadeitalia, mamedb=mamedb-mirror, gdb=theGamesDB-neogeo (default "adb,gdb")
  -marquee_dir directory
    	The directory to place downloaded marquees to locally. (default "images")
  -marquee_format jpg or png
    	jpg or png, the format to write the marquees. (default "png")
  -marquee_path path
    	The path to use for marquees in gamelist.xml. If scrape_all is used, only marquee_dir is used. (default "images")
  -marquee_suffix suffix
    	The suffix added after rom name when creating marquee files. (default "-marquee")
  -max_height height
    	The max height of images. Larger images will be resized.
  -max_width width
    	The max width of images. Larger images will be resized. (default 400)
  -missing file
    	The file where information about ROMs that weren't scraped is added.
  -nested_img_dir
    	Use a nested img directory structure that matches rom structure.
  -no_thumb
    	Don't add thumbnails to the gamelist.
  -output_file file
    	The XML file to output to. If scrape_all is used, this is ignored and the gamelist in the system path. (default "gamelist.xml")
  -overview_len N
    	If set it will truncate the overview of roms to N characters + ellipsis.
  -refresh
    	Information will be attempted to be downloaded again but won't remove roms that are not scraped.
  -region string
    	The order to choose for region if there is more than one for a value. xx is a special region that will choose any region. (default "us,wor,eu,jp,fr,xx")
  -retries N
    	Retry a rom N times on an error. (default 2)
  -rom_dir directory
    	The directory containing the roms file to process. (default ".")
  -rom_path path
    	The path to use for roms in gamelist.xml. (default ".")
  -scrape_all
    	If true, scrape all systems listed in es_systems.cfg. All dir/path flags will be ignored.
  -skip_check
    	Skip the check if thegamesdb.net is up.
  -ss_password password
    	The password for registered ScreenScraper users.
  -ss_user username
    	The username for registered ScreenScraper users.
  -strip_unicode
    	If true, remove all non-ascii characters.
  -thumb_only
    	Download the thumbnail for both the image and thumb (faster).
  -thumb_suffix suffix
    	The suffix added after rom name when creating thumb files. (default "-thumb")
  -update_cache
    	If false, don't check for updates on locally cached files. (default true)
  -use_filename
    	If true, use the filename minus the extension as the game title in xml.
  -use_nointro_name
    	Use the name in the No-Intro DB instead of the one in the GDB. (default true)
  -version
    	Print the release version and exit.
  -video_dir directory
    	The directory to place downloaded videos to locally. (default "images")
  -video_path path
    	The path to use for videos in gamelist.xml. If scrape_all is used, only video_dir is used. (default "images")
  -video_suffix suffix
    	The suffix added after rom name when creating video files. (default "-video")
  -workers N
    	Use N worker threads to process roms. (default 1)
```
