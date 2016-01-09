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

## Kodi 15.2 on Raspbian Jessie (as it's own system instead of in ports)

To compile Kodi 15 you can just replace the following in 

`/home/pi/RetroPie-Setup/scriptmodules/ports/kodi.sh`

and then reinstall kodi from the experimental menu of the [RetroPie Setup Script](Updating-RetroPie)

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
rp_module_flags="nobin !odroid"

function install_kodi() {
    # remove old repository - we will use Kodi from the Raspbian repositories
    rm -f /etc/apt/sources.list.d/mene.list
    aptInstall kodi
}

function configure_kodi() {
    echo 'SUBSYSTEM=="input", GROUP="input", MODE="0660"' > /etc/udev/rules.d/99-input.rules

    mkRomDir "kodi"

    cat > "$romdir/kodi/Kodi.sh" << _EOF_
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "kodi-standalone" "kodi"
_EOF_

    chmod +x "$romdir/kodi/Kodi.sh"

    setESSystem 'Kodi' 'kodi' '~/RetroPie/roms/kodi' '.sh .SH' '%ROM%' 'pc' 'kodi'
}
```

# Kodi on Raspbian Wheezy
## Black Screen Freeze Fix

If you find yourself having troubles with your screen freezing when you exit kodi, you can replace the code in `/roms/ports/kodi.sh` with
```
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
```
(note there may be some issues with the framebuffer but its the only functioning fix at the moment short of compiling Kodi 15)

### Kodi 15

To compile Kodi 15 you can just replace the following in 

`/home/pi/RetroPie-Setup/scriptmodules/ports/kodi.sh`

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

# http://www.gtkdb.de/index_36_2176.html
rp_module_id="kodi"
rp_module_desc="Install Kodi"
rp_module_menus="4+"
rp_module_flags="nobin"

function depends_kodi() {
    echo "deb http://archive.mene.za.net/raspbian wheezy contrib unstable" > /etc/apt/sources.list.d/mene.list
    apt-key adv --keyserver keyserver.ubuntu.com --recv-key 5243CDED
}

function install_kodi() {
    aptInstall kodi
}

function configure_kodi() {
    echo 'SUBSYSTEM=="input", GROUP="input", MODE="0660"' > /etc/udev/rules.d/99-input.rules

    mkRomDir "kodi"

    cat > "$romdir/kodi/Kodi.sh" << _EOF_
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "kodi-standalone" "kodi"
_EOF_

    chmod +x "$romdir/kodi/Kodi.sh"

    setESSystem 'Kodi' 'kodi' '~/RetroPie/roms/kodi' '.sh .SH' '%ROM%' 'pc' 'kodi'
}
```