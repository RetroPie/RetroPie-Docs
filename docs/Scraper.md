Scraping is a way to get metadata, boxart and video previews (snapshots) for your games from the internet. If the scraper isn't working either you are not connected to the Internet or source site may be down or overloaded and in that case you'll just have to wait until it comes back up.

Scraping adds extra information to the game - Publisher, Developer, Release year, Genre, Description, Number of Players supported and Rating.

![A scraped game](https://cloud.githubusercontent.com/assets/10035308/10357565/b97b4ec4-6d40-11e5-9f44-6b27ae31ebc3.png)

Since EmulationStation 2.1.0 you can have a video preview as scraped art, provided that is's supported by the theme EmulationStation is using.

RetroPie includes the following scrapers:

* The built-in EmulationStation scraper, which pulls information from TheGamesDb.net or ScreenScraper.fr.
* Steven Selph's Scraper (`scraper`), which pulls information from TheGamesDB.net, ScreenScraper.fr, [OpenVGDB](https://github.com/OpenVGDB), ArcadeItalia.net. It can also use your local media for scraping, adding it to EmulationStation's gamelist.
* Lars Muldjord's Skyscraper (`skyscraper`), which pulls information from TheGamesDB.net, ScreenScraper.fr, OpenRetro.org, MobyGames.com, IGDB.com and WorldOfSpectrum.org. It also has the ability to import your local media into the final gamelist.

## EmulationStation Built-In Scraper

EmulationStation has a built in scraper that pulls from [TheGamesDB](http://thegamesdb.net/) or [ScreenScraper](https://screenscraper.fr). It can be accessed from the main menu in EmulationStation, opened by the `Start` button.

![scrapermenu](https://cloud.githubusercontent.com/assets/10035308/10713271/534a0560-7a73-11e5-8076-90131881c054.png)

![scrapermenu2](https://cloud.githubusercontent.com/assets/10035308/10713277/92462faa-7a73-11e5-86d4-34e49ca93d14.png)

![scrapermenu3](https://cloud.githubusercontent.com/assets/10035308/10713295/3b237434-7a74-11e5-8c30-68d76b67388e.png)

![scrapermenu4](https://cloud.githubusercontent.com/assets/10035308/10713292/0f9360cc-7a74-11e5-8784-b1f2555a785f.png)

![scrapermenu5](https://cloud.githubusercontent.com/assets/10035308/10713306/b89d2d56-7a74-11e5-9415-485b1b5dbc0f.png)

**Note**: during the *first* scraping session using TheGamesDB as scraping source, Emulationstation will download additional information (list of publishers, developers, genres) from TheGamesDB. The scraper will seem unresponsive for a very short period of time - depending on the download speed - but after the necessary information is downloaded and saved, the scraping will resume. Any subsequent scraping operations will re-use the downloaded information, without any additional downloads.

### Scraper Not Saving Manual Edits

If you are having issues with your metadata changes not being saved, you need to select Quit EmulationStation from the quit menu rather than shutdown or restart system. Then your changes will be saved.

## Steven Selph's Scraper

### Installation
Steven Selph's scraper is one of the simplest and best way of scraping roms (provided that the systems are supported). It can be installed and used from the setup menu using the following steps:

1. (Optional) If you are remotely running this script you must be logged in with `pi` user, otherwise it will confuse the scraper.
2. Quit EmulationStation (from the start menu or press F4) and type `sudo ~/RetroPie-Setup/retropie_setup.sh`.
3. Choose **Manage Packages** then **Manage Optional Packages**.
4. Select `scraper` and install the package.
5. Wait for the installation to complete (it may take some time as it has to install various software libraries)

**It may take some time for the xml files to build. This will also only work if your roms are located in the local roms folder and not on an external device.**

If your roms are located on another source than the default one, you can download the stand alone releases from
[sselph's scraper releases](https://github.com/sselph/scraper/releases).
Please refer to [Sselphs Scraper Advanced Configuration](Scraper#sselphs-scraper-advanced-configuration) when using this method.

Make sure to update to the latest version of Retropie-Setup script if you're missing any options mentioned below!

### Using Scraper

Scraper is started from inside the Retropie Setup Menu. Navigate to **Manage Packages** > **Manage Optional Packages** and select scraper. You will navigate to the **Choose an option for scraper** window. Select option C **Configuration / Options**. It will take you to the window shown below and allow you to run/configure the various functions of the scraper.

<img src="https://raw.githubusercontent.com/UncleRus/__crap/master/sselph_scraper_shot.png" width="550">

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
  * ArcadeItalia.net

- **ROM Names:** Choose what name to display:
  * No-Intro: Rom Name (USA) (Rev 1)
  * theGamesDB: Rom Name
  * FileName: Rom Name [U] [!]

- **Gamelist:** Choose to overwrite the existing gamelist.xml or append to it.

- **Update scraper to the latest version:** This updates the scraper to the latest version.

### Scraping videos

Here is a video showing how to scrape videos using the Steven Selph's Scraper

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/rj1841sL8ro" title="How To Scrape Videos In RetroPie Using Steven Selph's Scraper" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; allowfullscreen"></iframe>

### Advanced Configuration

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

#### Parameter list:
```
Usage of /opt/retropie/supplementary/scraper/scraper:
  -add_not_found
    	If true, add roms that are not found as an empty gamelist entry.
  -append
    	If the gamelist file already exist skip files that are already listed and only append new files.
  -console_img string
    	Comma separated order to prefer images, s=snapshot, b=boxart, f=fanart, a=banner, l=logo, 3b=3D boxart, cart=cartridge, clabel=cartridge label, mix3=Standard 3 mix, mix4=Standard 4 mix. (default "b")
  -console_src string
    	Comma separated order to prefer console sources, ss=screenscraper, ovgdb=OpenVGDB, gdb=theGamesDB (default "gdb")
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
    	Comma separated order to prefer mame sources, ss=screenscraper, adb=arcadeitalia, mamedb=mamedb-mirror, gdb=theGamesDB-neogeo (default "adb,gdb")
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

## Lars Muldjord's Skyscraper

**Skyscraper** by Lars Muldjord is a powerful and versatile yet easy to use game scraper written in C++ for use with multiple frontends running on a Linux system. It scrapes and caches various game resources from various web sources, including media such as screenshot, cover and video. It then gives you the option to generate a game list and artwork for the chosen frontend by combining all of the cached resources.

For a more thorough description of any functionality described here, please check out the [official Skyscraper documentation](https://github.com/muldjord/skyscraper).

### Installation

1. Quit EmulationStation (from the start menu or press F4) and type
   `sudo ~/RetroPie-Setup/retropie_setup.sh`.
2. Choose **Manage Packages** then **Manage optional packages**.
3. Select `skyscraper` and install the package.
4. Wait for the installation to complete.

Make sure to update to the latest version of Retropie-Setup script if you don't have `skyscraper` as an installable package !

### Using Skyscraper

**Skyscraper** can be used to generate scraping information for both [EmulationStation](EmulationStation.md) and [AttractMode](http://attractmode.org). Installing `skyscraper` as a RetroPie package will automatically configure it for EmulationStation, but if you wish to use it for generating **AttractMode** metadata, you can use **Skyscraper** from the command line.

Check the [official documentation](https://github.com/muldjord/skyscraper/blob/master/docs/CLIHELP.md) for a list of all command line options.

The recommended usage is to scrape your system(s) by gathering data (image/videos/information) from as many online sources as you'd like. All of the data will be cached while doing so. Then, when you have gathered enough data, be sure to generate the game list for Emulationstation from the cache. This will combine all of your cached data into the most complete results for each rom.

**Skyscraper** can be started from the RetroPie-Setup script, opening the **Configuration/Tools** menu and choosing `skyscraper`.If you wish to run it from the command line, for more advanced options and parameters, you can find it installed in `/opt/retropie/supplementary/skyscraper/Skyscraper`.

<img width="579" alt="Skyscraper RetroPie package menu" src="https://retropie.org.uk/forum/assets/uploads/files/1551116278774-4ef4d83b-7b8d-481b-a4f9-bff542fca40f-image.png">

Scraping your ROMs and games consists of at least 2 actions:

* Gathering (scraping) the information from online sources and caching it on your system. You can repeat this action as many times you want, changing the gathering source or choosing which platforms (systems) you want.
* Generating the EmulationStation game list files (`gamelist.xml`) using the information from the populated cache.

When using the **Skyscraper** module from the RetroPie-Setup script, the following actions are available in the menu:

- **Gather resources:** This will gather information/media only for the systems you choose.
  Press <kbd>Space</kbd> to select each system you wish to include and <kbd>OK</kbd> to start scraping.

- **Gathering source:** Choose from a menu which source to use for gathering information and media for your ROMs:

  * ONLINE: screenscraper.fr (default)
  * ONLINE: openretro.org
  * ONLINE: thegamesdb.net
  * ONLINE: worldofspectrum.org
  * ONLINE: adb.arcadeitalia.net
  * LOCAL: esgamelist - Scrapes and caches data from an EmulationStation gamelist.xml located at `$HOME/RetroPie/roms/[platform]/gamelist.xml` or `~/.skyscraper/import/[platform]/gamelist.xml`
  * LOCAL: import -- imports resources into the resource cache. Read more about this [here](https://github.com/muldjord/skyscraper/blob/master/docs/IMPORT.md).

  **NOTE:** Some online sources require a username/password for using them. You can add this information by editing the `config.ini` configuration file (from the **Advanced options** menu).

  **INFO:** **Skyscraper** supports IGDB and MobyGames as gathering sources, but they are not integrated into the RetroPie script menu. If you wish to use them, you'll have to use it from the command line.

- **Gathering options** is a sub-menu used to configure various aspects of the gathering phase and of the information added to the cache. You can also use this sub-menu to remove information from the cache, in order to free up space or get rid of unwanted information.

  * _Cache screenshots:_ toggles the download and caching of screenshots from the scraping source into the resource cache.
  Default: _Enabled_

  * _Cache covers:_ toggles the download and caching of covers from the scraping source into the resource cache.
  Default: _Enabled_

  * _Cache wheels:_ toggles the download and caching of wheels from the scraping source into the resource cache.
  Default: _Enabled_

  * _Cache marquees:_ toggles the download and caching of marquees from the scraping source into the resource cache.
  Default: _Enabled_

  * _Scrape only missing:_ runs the scraper only for games/roms without any scraped information/media in the resource cache.
  Default: _Disabled_

  * _Force cache refresh:_ **Skyscraper** caches the media retrieved from online sources to speed up scraping and to combine multiple sources of information to give you the best scraped information available. This option forces the scraper to bypass the resource cache and re-download the resources from the online sources during the gathering action.
  Default: _Disabled_.
  **NOTE**: Use this option sparingly. **Skyscraper** automatically downloads missing media for new ROMs, so it's only needed if your really want to re-download the ROM media from online sources.

  * **Purge commands**
    **Skyscraper** caches locally the media downloaded from online sources. In time, this cache can grow and consume a considerable amount of disk space - especially if videos have been enabled. The cache size is displayed on top in this menu screen.
    You can delete the files from the cache using the following actions available in this menu:
    * **Vacuum chosen platform:** deletes the locally cached resources that don't have a ROM/Game file anymore. Useful to clean up space after deleting ROMs.
    * **Purge chosen platform:** deletes all the locally cached resources for a chosen platform.
    * **Purge all platforms:** deletes all locally cached resources, for all platforms.
    **NOTE:** use these options with care, they will completely remove the cached resources. Generating game lists after you've cleared the cache requires you to re-download the media from the scraping sources all over again.

- **Generate game list(s)** This will generate the EmulationStation game list(s) for the systems you choose using all previously cached resources. Press Space to select the system(s) you wish to include and OK to start the generator..

- **Generate options** is a sub-menu used to configure various options for **Skyscraper** that affect how the game lists will be generated

  * _ROM Names:_ Choose how to display the ROM name in EmulationStation:
    * **Source name** use the name pulled from the scraping source (_default_).
    * **Filename** use the file name of the ROM.
  * _Remove bracket info:_ Choose to remove (**Enabled**) or keep (**Disabled**) the text between brackets. If the name of the ROM is `Super Mario World (USA)[!].sfc`, enabling this option will make the ROM show as `Super Mario World` in EmulationStation. Conversely, when disabled, the text between brackets will be added to the ROM's name in the gamelist.
  Default: _Enabled_.
  * _Use ROM folders for gamelist and media_: Toggle the location where the scraper will generate the final `gamelist.xml` file for EmulationStation:
    * When _Enabled_, the `gamelist.xml` and the media will be written to the ROMs folder.
    * When _Disabled_,the `gamelist.xml` and the media will be written to the EmulationStation configuration folder - `$HOME/.emulationstation/gamelists` and `$HOME/.emulationstation/downloaded_media`.
  Default: _Disabled_

- **Other commands and options**
  * _Download Videos:_ Choose to toggle the download and caching of videos for the ROM names and also if videos are added to the game list for EmulationStation.
    Default: _Disabled_.
  **NOTE:** Be aware that gathering and caching videos could take up a lot of disk space.

  * _Advanced options_ is a separate sub-menu for advanced actions:
    - Edit the [**config.ini**](https://github.com/muldjord/skyscraper/blob/master/docs/CONFIGINI.md) file.
    - Edit the [**artwork.xml**](https://github.com/muldjord/skyscraper/blob/master/docs/ARTWORK.md) file.
    - Edit the **aliasMap.csv** file.

  * _Check for Updates_ will check if a new **Skyscraper** release is available, giving you the option to update to that release.

### Advanced Configuration

#### Configuration files

**Skyscraper** keeps its configuration files and downloaded resources cache in the `~/.skyscraper` folder. When installed through the RetroPie-Setup, this folder is also accessible via [Samba Shares](First-Installation#samba-shares) at

```
\\retropie\configs\all\skyscraper
```

If you wish to edit the configuration files or use the [Import](#import-your-own-media) module, you can do so directly on the system where RetroPie is installed or over the network from another computer.

#### Artwork

**Skyscraper** allows you to fully customize the final frontend artwork by composing the media resources scraped, through the `artwork.xml` configuration file.

Here's an example combining a game's screenshot, its cover and the wheel media files into the final image.

_cover_ | _screenshot_ | _wheel_ | **Final Artwork**
:-:|:-:|:-:|:-:
![cover](https://user-images.githubusercontent.com/31816814/47103794-ac009e00-d248-11e8-881a-d9bdaa1ff00a.png) | ![screenshot](https://user-images.githubusercontent.com/31816814/47103839-bcb11400-d248-11e8-9bf6-9b2043432c1a.png) | ![wheel](https://user-images.githubusercontent.com/31816814/47103856-cd618a00-d248-11e8-8eed-ef4c7728494e.png) | ![artowk](https://user-images.githubusercontent.com/31816814/47103761-9a1efb00-d248-11e8-936d-d52c33aecde1.png)

Consult the [official artwork documentation](https://github.com/muldjord/skyscraper/blob/master/docs/ARTWORK.md) on the artwork customisation.

#### Import your own media

If you have your own media, **Skyscraper** can import it and use it for scraping your ROMs.

Consult the [official import documentation](https://github.com/muldjord/skyscraper/blob/master/docs/IMPORT.md) to understand how to use this feature.

## Troubleshooting
### Slow Boot and Shutdown Times

You'll notice after adding lots of ROMs and scraping them that your boot and shutdown time can increase substantially - some solutions to speed up your boot and shutdown times are described [**HERE**](FAQ.md#why-does-shut-down-and-reboot-take-ages).

### Where are my scraped media and metadata saved?

Once your ROMs have been scraped, the scraped information will be located in two parts: the _Gamelist_ files (containing the ROMs metadata) and the downloaded _Media files_ (images and/or videos). Depending on the options chosen for each scraper, this information can be found in 2 possible places:

Scraper used|Gamelist|Media
-|-|-
EmulationStation | `/home/pi/.emulationstation/gamelists` | `/home/pi/.emulationstation/downloaded_images`
Scraper | <ul style='margin:0'><li>Default <br> `/home/pi/.emulationstation/gamelists` <li>Using **ROM folder for gamelists & images**<br> `/home/pi/RetroPie/roms/<system>`| <ul style='margin:0'><li>Default <br> `/home/pi/.emulationstation/downloaded_images` <li>Using **ROM folder for gamelists & images**<br> `/home/pi/RetroPie/roms/<system>/images`
Skyscraper | <ul style='margin:0'><li>Default <br> `/home/pi/.emulationstation/gamelists` <li>Using **ROM folder for gamelists & media**<br> `/home/pi/RetroPie/roms/<system>`| <ul style='margin:0'><li>Default <br> `/home/pi/.emulationstation/downloaded_media` <li>Using **ROM folder for gamelists & media**<br> `/home/pi/RetroPie/roms/<system>/media`


The `/home/pi/.emulationstation` folder can also be accessed over [Samba Shares](First-Installation#samba-shares) at
```
\\retropie\configs\all\emulationstation
```

**Remember:** if you are going to edit manually any `gamelist.xml` you need to quit EmulationStation first !
