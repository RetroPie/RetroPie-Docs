Scraping is a way to get metadata and boxart for your games from the internet. The scrapers RetroPie uses pull primarily from thegamesdb.net. If the scraper isn't working either you are not connected to the Internet or thegamesdb.net is down (which happens quite frequently) and in that case you'll just have to wait until it comes back up.

![](https://cloud.githubusercontent.com/assets/10035308/10357565/b97b4ec4-6d40-11e5-9f44-6b27ae31ebc3.png)


# Steven Selph's Scraper

Steven Selph's scraper is the simplest and best way of scraping roms (provided that the systems are supported.) It can be installed and used from the setup menu using the following steps:

1) Quit EmulationStation and type on the command line
```
sudo /home/pi/RetroPie-Setup/retropie_setup.sh
```

2) In the "Choose an option" menu choose item 3, "Setup / Configuration (to be used post install)"

3) In the "Choose task" menu choose item 821, "Scraper for EmulationStation by Steven Selph"

4) Wait for the installation to complete (it may take some time as it has to install various software libraries)

**Note that before you can use this scraper you have to exit EmulationStation by pressing f4 or quit from the start menu so that the gamelists are created properly. It may take some time for the xml files to build. This will also only work if your roms are located in the local roms folder and not on an external device.**

To use the scraper at any time, you run the setup script from the terminal again.

**Note that if you are remotely running this script you must be logged in with pi otherwise it will confuse the scraper.**
```
sudo /home/pi/RetroPie-Setup/retropie_setup.sh
```

Make sure to update to the latest version of Retropie-Setup script if youre missing any options mentioned below!

<img width="500" alt="sselph" src="https://cloud.githubusercontent.com/assets/8129878/15624414/5d56d330-2455-11e6-8a6a-850678d58712.png">

- **Scrape All Systems:** This will scrape all the systems the scraper supports

- **Scrape Chosen Systems:** You can choose to only scrape the systems you choose (press the **spacebar** to select each system) and select ok to start scraping.

![systems](https://cloud.githubusercontent.com/assets/10035308/10713183/98a7ad9a-7a70-11e5-8e24-92d9a4a767b8.png)

- **Thumbnails Only:** When enabled it will load lower resolution images to save space (enabled by default).

- **Max Image Width:** Specify the max image width to scrape.

- **Scraper:** Choose which database to scrape from - thegamesdb is default, but when thegamesdb is down you can specify to use OpenVGBD instead.

- **ROM Names:** Choose what name to display:
  * No-Intro: Rom Name (USA) (Rev 1)
  * theGamesDB: Rom Name
  * FileName: Rom Name [U] [!]

- **Gamelist:** Choose to overwrite the existing gamelist.xml or append to it.

- **Update scraper to the latest version:** This updates the scraper to the latest version.

#### Slow Boot and Shutdown Times

You'll notice after adding lots of ROMs and scraping them that your boot and shutdown time can increase substantially- some solutions to speed up your boot and shutdown times are described [**HERE**](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-does-shut-down-and-reboot-take-ages)

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

#### Parameter list:
```
Usage of /opt/retropie/supplementary/scraper/scraper:
  -add_not_found=false: If true, add roms that are not found as an empty gamelist entry.
  -append=false: If the gamelist file already exist skip files that are already listed and only append new files.
  -download_images=true: If false, don't download any images, instead see if the expected file is stored locally already.
  -extra_ext="": Comma separated list of extensions to also include in the scraper.
  -gdb_img="b": Comma seperated order to prefer images, s=snapshot, b=boxart, f=fanart, a=banner, l=logo.
  -hash_file="": The `file` containing hash information.
  -image_dir="images": The `directory` to place downloaded images to locally.
  -image_path="images": The `path` to use for images in gamelist.xml.
  -image_suffix="-image": The `suffix` added after rom name when creating image files.
  -img_format="jpg": `jpg or png`, the format to write the images.
  -img_workers=0: Use `N` worker threads to process images. If 0, then use the same value as workers.
  -mame=false: If true we want to run in MAME mode.
  -mame_img="s,t,m,c": Comma separated order to prefer images, s=snap, t=title, m=marquee, c=cabniet.
  -max_width=400: The max `width` of images. Larger images will be resized.
  -missing="": The `file` where information about ROMs that weren't scraped is added.
  -nested_img_dir=false: Use a nested img directory structure that matches rom structure.
  -no_thumb=false: Don't add thumbnails to the gamelist.
  -output_file="gamelist.xml": The XML `file` to output to.
  -overview_len=0: If set it will truncate the overview of roms to `N` characters + ellipsis.
  -refresh=false: Information will be attempted to be downloaded again but won't remove roms that are not scraped.
  -retries=2: Retry a rom `N` times on an error.
  -rom_dir=".": The `directory` containing the roms file to process.
  -rom_path=".": The `path` to use for roms in gamelist.xml.
  -scrape_all=false: If true, scrape all systems listed in es_systems.cfg. All dir/path flags will be ignored.
  -skip_check=false: Skip the check if thegamesdb.net is up.
  -start_pprof=false: If true, start the pprof service used to profile the application.
  -strip_unicode=true: If true, remove all non-ascii characters.
  -thumb_only=false: Download the thumbnail for both the image and thumb (faster).
  -thumb_suffix="-thumb": The `suffix` added after rom name when creating thumb files.
  -use_filename=false: If true, use the filename minus the extension as the game title in xml.
  -use_gdb=true: Use the hash.csv and theGamesDB metadata.
  -use_nointro_name=true: Use the name in the No-Intro DB instead of the one in the GDB.
  -use_ovgdb=false: Use the OpenVGDB if the hash isn't in hash.csv.
  -version=false: Print the release version and exit.
  -workers=1: Use `N` worker threads to process roms.
```
