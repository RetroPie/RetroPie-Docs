# Introduction
This page describes how to use UI modes within EmulationStation (ES). 
These modes allow administrators to lock down (part of) the system, so that naive users are less likely to change any settings inadvertently. 

> *Do you want to be able to leave your carefully set-up Retropie system alone with a group of friends?  Without having to re-flash the SD card afterwards? Do you want your kids to enjoy your childhood, but maybe not play Mortal Kombat just yet? Do you want to simplify your UI by hiding all configuration items once you're done tweaking the set-up?*
>**UI modes are for you!**

# Overview
* [UI modes](#ui-modes)  
* [Switching modes](#switching-modes)  
* [Gamelist.xml](#gamelist.xml)
* [Themes](#themes)
***

# UI modes
To allow different levels of system protection, user modes have been introduced to allow the user to restrict certain settings and files from use. The two new modes are Kiosk and Kid. In general, visiting friends and children do not need to modify system settings. The full set of options also complicates the UI. The kid and kiosk modes hide these for a simpler experience.

Setting UI mode to Full will give you the default ES user interface. This includes options such as CONFIGURE INPUT, UI SETTINGS, SCRAPER, but also EDIT THIS GAMES METADATA, and many other menu items that allow you to configure the system.

Kiosk and Kid mode expose fewer of the menu options of Emulation Station, only showing menu items that do not affect the system configuration (i.e. do not survive a reboot). In Kiosk Mode, the user is still able to toggle the favorite status of a game. In Kid mode, this functionality is removed.

In addition to this, the Kiosk and Kid modes allow for filtering of the game lists to hide unwanted games from view. This does not remove any files from the system. Kiosk mode only shows items in the game lists that are not explicitly set to be hidden (aka blacklisting). The Kid mode only shows items which are explicitly selected to be kid-friendly (aka whitelisting). Items which are set to be both `hidden` and `kidgame`, will be visible while in UI mode `kid`, but not while in UI mode `Kiosk`.

# Switching modes
To switch the UI mode from Full to one of the limited modes, a new menu option was implemented under UI OPTIONS:
![uimodemenu_comb](https://user-images.githubusercontent.com/6103768/32353188-ac071a64-c024-11e7-9882-70645d66f250.png)

Switching back to the Full UI
Once the system is in one of the restricted modes, it is not possible to access the UI OPTIONS menu to revert to the full UI. To return to the full UI while the system is restricted, go to the `/home/pi/.emulationstation/es_settings.cfg` file and edit the UI_mode value to read:
`<string name="UIMode" value="Full" />`

Alternatively, you can use a pre-defined passkey sequence that you can enter while you are anywhere in the ES interface. The default passkey is [up,up, down, down, left, right, left, right, b, a] which some of you might recognize as the Konami cheat code from olden-times. This sequence can be changed in `es_settings.cfg ` if need be:
`<string name="UIMode_passkey" value="uuddlrlrba" />`
When successfully entered, this will reset the UI mode to FULL.

# Gamelist.xml 
So in all, three new tags have been introduced: favorites, kid game, and hidden (all boolean).
```
<game>
 	...
 	<favorite>false</favorite>
 	<kidgame>true</kidgame>
 	<hidden>false</hidden>
 	...`
`</game>

```

These new metadata tags are not present in the gamelists you have by default, but once you edit the metadata for a single game, they will be added for that specific system’s `gamelist.xml`. If you want to edit your `gamelist.xml` files in some other tools outside ES, you will need to take care not to overwrite or remove these tags.

The values can be set using the meta-data editor in the UI, or by directly editing the gamelist.xml file (make sure to exit ES first, as it will overwrite the file upon exit). This latter method could be much faster if you want to set the metadatavalue for a lot of items.
![metadata_resize](https://user-images.githubusercontent.com/6103768/32353325-3bcb19b6-c025-11e7-886c-c4643a0e71b7.png)

# Themes
The beta version of this functionality (from mid-2016) had some limited theming support to show the status of favorites, hidden and kid metadata fields in the theme. This has been removed, possibly to be restored in a later update.
