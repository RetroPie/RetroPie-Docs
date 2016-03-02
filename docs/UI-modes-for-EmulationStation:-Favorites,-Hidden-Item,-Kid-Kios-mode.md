# Introduction
This page describes the functioning of an experimental branch of EmulationStation (ES). This branch allows ES to be run in three different UI modes: Full, Kiosk and Kid mode. These modes have ever decreasing options available, and are meant for people who want to be able to leave the carefully set up installation alone with a group of friends/kids without having to re-flash the SD card afterwards.
The Full mode offers the same functionality as the vanilla ES UI. The Kiosk mode only shows items in the game-lists that are not explicitly hidden. The Kid only shows items which are explicitly selected to be kid-friendly (and excludes almost all system options).

***

### _This is in the experimental packages for a reason, backup everything you cannot afford to lose!_

***

# Installation
The ES branch is located at: https://github.com/zigurana/EmulationStation/tree/UI_modes_Kiosk_Kid_Full . It can be installed **over your current installation of ES** via the RetroPie-Setup script. It is located under 'Experiment Packages' > option 306: emulationstation-kids

# Features
## UI modes
To allow different levels of system 'lock-down', user modes were introduced with different sets of functionalities. These modes are Full, Kiosk and Kid. Generally speaking, kids do not need to edit system settings, nor will visiting friends. The full set of options also complicates the UI, and the kid and kiosk modes hide these when they are not needed.

**Full user interface **
Aka admin mode – This is the current UI, it has all the options, bells and whistles.
**Kiosk mode**
This mode hides most of the ui options, such as CONFIGURE INPUT, UI SETTINGS, SCRAPER, but also EDIT THIS GAMES METADATA, etc. In addition this mode also hides those entries in the gamelist which have their metadata-tag `hidden `set to true.
**Kid mode**
This mode has all the restrictions of Kiosk mode, but in addition -only- lists games which are explicitly white-listed. This can be done by setting the metadata-tag `Kid-game` to true.
![Compare the full UI with Kid ui, showing only selected games](https://dl.dropboxusercontent.com/u/859248/RetroPieES/systemlist_gamelist_full_kid.png)

To switch the UI mode from Full to one of the limited modes, a new menu option was implemented under UI OPTIONS:
![screenshot of UI](https://dl.dropboxusercontent.com/u/859248/RetroPieES/UIModeMenu_comb.png)

Switching back to the Full UI
Once you are in one of the restricted modes, the UI options (where I put the UI Mode selector), is not shown anymore. So how to return to the full UI once your in Kid/kiosk mode? Well one way, is to go to the `/home/pi/.emulationstation/es_settings.cfg `file and edit the UI_mode value manually:
`<string name="UIMode" value="Full" />`

Alternatively, you can use a pre-defined passkey sequence that you can enter while you are anywhere in the ES ui. The default passkey is [up,up, down, down, left, right, left, right, b, a] which some of you might recognize as the Konami cheat code from olden-times. This sequence can be changed in `es_settings.cfg ` if need be:
`<string name="UIMode_passkey" value="uuddlrlrba" />`
When succesfully entered, this will exit (and restart) ES.

## Favorites in ES
This branch of ES has incorporated the pull request by Kaptainka to allow the setting of favorites in the game-list, and subsequent filtering of said list to show only the favorites.

## Gamelist.xml 
So in three new tags have been introduced: favorites, kid game, and hidden (all boolean).   
`<game>`  
 	`...`   
 	`<favorite>false</favorite>`   
 	`<kidgame>true</kidgame>`   
 	`<hidden>false</hidden>`   
 	`...`   
 `</game> `   

Of course, these new metadata tags are not present in the gamelists you have by default, but once you edit the metadata for a single game, they will be added for that specific system’s `gamelist.xml`. If you want to edit your `gamelist.xml` files in some other tools (for instance SSelphs excellent scraper), you will need to take these new tags into account.

The values can be set using the meta-data editor in the UI, or by directly editing the gamelist.xml file (make sure to exit ES first, as it will overwrite the file upon exit).
[https://dl.dropboxusercontent.com/u/859248/RetroPieES/metadata_resize.png](metadata editor UI)

# Themes
The visualization for these tags are NOT included in most of the current themes (which are specified by version 3). 
In his/her original pull request, kaptainkia suggested to increase the xml version to 4 to indicate the availability of the new favorite tag. This has been copied for the other tags as well. At least from the ES side of things, you can then keep on using the old themes, without anything breaking. You will just not be able to see the values at a glance.

If the theme supports it, the boolean status of metadata items Favorite, Hidden, and Kidgame is visualized using simple icons:
![screenshot of the theme](https://dl.dropboxusercontent.com/u/859248/RetroPieES/newtheme.png)

To see these changes, you will also need to update your theme(s). To make a start, I’ve updated the Carbon theme to include these new elements. [You can download it here.](https://dl.dropboxusercontent.com/u/859248/RetroPieES/carbon_v4.zip)

This theme will also allow you to toggle some values quickly using x for favorites and y for kidgames.
![toggle screenshot](https://dl.dropboxusercontent.com/u/859248/RetroPieES/gameList_toggle_crop.png)
 
If you want in include this in your own theme, these are the items to add:  

`<image name="md_hidden">`  
     `<pos>0.17 0.165</pos>`  
     `<path>./../art/hidden.svg</path>`  
     `<maxSize>0.06 0.045</maxSize>`  
     `<origin>0 0</origin>`  
`</image>`  
`<image name="md_kidgame">`  
     `<pos>0.10 0.16</pos>`  
     `<path>./../art/teddy.svg</path>`  
     `<maxSize>0.06 0.06</maxSize>`  
     `<origin>0 0</origin>`  
`</image>`  
`<image name="md_favorite">`  
     `<pos>0.03 0.165</pos>`  
     `<path>./../art/heart.svg</path>`  
     `<maxSize>0.045 0.045</maxSize>`  
     `<origin>0 0</origin>`  
`</image>`  

The corresponding images are in the folder ` carbon_v4\art `. Of course, the values for pos and sizes will depend on the theme.

# Random Game selection
The original plan was to get a random game starter that could be triggered as some sort of screensaver, and act as a stand-in for an actual attract-mode. I got it working up to the point where it is an option in the GameList Options menu (what you get when you press ‘select’ while in a game-list view):
![](https://dl.dropboxusercontent.com/u/859248/RetroPieES/surprise_me_crop.png)
This will change the view focus to a new random game, in any of the systems that have games that are visible given the current UI mode. The implementation of the screensaver turned out to be very tricky and has been demoted to a someday-maybe project.

# Future developments
The difference between the stock ES and this branch is rather large, with many small changes in a lot of files. Consequently, when any update occurs in the original ES branch (upstream), this might impact this branch as well. Therefore, the risk of a high maintenance burden for this branch was deemed too high to incorporate it into the RetroPie branch proper. Kid Mode ES will remain in the experimental packages menu, where it is available for users who which to test it out.

For the foreseeable future this ES version will remain maintained will be done by https://github.com/zigurana, merging in all relevant changes when they occur (or when someone alerts him to it).

# Credits
* Aloshi, of course.
* The RetroPie team: Buzz, Herb, Floob,  for bringing this to the masses.
* Kaptainka, for the initial implementation of favorites in ES.
* Gizmo98, for creating the module in the RetroPie-setup script.
* The beta-testers who went bug hunting and helped make this better. See [here](http://blog.petrockblock.com/forums/topic/kid-friendly-retropiees-ui-modes-favorites-hiding-items-s-testers-wanted/) for the original forum thread.