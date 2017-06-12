![](http://www.grandrapidsdevs.com/wp-content/uploads/2015/06/kodiLogo.png)
***

_Kodi is a Home Media Server (basically your own personal netflix) formerly known as XBMC. Kodi is currently an optional build that can be installed from the optional menu of the setup script._

***
## General Information

See here for more info: http://kodi.tv/

See [here](http://blog.petrockblock.com/forums/topic/kodi-tab-in-emulationstation/) for more information on setting up Kodi

## Installation

Visit the RetroPie-Setup Screen, select Optional Packages, and select Kodi.  Installation can take 10 minutes.  After installation, you will be able to go to the Ports section and view Kodi as an option.

RetroPie currently installs Kodi 17.3 Krypton

### PVRs Installation

By default, RetroPie doesn't install any PVRs. If you want to install them, run the following commands in a terminal:

Search available PVRs:
````
apt-cache search kodi-pvr
````
Install one PVR, in this case IPTV Simple Client:
````
sudo apt-get install kodi-pvr-iptvsimple
````
Install all PVRs:
````
sudo apt-get install kodi-pvr*
````

## Joypad Support

The latest Kodi module (Kodi 17/17.3) includes joypad support by default. Some joypads are detected and work out-of-the-box like PS3, Xbox360, Logitech, Ibuffalo, Retrolink Snes and more. If your joypad doesn't work OOTB or you prefer to add your custom keymap, create the file `/home/pi/.kodi/userdata/keymaps/joystick.xml` like the following

**Example** `joystick.xml`
```
<?xml version="1.0" encoding="UTF-8"?>
<keymap>
  <global>
    <joystick name="USB gamepad           ">
      <button id="3">Select</button>
      <button id="2">Back</button>
      <axis id="1" limit="+1">Right</axis>
      <axis id="1" limit="-1">Left</axis>
      <axis id="2" limit="-1">Up</axis>
      <axis id="2" limit="+1">Down</axis>
    </joystick>
  </global>
</keymap>
```

You can see what your joystick name is with `cat /proc/bus/input/devices`

For more information on how to create your custom keymaps for Kodi, check [here](http://kodi.wiki/view/keymap)


#### Xbox 360:

If you are experiencing problems with your Xbox controls, see the following examples and adapt for your version of controller
- [**HERE**](http://kodi.wiki/view/Xbox_360_Wireless_Controller) 
- [Example 1](https://github.com/xbmc/xbmc/blob/Eden/system/keymaps/joystick.Microsoft.Xbox.360.Controller.xml)
- [Example 2](http://pastebin.com/ZiNyYEZV)
- [Example 3](https://gitlab.com/ember-dev/kodi/blob/436c61114dfbf7ec0667873428da0812de3c6954/system/keymaps/joystick.Microsoft.Xbox.360.Controller.xml)

## Recommended Smartphone App to control Kodi: [Yatse](http://yatse.tv/redmine/projects/yatse)

![](http://kodi.wiki/images/3/3c/Yatse_Holo_1.png)

## Kodi as its own system instead of in ports

The first method here is a cleaner method that wont mess with the RetroPie setup script updates (note that in the future you will have to manually update the es_systems.cfg in .emulationstation as they aren't overwritten on updates from RetroPie). Once you've installed Kodi from the experimental menu of the setup script, Drop into a terminal with f4 or access the pi over [SSH](https://github.com/retropie/retropie-setup/wiki/ssh)

create an es_systems.cfg file so that Kodi will show up in emulationstation

```
sudo cp /etc/emulationstation/es_systems.cfg /home/pi/.emulationstation/es_systems.cfg
sudo nano /home/pi/.emulationstation/es_systems.cfg
```
add the following codeblock anywhere after `<systemList>`:
```
  <system>
    <fullname>Kodi</fullname>
    <name>kodi</name>
    <path>~/RetroPie/roms/kodi</path>
    <extension>.sh .SH</extension>
    <command>bash %ROM%</command>
    <platform>kodi</platform>
    <theme>kodi</theme>
  </system>
```

save you changes with `ctrl+x` , `y` , `enter`

then make a kodi rom directory

```
mkdir /home/pi/RetroPie/roms/kodi
```

make a launch script:

```
sudo nano /home/pi/RetroPie/roms/kodi/kodi.sh
```

add the following line:

```
kodi-standalone
```
save you changes with `ctrl+x` , `y` , `enter`

make the launch script executable:
```
sudo chmod +x /home/pi/RetroPie/roms/kodi/kodi.sh
```

type `emulationstation` to go back into emulationstation and kodi should be there as its own system. 

## Old configs

```
# Kodi on Raspbian Wheezy
## Black Screen Freeze Fix

If you find yourself having troubles with your screen freezing when you exit Kodi, you can replace the code in `/roms/ports/kodi.sh` with

#!/bin/bash
 
LOG_FILE=$HOME/.kodi/temp/kodi.log
 
rm $LOG_FILE 2> /dev/null
 
/usr/lib/kodi/kodi.bin --standalone &
 
while [[ ! -f $LOG_FILE ]] ; do
  sleep 1s
done
 
while read line ; do
  if [[ ${line} =~ "application stopped" ]] ; then
    echo "Killing kodi"
    break
  fi
done < <(tail --pid=$$ -f -n0 $LOG_FILE)
 
killall kodi.bin
 
fbset -depth 8 && fbset -depth 16

(note there may be some issues with the framebuffer but its the only functioning fix at the moment short of compiling Kodi 15)
```