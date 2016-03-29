![](http://www.grandrapidsdevs.com/wp-content/uploads/2015/06/kodiLogo.png)
***

_Kodi is a Home Media Server (basically your own personal netflix) formerly known as XBMC. Kodi is currently an experimental build that can be installed from the experimental menu of the setup script._

***
## General Information

See here for more info: http://kodi.tv/

See [here](http://blog.petrockblock.com/forums/topic/kodi-tab-in-emulationstation/) for more information on setting up Kodi

## Installation

Visit the RetroPie-Setup Screen, select Experimental Packages, and select Kodi.  Installation can take 15 minutes.  After installation, you will be able to go to the Ports section and view Kodi as an option.

## Recommended Smartphone App to control Kodi: [Yatse](http://yatse.tv/redmine/projects/yatse)

![](http://kodi.wiki/images/3/3c/Yatse_Holo_1.png)

### Kodi 16 (ONLY ON RASPBIAN JESSIE, TEST AT OWN RISK)

To add the code you have to first make a backup of the current `kodi.sh` module in `/home/pi/RetroPie-Setup/scriptmodules/ports` and then replace the contents with the following code block, you will then be able to install kodi 16 from the experimental menu of the setup script like you normally would. 

Note that you will need elevated priveleges to make any edits. You can edit the file directly with sudo over SSH or you can see [HERE](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-cant-i-ssh-as-root-anymore) on how to log in as user ROOT in winscp. Note that by editing the aforementioned file you will need to git stash your changes or delete the file before you update the setup script again (after update the setup script the original kodi.sh will be restored)

```
#!/usr/bin/env bash

# This file is part of The RetroPie Project
# 
# The RetroPie Project is the legal property of its developers, whose names are
# too numerous to list here. Please refer to the COPYRIGHT.md file distributed with this source.
# 
# See the LICENSE.md file at the top-level directory of this distribution and 
# at https://raw.githubusercontent.com/RetroPie/RetroPie-Setup/master/LICENSE.md
#

rp_module_id="kodi"
rp_module_desc="Kodi - Open source home theatre software"
rp_module_menus="4+"
rp_module_flags="nobin !mali"

function depends_kodi() {
 # add repository to install Kodi 16 (Jarvis)
    echo "deb http://pipplware.pplware.pt/pipplware/dists/jessie/main/binary /" > /etc/apt/sources.list.d/pipplware_jessie.list
    wget -O - http://pipplware.pplware.pt/pipplware/key.asc | sudo apt-key add -
}

function install_kodi() {
    # remove old repository - we will use Kodi from the Raspbian repositories
    rm -f /etc/apt/sources.list.d/mene.list
    aptInstall kodi
}

function configure_kodi() {
    addPort "$md_id" "kodi" "Kodi" "kodi-standalone"

    if [[ ! -f /etc/udev/rules.d/99-input.rules ]]; then
        echo 'SUBSYSTEM=="input", GROUP="input", MODE="0660"' > /etc/udev/rules.d/99-input.rules
    fi

    # we launch directly rather than from roms section now
    rm -f "$romdir/ports/Kodi.sh"
    rm /etc/apt/sources.list.d/pipplware_jessie.list
}
```
The module above includes joypad support by default: add your custom keymap to `/home/pi/.kodi/userdata/keymap/joystick.xml`

You can see what your joystick name is with `cat /proc/bus/input/devices`

Example `joystick.xml`
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

Ibuffalo Template: `ibuffalo.xml`

```
<?xml version="1.0" encoding="UTF-8"?>
<keymap>
  <global>
    <joystick name="USB,2-axis 8-button gamepad  "> <!-- iBuffalo SNES -->
      <button id="1">Select</button><!-- A -->
      <button id="2">Back</button><!-- B -->
	  <button id="3">Stop</button><!-- X -->
	  <button id="4">ContextMenu</button><!-- Y -->
	  <button id="5">Rewind</button><!-- L -->
	  <button id="6">FastForward</button><!-- R -->
	  <button id="7">Info</button><!-- SELECT -->
	  <button id="8">PlayPause</button><!-- START -->
      <axis id="1" limit="+1">Right</axis>
      <axis id="1" limit="-1">Left</axis>
      <axis id="2" limit="-1">Up</axis>
      <axis id="2" limit="+1">Down</axis>
    </joystick>
  </global>
</keymap>
```

For Xbox controls see [**HERE**](http://kodi.wiki/view/Xbox_360_Wireless_Controller) and [HERE](https://github.com/xbmc/xbmc/blob/Eden/system/keymaps/joystick.Microsoft.Xbox.360.Controller.xml)

```
OLD CONFIGS:

# Kodi on Raspbian Wheezy
## Black Screen Freeze Fix

If you find yourself having troubles with your screen freezing when you exit kodi, you can replace the code in `/roms/ports/kodi.sh` with

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