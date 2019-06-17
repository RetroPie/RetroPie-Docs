# Splashscreen Menu

The Splash Screen Menu can be accessed from the RetroPie Menu in EmulationStation or through the setup script under option 3 - it is only available on the Raspberry Pi.

![splashes](https://cloud.githubusercontent.com/assets/10035308/16179686/82420dcc-362a-11e6-963d-13d4471f813e.png)

- **Choose RetroPie Splashscreen:** This option allows you to choose a splashscreen that has been installed on RetroPie by default. See the gallery of images [**HERE**](https://github.com/RetroPie/retropie-splashscreens/wiki)

- **Choose Own Splashscreen:** Once you've opened up the splashscreen menu in the setup script at least once a folder will be created in `/home/pi/RetroPie/splashscreens` you can also access this splashscreens folder from [samba shares](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#samba-shares-needs-an-active-internet-connection) once its created. (**Note you may need to install or restart samba shares from the setup script for the splashscreens folder to show up over samba shares**) Make sure you create a new folder to place your splashscreen in- for example:  `/home/pi/RetroPie/splashscreens/video/yourvideo.mp4`

- **Enable Custom Splashscreen On Boot:** This is pretty self explanatory- if you've disabled splashscreens the you select this to re-enable splashscreens on boot.

- **Disable Custom Splashscreen On Boot:** Select this option to disable splashscreens on boot

- **Use Default Splashscreen:** This makes the blue retropie splashscreen the default splash screen (the splashscreen you see the first time it boots up)

- **Manually Edit Splashscreen List:** You can edit the splashscreen.list manually to point to multiple images to be played as a slideshow (you'll use tab to get out of edit mode)

- **Update RetroPie Splashscreens:** This updates the latest default splashscreens included with the RetroPie image from [retropie-splashscreens repo](https://github.com/RetroPie/retropie-splashscreens)

- **Download RetroPie-Extra Splashscreens:** You can download a mass of user created splashscreens from the [retropie-splashscreens-extra](https://github.com/HerbFargus/retropie-splashscreens-extra) repository. Splashes will be placed in `/home/pi/RetroPie/splashscreens/retropie-extra`

## Video Splash Screens

A few notes:

- you add the video to a folder just like you would a regular splashscreen image and select that folder from the splashscreen menu as described above

- for best results use .mp4 filetype. If you have a video in another format and it isn't working try converting it with a program like [vlc](http://www.videolan.org/vlc/index.html) or [handbrake](https://handbrake.fr/) I've found that h.264 is a good codec and .mp4 is a good filetype- but others may also work.
 
- For a raspberry pi 1 a good video time is ~20-40 seconds, for the rpi 2 a good video time is ~5-10 seconds. It will vary depending on the number of roms and systems you have installed on RetroPie. 

- OMXPlayer is coded to play on the highest layer of the framebuffer while EmulationStation loads up, so you no longer have to worry about EmulationStation cutting in front of your video before the video finishes. This way your video can be as long or as short as you want it to be.

## Plymouth Splash Screen

This is for more advanced users.

Plymouth is more integrated into the boot process than OMX player. It won't have audio and takes more effort to code

Plymouth should already be installed on the full Raspbian, but if you're using Raspian Lite then you'll need to go through the following steps to enable it:

```
sudo apt-get install plymouth plymouth-themes
```

Install Raspberry Pi Foundation Pixel splash

```
sudo apt-get install pix-plym-splash
```

Enable in /boot/cmdline.txt

add `quiet splash plymouth.ignore-serial-consoles` on the same line

and remove `plymouth.enable=0` if you're using retropie

You can see [HERE](FAQ#how-do-i-hide-the-boot-text) on more info on how to hide the boot text

### Using Plymouth

#### List Themes:

```
plymouth-set-default-theme --list
```

#### Set Default Theme:

```
sudo plymouth-set-default-theme yourtheme
```

#### Test Theme:

```
sudo plymouthd
sudo plymouth --show-splash
sudo plymouth quit 
```

If you want a little more debugging while testing:
```
sudo plymouthd --debug --debug-file=/tmp/plymouth-debug-out ; sudo plymouth --show-splash ; for ((I=0;I<10;I++)); do sleep 1 ; sudo plymouth --update=event$I ; done ;sudo  plymouth --quit
```

#### Adding a new plymouth theme

Add your new themes to:

```
/usr/share/plymouth/themes/
```

You'll want to disable the splashscreen from the setup script if you don't want plymouth conflicting with the default retropie splash integration.

More plymouth themes can be found [HERE](https://github.com/HerbFargus/plymouth-themes)

If you want to install them directly through the terminal you can run these commands:

```
sudo wget https://github.com/HerbFargus/plymouth-themes/archive/master.zip -O plymouththemes.zip
unzip plymouththemes.zip
sudo cp -a plymouth-themes-master/. /usr/share/plymouth/themes/
rm plymouththemes.zip
rm -r plymouth-themes-master/
```

Guide on Plymouth Scripting [HERE](http://brej.org/blog/?p=158)