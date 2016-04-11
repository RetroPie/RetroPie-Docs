![](http://www.grandrapidsdevs.com/wp-content/uploads/2015/06/kodiLogo.png)
***

_Kodi is a Home Media Server (basically your own personal netflix) formerly known as XBMC. Kodi is currently an experimental build that can be installed from the experimental menu of the setup script._

***
## General Information

See here for more info: http://kodi.tv/

See [here](http://blog.petrockblock.com/forums/topic/kodi-tab-in-emulationstation/) for more information on setting up Kodi

## Installation

Visit the RetroPie-Setup Screen, select Experimental Packages, and select Kodi.  Installation can take 15 minutes.  After installation, you will be able to go to the Ports section and view Kodi as an option.

RetroPie currently installs Kodi 16 Jarvis

## Recommended Smartphone App to control Kodi: [Yatse](http://yatse.tv/redmine/projects/yatse)

![](http://kodi.wiki/images/3/3c/Yatse_Holo_1.png)

### Kodi as its own system instead of in ports

The first method here is a cleaner method that wont mess with the RetroPie setup script updates (note that in the future you will have to manually update the es_systems.cfg in .emulationstation as they arent overwritten on updates from RetroPie). Once you've installed kodi from the experimental menu of the setup script, Drop into a terminal with f4 or access the pi over [SSH](https://github.com/retropie/retropie-setup/wiki/ssh)

create an es_systems.cfg file so that kodi will show up in emulationstation

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
    <command>%ROM%</command>
    <platform>kodi</platform>
    <theme>kodi</theme>
  </system>
```

save you changes with `ctrl+x` , `y` , `enter`

Then make a kodi rom directory

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

**For more advanced users the following is another method that you can use to set kodi as its own system.**

To add the code you have to first make a backup of the current `kodi.sh` module in `/home/pi/RetroPie-Setup/scriptmodules/ports` and then replace the contents with the following code block, you will then be able to install kodi from the experimental menu of the setup script like you normally would. 

Note that you will need elevated priveleges to make any edits. You can edit the file directly with sudo over SSH or you can see [HERE](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-cant-i-ssh-as-root-anymore) on how to log in as user ROOT in winscp. Note that by editing the aforementioned file you will need to git stash your changes or delete the file before you update the setup script again (after update the setup script the original kodi.sh will be restored)

If you want to setup Kodi as its own system instead of in ports replace the configure function with this:

```
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

### Joypad Support

The latest Kodi module (Kodi 16) includes joypad support by default: add your custom keymap to `/home/pi/.kodi/userdata/keymaps/joystick.xml`

You can see what your joystick name is with `cat /proc/bus/input/devices`

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

#### Retrolink Snes

Template: `retrolink.xml`

```

<?xml version="1.0" encoding="UTF-8"?>
<keymap>
  <global>
    <joystick name="USB Gamepad "> <!--Retrolink SNES-->
      <button id="2">Select</button><!--A-->
      <button id="3">Back</button><!--B-->
      <button id="1">Stop</button><!--X-->
      <button id="4">ContextMenu</button><!--Y-->
      <button id="5">Rewind</button><!--L-->
      <button id="6">FastForward</button><!--R-->
      <button id="9">Info</button><!--SELECT-->
      <button id="10">PlayPause</button><!--START-->
      <button id="9,10">Quit</button><!--SELECT+START-->
      <axis id="1" limit="+1">Right</axis><!--RIGHT-->
      <axis id="1" limit="-1">Left</axis><!--LEFT-->
      <axis id="2" limit="-1">Up</axis><!--UP-->
      <axis id="2" limit="+1">Down</axis><!--DOWN-->
    </joystick>
  </global>
</keymap>
```

#### Ibuffalo 

Template: `ibuffalo.xml`

```
<?xml version="1.0" encoding="UTF-8"?>
<keymap>
  <global>
    <joystick name="USB,2-axis 8-button gamepad "><!--iBuffalo SNES-->
      <button id="1">Select</button><!--A-->
      <button id="2">Back</button><!--B-->
      <button id="3">Stop</button><!--X-->
      <button id="4">ContextMenu</button><!--Y-->
      <button id="5">Rewind</button><!--L-->
      <button id="6">FastForward</button><!--R-->
      <button id="7">Info</button><!--SELECT-->
      <button id="8">PlayPause</button><!--START-->
      <button id="7,8">Quit</button><!--SELECT+START-->
      <axis id="1" limit="+1">Right</axis><!--RIGHT-->
      <axis id="1" limit="-1">Left</axis><!--LEFT-->
      <axis id="2" limit="-1">Up</axis><!--UP-->
      <axis id="2" limit="+1">Down</axis><!--DOWN-->
    </joystick>
  </global>
</keymap>
```

#### Xbox 360:

For Xbox controls see the following and adapt for your version of controller
- [**HERE**](http://kodi.wiki/view/Xbox_360_Wireless_Controller) 
- [Example 1](https://github.com/xbmc/xbmc/blob/Eden/system/keymaps/joystick.Microsoft.Xbox.360.Controller.xml)
- [Example 2](http://pastebin.com/ZiNyYEZV)
- [Example 3](https://gitlab.com/ember-dev/kodi/blob/436c61114dfbf7ec0667873428da0812de3c6954/system/keymaps/joystick.Microsoft.Xbox.360.Controller.xml)

Template: `xbox360.xml`
```
<!--
# This file is for use with a XBOX 360 Controller
# To use please replace the joystickname with the one you find 
# in your xbmclogfile
#
# Be careful:
# I generally encourage people to use the analog stick
# The DPad gets remapped from its default (up, down, etc) to various
# actions (delete, queue, etc.)
# The AnalogStick should be used for browsing.
#
# The Buttons of the controller are mapped as the following list shows:
#button id 1 = A
#button id 2 = B
#button id 3 = X
#button id 4 = Y
#button id 5 = Left Shoulder Button
#button id 6 = Right Shoulder Button
#button id 7 = back
#button id 8 = start
#button id 9 = left stick button
#button id 10 = right stick button
#
#
#axis limit="-1" id="2"   Up on left stick
#axis limit="+1" id="2"   Down on left stick
#axis limit="-1" id="1"   Left on left stick
#axis limit="+1" id="1"   Right on left stick
#
#axis limit="-1" id="3"   LeftTrigger
#axis limit="+1" id="3"   RightTrigger
#
#axis limit="-1" id="4"   Up on right stick
#axis limit="+1" id="4"   Down on right stick
#axis limit="-1" id="5"   Left on right stick
#axis limit="+1" id="5"   Right on right stick
#
#
#hat id="1" position="up"   Up on DPAD
#hat id="1" position="right"   Right on DPAD
#hat id="1" position="down"   Down on DPAD
#hat id="1" position="left"   Left on DPAD
#
#
-->
<keymap>
  <global>
    <joystick name="Xbox Gamepad (userspace driver)">
      <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
      <button id="1">Select</button><!--A-->
      <button id="2">ParentDir</button><!--B-->
      <button id="3">FullScreen</button><!--X-->
      <button id="4">ContextMenu</button><!--Y-->
      <button id="5">Stop</button><!--LEFT SHOULDER BUTTON-->
      <button id="6">Pause</button><!--RIGHT SHOULDER BUTTON-->
      <button id="7">PreviousMenu</button><!--BACK-->
      <button id="7,8">Quit</button><!--BACK+START-->
      <button id="8">XBMC.ActivateWindow(settings) </button><!--START-->
      <button id="9">Playlist</button><!--LEFT ANALOGUE STICK BUTTON-->
      <button id="10">XBMC.UpdateLibrary(video)</button><!--RIGHT ANALOGUE STICK BUTTON-->

      <hat id="1" position="up">Up</hat><!--DPAD UP-->
      <hat id="1" position="down">Down</hat><!--DPAD DOWN-->
      <hat id="1" position="right">Right</hat><!--DPAD RIGHT-->
      <hat id="1" position="left">Left</hat><!--DPAD LEFT-->

      <axis limit="-1" id="2">Up</axis><!--LEFT ANALOGUE UP-->
      <axis limit="+1" id="2">Down</axis><!--LEFT ANALOGUE DOWN-->
      <axis limit="+1" id="1">Right</axis><!--LEFT ANALOGUE RIGHT-->
      <axis limit="-1" id="1">Left</axis><!--LEFT ANALOGUE LEFT-->
	  
      <axis limit="-1" id="4">VolumeUp</axis><!--RIGHT ANALOGUE UP-->
      <axis limit="+1" id="4">VolumeDown</axis><!--RIGHT ANALOGUE DOWN-->
      <axis limit="-1" id="5">AnalogSeekBack</axis><!--RIGHT ANALOGUE LEFT-->
      <axis limit="+1" id="5">AnalogSeekForward</axis> <!--RIGHT ANALOGUE RIGHT-->

      <axis limit="-1" id="3">ScrollDown</axis><!--LEFT TRIGGER-->
      <axis limit="+1" id="3">ScrollUp</axis><!--RIGHT TRIGGER-->
    </joystick>
  </global>
<Home>
 <joystick name="Xbox Gamepad (userspace driver)">
 <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
    <button id="8">XBMC.ActivateWindow(shutdownmenu)</button>
 </joystick>
</Home>
  <FullscreenVideo>
    <joystick name="Xbox Gamepad (userspace driver)">
    <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
      <button id="1">Pause</button>
      <button id="2">Stop</button>
      <button id="3">FullScreen</button>
      <button id="4">SkipNext</button>
      <button id="5">CodecInfo</button>
      <button id="6">ShowTime</button>
      <button id="7">Info</button>
      <button id="8">OSD</button>
      <axis limit="-1" id="3">AnalogFastForward</axis>
      <axis limit="+1" id="3">AnalogRewind</axis>
      <hat id="1" position="up">BigStepForward</hat>
      <hat id="1" position="right">StepForward</hat>
      <hat id="1" position="down">BigStepBack</hat>
      <hat id="1" position="left">StepBack</hat>
    </joystick>
  </FullscreenVideo>
 <FullscreenInfo>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
      <button id="7">Close</button> 
      <button id="2">Close</button> 
    </joystick>
  </FullscreenInfo>
 <PlayerControls>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="8">Close</button>
     <button id="7">Close</button> 
     <button id="2">Close</button>
   </joystick>
 </PlayerControls>
 <MusicOSD>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button>  
     <button id="2">Close</button>
   </joystick>
 </MusicOSD>
 <VisualisationSettings>
  <joystick name="Xbox Gamepad (userspace driver)">
  <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
   <button id="7">Close</button>  
   <button id="2">Close</button> 
  </joystick>
 </VisualisationSettings>
 <VisualisationPresetList>
  <joystick name="Xbox Gamepad (userspace driver)">
  <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
   <button id="7">Close</button>  
   <button id="2">Close</button>
  </joystick>
 </VisualisationPresetList>
 <SlideShow>
  <joystick name="Xbox Gamepad (userspace driver)">
  <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
   <button id="1">Pause</button> 
   <button id="2">Stop</button> 
  </joystick>
 </SlideShow>
 <SelectDialog>
  <joystick name="Xbox Gamepad (userspace driver)">
  <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
   <button id="7">Close</button> 
   <button id="2">Close</button> 
  </joystick>
 </SelectDialog>
 <VideoOSD>
  <joystick name="Xbox Gamepad (userspace driver)">
  <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
   <button id="8">Close</button> 
   <button id="7">Close</button>  
   <button id="2">Close</button>
  </joystick>
 </VideoOSD>
 <OSDVideoSettings>
  <joystick name="Xbox Gamepad (userspace driver)">
  <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
   <button id="7">Close</button>  
   <button id="2">Close</button>
   <button id="8">Close</button> 
  </joystick>
 </OSDVideoSettings>
 <OSDAudioSettings>
  <joystick name="Xbox Gamepad (userspace driver)"> 
  <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
   <button id="7">Close</button>  
   <button id="2">Close</button>
  </joystick>
 </OSDAudioSettings>
 <VideoBookmarks>
  <joystick name="Xbox Gamepad (userspace driver)"> 
  <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
   <button id="7">Close</button>  
   <button id="2">Close</button>
  </joystick>
 </VideoBookmarks>
 <ContextMenu>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button> 
     <button id="2">Close</button>
     <button id="8">Close</button> 
   </joystick>
 </ContextMenu>
 <AddonInformation>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button> 
     <button id="2">Close</button>
   </joystick>
 </AddonInformation>
 <AddonSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button> 
     <button id="2">Close</button>
   </joystick>
 </AddonSettings>
 <TextViewer>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button> 
     <button id="2">Close</button>
  </joystick>
 </TextViewer>
 <MyPicturesSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </MyPicturesSettings>
 <MyProgramsSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
    <button id="7">PreviousMenu</button> 
    <button id="2">PreviousMenu</button>
   </joystick>
 </MyProgramsSettings>
 <MyWeatherSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </MyWeatherSettings>
 <MyMusicSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </MyMusicSettings>
 <SystemSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </SystemSettings>
 <MyVideosSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </MyVideosSettings>
 <NetworkSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </NetworkSettings>
 <AppearanceSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </AppearanceSettings>
 <Profiles>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </Profiles>
 <systeminfo>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </systeminfo>
 <shutdownmenu>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="8">Close</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </shutdownmenu>
 <submenu>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">PreviousMenu</button> 
     <button id="2">PreviousMenu</button>
   </joystick>
 </submenu>
 <MusicInformation>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button> 
     <button id="2">Close</button>
   </joystick>
 </MusicInformation>
 <MovieInformation>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button> 
     <button id="2">Close</button>
   </joystick>
 </MovieInformation>
 <LockSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button> 
     <button id="2">Close</button>
   </joystick>
 </LockSettings>
 <ProfileSettings>
   <joystick name="Xbox Gamepad (userspace driver)">
   <altname>Controller (Xbox 360 Wireless Receiver for Windows)</altname>
     <button id="7">Close</button> 
     <button id="2">Close</button>
   </joystick>
 </ProfileSettings>
</keymap>
```

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