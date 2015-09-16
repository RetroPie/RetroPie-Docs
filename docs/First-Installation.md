# RetroPie 3.0

Congratulations! You have discovered the wonderful world of RetroPie- your entire childhood is within reach! This page is for people just getting started on RetroPie 3.0. You can install RetroPie manually but for simplicity's sake this page will focus on installing the RetroPie SD card image. This page will give you the very basics to get you up and running from a blank SD card to first boot into Emulationstation.

If you hate reading then see this video. Otherwise read on! 

<a href="https://www.youtube.com/watch?v=WAyDUQoxMKY
" target="_blank"><img src="https://i.ytimg.com/vi_webp/WAyDUQoxMKY/mqdefault.webp" 
alt="Configuration Video" width="300" height="190" border="10" /></a>

## Hardware Needed:

 * Raspberry Pi (A, A+, B, B+,) or for best results: **Raspberry Pi 2 Model B**
 * Raspberry Pi Case (optional but recommended)
 * MicroSD Card (see compatible SD card list [**here**)](http://elinux.org/RPi_SD_cards)
 * MicroSD Card Reader (For installing retropie from your computer)
 * HDMI cable or 4 Pole RCA to 3.5mm Cable (HDMI works best)
 * Television or Computer Monitor- really any screen with HDMI or RCA ports
 * Wifi Dongle or Ethernet Cable (Wifi Dongle is more convenient- see compatible list [**here**)](http://elinux.org/RPi_USB_Wi-Fi_Adapters)
 * 5V 2A Micro USB Power Supply
 * USB Keyboard and Mouse (to get things set up or you can use SSH)
 * USB Game Controller of your choice (or you can get the [Control Block](http://blog.petrockblock.com/2014/12/29/controlblock-power-switch-and-io-for-the-raspberry-pi/) to use original controllers)

## Installation

### SD Images

There are currently two versions of RetroPie 3.0. There is one version for Raspberry Pi 1 (Model A, A+, B, B+) and there is a version for Raspberry Pi 2. Download the SD image for your version of Raspberry Pi:

**[Raspberry Pi 1](http://blog.petrockblock.com/retropie/retropie-downloads/retropie-project-sd-card-image-for-raspberry-pi-1-beta/)**

**[Raspberry Pi 2](http://blog.petrockblock.com/retropie/retropie-downloads/retropie-project-sd-card-image-for-raspberry-pi-2-beta/)**

(If these links become outdated see the downloads page [here](http://blog.petrockblock.com/retropie/retropie-downloads/).)

If you are unsure which version of Raspberry Pi you have there is an easy way to check:

Rpi 1= 1 raspberry when the pi boots up

Rpi 2= 4 raspberries when the pi boots up

### Extract

Once you have downloaded your SD card image you need to extract it using a program such as [7-Zip](http://www.7-zip.org/). You will extract the downloaded .gz file and the extracted file will be a .img file.

### Install 3.0 Image on SD Card

For Windows you can use a program called [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/) or for mac you can use [Apple Pi Baker](http://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/) to install the RetroPie 3.0 SD image on your MicroSD card. (You may need a MicroSD card reader to plug it into your computer) 

# Configurations

## Controller Configurations

When you first boot up you will be welcomed with the following screen- unlike previous versions of retropie, this menu will configure your controls for both Emulationstation and RetroArch Emulators:

![welcomescreen](https://cloud.githubusercontent.com/assets/10035308/9140482/cf42f25c-3cee-11e5-8f91-c1fc1c57175c.png)

Hold down any button on your keyboard or gamepad and the name will appear at the bottom and then open up into a configuration menu:

![welcomescreengamepadname](https://cloud.githubusercontent.com/assets/10035308/9140505/f5c19e38-3cee-11e5-965e-0e4e85ddaf56.png)

Follow the onscreen instructions to configure your gamepad- if you run out of buttons just hold down a button to skip each unused button.

![welcomescreengamepadconfigure](https://cloud.githubusercontent.com/assets/10035308/9140518/0263b9c8-3cef-11e5-922f-42f790f3be91.png)

See the following diagrams for reference:

![Super Nintendo Controller](https://cloud.githubusercontent.com/assets/10035308/7110174/0f2fdb54-e16a-11e4-8f3d-37bdca8f1ddf.png)

![Xbox 360 Controller](https://cloud.githubusercontent.com/assets/10035308/7110173/0f2ea784-e16a-11e4-9c6f-5fe7c594b05a.png)

![PlayStation 3 Controller](https://cloud.githubusercontent.com/assets/10035308/7111199/e29365ec-e179-11e4-87b4-f00685661d7e.png)

### Default Hotkeys

Hotkeys | Action
| :---: | :---: |
Select+Start | Exit
Select+Right Shoulder | Save
Select+Left Shoulder | Load
Select+Right | Input State Slot Increase
Select+Left | Input State Slot Decrease 
Select+X | RGUI Menu
Select+B | Reset

If you wish to put in configurations for multiple controllers you can do so from the start menu of emulationstation. For more details on manual controller configurations see this page [Here](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

For those of you that are interested, the retroarch controller config that is created after you've followed the aforementioned steps is located in 
```
/opt/retropie/configs/all/retroarch-joypads
``` 
the following is an example of a snes controller config- your configurations may be a bit different.

```
input_device = "USB gamepad           "
input_driver = "udev"
input_r_btn = "5"
input_save_state_btn = "5"
input_start_btn = "9"
input_exit_emulator_btn = "9"
input_l_btn = "4"
input_load_state_btn = "4"
input_up_axis = "-1"
input_a_btn = "1"
input_b_btn = "2"
input_reset_btn = "2"
input_down_axis = "+1"
input_right_axis = "+0"
input_state_slot_increase_axis = "+0"
input_x_btn = "0"
input_menu_toggle_btn = "0"
input_select_btn = "8"
input_enable_hotkey_btn = "8"
input_y_btn = "3"
input_left_axis = "-0"
input_state_slot_decrease_axis = "-0"
```

## EmulationStation

**When you first see EmulationStation you may wonder why you don't see systems like the SNES or Game Boy- worry not- they are installed on the system, roms just need to be added to their respective rom folders before they will become visible. Transferring roms are described in the following steps.**

## Expand File System

Once your controller is set up you'll need to make a few configurations before you can transfer your ROMs over go to the RetroPie Menu:

![retropiemenu](https://cloud.githubusercontent.com/assets/10035308/9140677/2beba548-3cf0-11e5-8254-d8329b0f35b8.png)

You'll want to select raspberry Pi configuration tool raspi-config (This allows your sd card to use all its memory rather than the small partition it was released with.)

![retropiemenuraspiconfig](https://cloud.githubusercontent.com/assets/10035308/9140687/3be5a282-3cf0-11e5-9f48-58d23552bcda.png)

It will open up into the following, if using a gamepad **Press right on the dpad until select is highlighted** and choose select:

![raspi-config](https://cloud.githubusercontent.com/assets/10035308/9140867/856bb85a-3cf1-11e5-8697-04f60ecf8563.png)

You will get this message:

![raspi-config2](https://cloud.githubusercontent.com/assets/10035308/9140889/ad8879c2-3cf1-11e5-8d77-7c81af7dba16.png)

Press right and choose finish

![raspi-config3](https://cloud.githubusercontent.com/assets/10035308/9140900/dcfdf556-3cf1-11e5-978c-e5d620ab98fc.png)

And then reboot your raspberry pi

![raspi-config4](https://cloud.githubusercontent.com/assets/10035308/9140912/fc047e3e-3cf1-11e5-9463-f574e0efc38a.png)

## Configuring Wifi

If you wish to use a wifi dongle to transfer roms over the network rather than a USB stick or Ethernet cable you'll need to setup your wifi- which can also be done from the Retropie menu in emulationstation:

![retropiemenuwifi](https://cloud.githubusercontent.com/assets/10035308/9141387/7ed23ec0-3cf5-11e5-9944-a8f7870cc6c0.png)

It will open into this menu:

![wifi1](https://cloud.githubusercontent.com/assets/10035308/9141521/96ceb142-3cf6-11e5-9ba4-2b23a8b52480.png)

Choose your SSID from a list:

![wifi2](https://cloud.githubusercontent.com/assets/10035308/9141549/cd763742-3cf6-11e5-836e-a257e888bfb2.png)

Type your Wifi Password (You may need to wait a bit after you finish for the configurations to save)

![wifi3](https://cloud.githubusercontent.com/assets/10035308/9141565/f2252120-3cf6-11e5-9eeb-e9ad88e77977.png)

After it's done configuring you should see your wifi info in the original menu:

![wifiinfo](https://cloud.githubusercontent.com/assets/10035308/9141742/226f50de-3cf8-11e5-8b6b-328f2110e655.png)

For more WiFi configuration options see this page [HERE](https://github.com/RetroPie/RetroPie-Setup/wiki/Setting-Up-Wifi)

## Transferring Roms

There are three main methods of transferring roms: 

### USB
 * first create a folder called `retropie` on your USB stick
 * plug it into the pi and wait for it to finish blinking
 * pull the USB out and plug it into a computer
 * add the roms to their respective folders (in the retropie/roms folder)
 * plug it back into the raspberry pi
 * wait for it to finish blinking
 * refresh emulationstation by pressing F4, or choosing quit from the start menu

see this video for reference:

<a href="https://www.youtube.com/watch?v=OYMoxvbkYD4
" target="_blank"><img src="https://i.ytimg.com/vi_webp/OYMoxvbkYD4/mqdefault.webp" 
alt="Configuration Video" width="300" height="190" border="10" /></a>

### FTP (needs an active internet connection) 
* Wired (needs ethernet cable)
* Wireless (needs wifi dongle)
There are many FTP programs out there, for windows many people use [WinSCP](https://winscp.net/eng/download.php) for mac you can use something like [Cyberduck](https://cyberduck.io/?l=en)

![ftp](https://cloud.githubusercontent.com/assets/10035308/9144892/68994618-3d0d-11e5-8db0-2991f9068115.png)

You can also log in as root if you wish to change more files than just the roms, but you first need to enable the root password by typing `sudo passwd root` into the terminal and choosing a new root password.

### Samba Shares (needs an active internet connection)

- if on windows type \\\RETROPIE into the computer folder. You can also replace RETROPIE with your Raspberry Pi's IP address

![samba](https://cloud.githubusercontent.com/assets/10035308/9141308/edee8b52-3cf4-11e5-8bf3-73f8c27f99fb.png)


## PLAY!

After you've added your roms you can refresh emulationstation by pressing F4, or choosing quit from the start menu, or rebooting your pi with `sudo reboot`. 

HAVE FUN!

- see the rest of the [wiki](https://github.com/RetroPie/RetroPie-Setup/wiki) for more detailed info on individual emulators, advanced settings etc. If you still can't figure it out, the RetroPie community is very helpful on the [forum](http://blog.petrockblock.com/forums/forum/retropie-project-forum/).