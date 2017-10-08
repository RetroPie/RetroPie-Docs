# Splashcreen Menu

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
