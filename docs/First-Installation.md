![retropie-original-flat-outline](https://cloud.githubusercontent.com/assets/10035308/11428906/0300d80c-942e-11e5-8675-1e033d731d49.png)

|Version|
|---|
|3.7|
1. [Hardware](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#hardware-needed)
1. [Installation](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#installation)
1. [Controller Configuration](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#controller-configurations)
1. [Configure Wifi](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#configuring-wifi)
1. [Transferring Roms](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#transferring-roms)

Congratulations! You have discovered the wonderful world of RetroPie- your entire childhood is within reach! RetroPie is a combination of multiple projects including [RetroArch](http://www.libretro.com), [EmulationStation](http://www.emulationstation.org), and many others. 

This page is for people just getting started on RetroPie. The easiest way to install RetroPie is the SD image which is a ready to go system built upon top of the Raspbian OS - this is the method described in the following guide. Alternatively, advanced users can install RetroPie [manually](https://github.com/RetroPie/RetroPie-Setup/wiki/Manual-Installation). 

This guide will give you the very basics to get you up and running from a blank SD card to first boot into EmulationStation.

If you hate reading then see this video. Otherwise read on! 

<a href="https://youtube.com/watch?v=xvYX_7iRRI0
" target="_blank"><img src="https://i.ytimg.com/vi/xvYX_7iRRI0/maxresdefault.jpg" 
alt="Configuration Video" width="1280" height="400" border="10" /></a>

## Hardware Needed:

 * Raspberry Pi (A, A+, B, B+, 2, Zero, or 3) - for best performance use a **Raspberry Pi 3 Model B**
 * Raspberry Pi Case (optional but recommended)
 * MicroSD Card (see compatible SD card list [**here**)](http://elinux.org/RPi_SD_cards)
 * MicroSD Card Reader (For installing retropie from your computer)
 * HDMI cable or 4 Pole RCA to 3.5mm Cable (HDMI works best)
 * Television or Computer Monitor- really any screen with HDMI or RCA ports
 * Wifi Dongle or Ethernet Cable (Wifi is built into the Pi 3- see wifi dongle compatible list [**here**)](http://elinux.org/RPi_USB_Wi-Fi_Adapters)
 * 5V 2A Micro USB Power Supply (2.5A for pi 3)
 * USB Keyboard and Mouse (to get things set up or you can use [SSH](ssh))
 * USB Game Controller of your choice (or you can get the [Control Block](http://blog.petrockblock.com/2014/12/29/controlblock-power-switch-and-io-for-the-raspberry-pi/) to use original SNES controllers)

The simplest way to get most of these components is through a kit such as the [Canakit](http://www.amazon.com/CanaKit-Raspberry-Complete-Starter-9-Items/dp/B008XVAVAW). 

## Installation

### SD Images

There are currently two versions of RetroPie. There is one version for Raspberry Pi 1/Zero (Model A, A+, B, B+) and there is a version for Raspberry Pi 2/Raspberry Pi 3. 

Download the SD image for your version of Raspberry Pi from the following page:

**https://retropie.org.uk/download/**

If you are unsure which version of Raspberry Pi you have there is an easy way to check:

Rpi 1/Zero= 1 raspberry when the pi boots up

Rpi 2/Rpi 3= 4 raspberries when the pi boots up

If you get the error `Illegal Instruction`  when it boots, you picked the wrong SD image.

### Extract

Once you have downloaded your SD card image you need to extract it using a program such as [7-Zip](http://www.7-zip.org/). You will extract the downloaded **.gz** file and the extracted file will be a **.img** file.

### Install RetroPie Image on SD Card

To install the RetroPie SD image on your MicroSD card. (You may need a MicroSD card reader to plug it into your computer) 

1. For Windows you can use a program called [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/) 
2. For mac you can use [Apple Pi Baker](http://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/) 
3. For Linux you can use `dd` command or [Unetbootin](https://unetbootin.github.io/)

**Note** RetroPie is built on top of Raspbian (a linux based OS for the Raspberry Pi) and as such the partition on the SD card is EXT4 (a linux filesystem) which is not visible on windows systems, so the card will show up as a smaller size than usual and you wont be able to see everything on the card, but it is all there. You will be able to access the filesystem over the network as described in the transferring roms section below.

If you're updating from a previous version of retropie see [**HERE**](https://github.com/RetroPie/RetroPie-Setup/wiki/Updating-RetroPie)

# Configurations

## Controller Configurations

On first boot your filesystem will be expanded automatically, you will then be welcomed with the following screen- this menu will configure your controls for both Emulationstation and RetroArch Emulators:

![welcomescreen](https://cloud.githubusercontent.com/assets/10035308/9140482/cf42f25c-3cee-11e5-8f91-c1fc1c57175c.png)

Hold down any button on your keyboard or gamepad and the name will appear at the bottom and then open up into a configuration menu:

![welcomescreengamepadname](https://cloud.githubusercontent.com/assets/10035308/9140505/f5c19e38-3cee-11e5-965e-0e4e85ddaf56.png)

Follow the onscreen instructions to configure your gamepad- if you run out of buttons just hold down a button to skip each unused button. **When you get to OK press the button you have configured as "A"**.

![welcomescreengamepadconfigure](https://cloud.githubusercontent.com/assets/10035308/9140518/0263b9c8-3cef-11e5-922f-42f790f3be91.png)

If you wish to configure more than one controller, you can do so from the start menu of emulationstation. For more details on manual controller configurations see this page [Here](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration). See also [HERE](https://github.com/RetroPie/RetroPie-Setup/wiki#controller-configurations)

See the following diagrams for reference:

![Super Nintendo Controller](https://cloud.githubusercontent.com/assets/10035308/7110174/0f2fdb54-e16a-11e4-8f3d-37bdca8f1ddf.png)

![Xbox 360 Controller](https://cloud.githubusercontent.com/assets/10035308/7110173/0f2ea784-e16a-11e4-9c6f-5fe7c594b05a.png)

![PlayStation 3 Controller](https://cloud.githubusercontent.com/assets/10035308/7111199/e29365ec-e179-11e4-87b4-f00685661d7e.png)

### Default Hotkeys

Hotkeys enable you to press a combination of buttons to access functions such as saving, loading, and exiting emulators. The following chart shows the default hotkey combinations. By default, the hotkey is select so that means you hold down select while pressing another button to execute a command.

Hotkeys | Action
| :---: | :---: |
Select+Start | Exit
Select+Right Shoulder | Save
Select+Left Shoulder | Load
Select+Right | Input State Slot Increase
Select+Left | Input State Slot Decrease 
Select+X | RGUI Menu
Select+B | Reset

For those that are interested, the retroarch controller config that is created after you've followed the aforementioned steps is located in: 
```
/opt/retropie/configs/all/retroarch-joypads
``` 
the following is an example of a SNES controller config- your configurations may be a bit different.

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

| **Where are the systems?**|
| :---: | 
**When you first see EmulationStation you may wonder why you don't see systems like the SNES or Game Boy- worry not- they are installed on the system, roms just need to be added to their respective rom folders before they will become visible. Transferring roms are described in the following steps.**|
|![firstboot](https://cloud.githubusercontent.com/assets/10035308/12865816/d4c76dfa-cc74-11e5-9a1f-922a6d830d49.png)|
## Configuring Wifi

If you wish to use wifi to transfer roms over the network rather than a USB stick or Ethernet cable you'll need to setup your wifi- which can also be done from the Retropie menu in emulationstation:

![wifi](https://cloud.githubusercontent.com/assets/10035308/12865761/adc9f5c6-cc72-11e5-9b02-9e98b90bbd98.png)

It will open into this menu:

![wifi1](https://cloud.githubusercontent.com/assets/10035308/9141521/96ceb142-3cf6-11e5-9ba4-2b23a8b52480.png)

Choose your SSID from a list:

![wifi2](https://cloud.githubusercontent.com/assets/10035308/9141549/cd763742-3cf6-11e5-836e-a257e888bfb2.png)

Type your Wifi Password (You may need to wait a bit after you finish for the configurations to save)

![wifi3](https://cloud.githubusercontent.com/assets/10035308/9141565/f2252120-3cf6-11e5-9eeb-e9ad88e77977.png)

After it's done configuring you should see your wifi info in the original menu:

![wifiinfo](https://cloud.githubusercontent.com/assets/10035308/9141742/226f50de-3cf8-11e5-8b6b-328f2110e655.png)

For more WiFi configuration options see this page [HERE](https://github.com/RetroPie/RetroPie-Setup/wiki/Wifi)

## Transferring Roms

Due to the nature/complexity of Copyright/Intellectual Property Rights Law, which differs significantly from Country to Country, ROMs cannot be provided with RetroPie and must be provided by the user. You should only have ROMs of games that you own. 

There are three main methods of transferring roms: 

### USB
 * (ensure that your USB is formatted to FAT32 or NTFS)
 * first create a folder called `retropie` on your USB stick
 * plug it into the pi and wait for it to finish blinking
 * pull the USB out and plug it into a computer
 * add the roms to their respective folders (in the `retropie/roms` folder)
 * plug it back into the raspberry pi
 * wait for it to finish blinking
 * refresh emulationstation by choosing restart emulationstation from the start menu

see this video for reference:

<a href="https://www.youtube.com/watch?v=OYMoxvbkYD4
" target="_blank"><img src="https://i.ytimg.com/vi_webp/OYMoxvbkYD4/mqdefault.webp" 
alt="Configuration Video" width="300" height="190" border="10" /></a>

### SFTP (needs an active internet connection) 
* Wired (needs ethernet cable)
* Wireless (needs wifi dongle)
There are many SFTP programs out there, for windows many people use [WinSCP](https://winscp.net/eng/download.php) for mac you can use something like [Cyberduck](https://cyberduck.io/?l=en)

![winscp](https://cloud.githubusercontent.com/assets/10035308/12865832/7d9afb68-cc75-11e5-81b2-4529991e1821.png)

Default username: **pi** 

Default Password: **raspberry**

You can also log in as root if you wish to change more files than just the roms, but you first need to enable the root password which is explained [here](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-cant-i-ssh-as-root-anymore)

### Samba-Shares (needs an active internet connection)

- if on windows type `\\retropie` into the computer folder. You can also replace `retropie` with your Raspberry Pi's IP address

![samba](https://cloud.githubusercontent.com/assets/10035308/12865893/d2eab264-cc77-11e5-9ec6-003e13322a5a.png)

- if on MAC OS X open finder, select "Go" menu and "Connect to Server". Type `smb://retropie` and hit "Connect".

## PLAY!

After you've added your roms you need to restart emulationstation in order for them to show up. You can restart emulationstation from the start menu, or by rebooting your pi with `sudo reboot`. 

- see the rest of the [wiki](https://github.com/RetroPie/RetroPie-Setup/wiki) for more detailed information on individual emulators, advanced settings etc. If you still can't figure it out, the RetroPie community is very helpful on the [forum](https://retropie.org.uk/forum/). 

- **The RetroPie Project is primarily maintained by a few developers who develop the project in their free time. If you have found the RetroPie project useful please consider donating to the project [here.](https://retropie.org.uk/donate/). As you become more familiar with RetroPie, pay it forward by helping others on the forum. The RetroPie Project is what it is today because of the many contributions of the community.**

THANK YOU!