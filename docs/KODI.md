<img src="https://kodi.tv/images/kodi-logo-with-text.svg" title="Kodi" alt="Kodi image" width="240">

***

_Kodi is a Home Media Server (basically your own personal Netflix) formerly known as XBMC. Kodi is currently an optional build that can be installed from the optional menu of the setup script._

***
## General Information

See here for more info: http://kodi.tv/

See [here](http://blog.petrockblock.com/forums/topic/kodi-tab-in-emulationstation/) for more information on setting up Kodi.

## Installation

Visit the RetroPie-Setup Screen, select Optional Packages, and select Kodi.  Installation can take 10 minutes.  After installation, you will be able to go to the Ports section and view Kodi as an option.

RetroPie currently installs Kodi 17.6 "Krypton" on Raspbian Jessie and Kodi 18 "Leia" on Raspbian Stretch and Ubuntu PC systems.

### PVRs Installation

By default, RetroPie doesn't install any PVRs (personal video recorders). If you want to install them, run the following commands in a terminal:

Search available PVRs:
````
apt search kodi-pvr
````
Install one PVR, in this case the IPTV Simple Client:
````
sudo apt install kodi-pvr-iptvsimple
````
Install all PVRs:
````
sudo apt install kodi-pvr*
````

## Joypad Support

The latest Kodi module (Kodi 17/17.6) includes joypad support by default. Some joypads are detected and work out-of-the-box like PS3, Xbox360, Logitech, iBuffalo, Retrolink SNES, and more. If your joypad doesn't work OOTB or you prefer to add your custom keymap, create the file `/home/pi/.kodi/userdata/keymaps/joystick.xml` like the following:

**Example** `joystick.xml`
```
<?xml version="1.0" encoding="UTF-8"?>
<keymap>
  <global>
    <joystick name="USB gamepad">
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

You can see what your joystick name is with `cat /proc/bus/input/devices`.

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

The first method here is a cleaner method that won't mess with the RetroPie setup script updates. (Note: in the future, you will have to manually update `/home/pi/.emulationstation/es_systems.cfg`, as it will not be overwritten by RetroPie updates.) Once you've installed Kodi from the optional menu of the setup script, drop into a terminal with F4 or access the pi over [SSH](SSH).

Create an es_systems.cfg file so that Kodi will show up in EmulationStation:

```
cp /etc/emulationstation/es_systems.cfg /home/pi/.emulationstation/es_systems.cfg
nano /home/pi/.emulationstation/es_systems.cfg
```
Add the following codeblock anywhere after `<systemList>` and before `</systemList>`:
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

Save your changes with `ctrl+x` , `y` , `enter`.

Then make a Kodi ROM directory:

```
mkdir /home/pi/RetroPie/roms/kodi
```

Create the launch script and make it executable:

```
echo "kodi-standalone" > /home/pi/RetroPie/roms/kodi/kodi.sh
chmod +x /home/pi/RetroPie/roms/kodi/kodi.sh
```

Type `emulationstation` to go back into EmulationStation, and Kodi should be there as its own system. 

## Adding a VPN

Install dependencies:

```
sudo apt update
sudo apt install openvpn psmisc
```

From the terminal in RetroPie Download Addon:

```
wget https://github.com/Zomboided/repository.zomboided.plugins/releases/download/1.0.0/repository.zomboided.plugins-1.0.0.zip
```

In Kodi:

- Go to addons
- Select the open box icon
- Install from Zip
- Navigate to where you just downloaded the repo
- Install the repository
- Go back to addons
- Select the open box icon
- Now select install from repository
- Select VPN Manager for OpenVPN

Then follow the directions to configure your VPN provider. If it's unsupported (like NordVPN) you can set it to user defined, manually import the server configurations, and set them up as their own source in the Kodi file manager so they are accessible to the addon. 

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
