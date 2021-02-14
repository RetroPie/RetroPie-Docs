![retropie_logo](https://cloud.githubusercontent.com/assets/10035308/21968193/e1670f2a-db46-11e6-8ff7-eb6d7188c9e7.png)

|Version|4.7|
|:---:|:---:|

Congratulations! You have discovered the wonderful world of RetroPie- your entire childhood is within reach! RetroPie is a combination of multiple projects including [RetroArch](http://www.retroarch.com), [EmulationStation](https://www.emulationstation.org), and many others. 

This page is for people just getting started on RetroPie. The easiest way to install RetroPie is the SD image which is a ready to go system built upon top of the Raspberry Pi OS - this is the method described in the following guide. Alternatively, advanced users can install RetroPie [manually](Manual-Installation). 

This guide will give you the very basics to get you up and running from a blank MicroSD card to first boot into EmulationStation.

The following video will also walk you through the installation process. Otherwise read on! 

<a href="https://www.youtube.com/watch?v=E1sbnPZ_A8w
" target="_blank"><img src="https://user-images.githubusercontent.com/540857/107464585-9fe22e00-6b2e-11eb-9927-b1ec32360838.jpg" 
alt="RetroPie First Installation Video" border="10" /></a>

## Hardware

The simplest way to get most of these components is through an all-in-one kit such as the [Canakit](https://www.amazon.com/stores/CanaKit/page/19109D80-639C-40C8-9222-DC6775C304EE).

### Required

* [Raspberry Pi](https://retropie.org.uk/about/building/)
* MicroSD Card ([list of compatible SD cards](http://elinux.org/RPi_SD_cards))
* [USB MicroSD card reader](https://user-images.githubusercontent.com/540857/107463579-68728200-6b2c-11eb-9612-05c4d1931882.jpg) - an adapter that allows plugging the MiscroSD card into any USB port
  * Some laptops have this functionality in the form of an SD card slot ([example #1](https://user-images.githubusercontent.com/540857/107868575-6f163780-6e53-11eb-9943-faec57cbf48e.png), [example #2](https://user-images.githubusercontent.com/540857/107868592-94a34100-6e53-11eb-91ed-e645be9827aa.jpg)). In this case, a USB MicroSD card reader may not be needed, but can still be useful to have to allow manipulation of the MicroSD card in any computer with a USB port.
* Screen (TV, computer monitor, projector, etc) - anything with HDMI or RCA
* Video cable
  * Pi 4 will need a [Micro HDMI to HDMI](https://user-images.githubusercontent.com/540857/107463741-c3a47480-6b2c-11eb-8402-7313a490e234.jpg) cable
  * Pi 1, 2, and 3 will need a full-size [HDMI](https://user-images.githubusercontent.com/540857/107463845-ff3f3e80-6b2c-11eb-8031-3d0ed5563861.jpg) cable
  * Pi Zero will need a [Mini HDMI to HDMI](https://user-images.githubusercontent.com/540857/107686191-e3de4b80-6c72-11eb-8162-07a82afaac7b.jpg) cable
  * [4-Pole RCA to 3.5mm](https://user-images.githubusercontent.com/540857/107688722-f3ab5f00-6c75-11eb-9837-ffe7f385b1c5.jpg) is also an option for older screens
* Power supply
  * View the official [Raspberry Pi Power](https://www.raspberrypi.org/documentation/hardware/raspberrypi/power/) documentation for each model
* Game controller of your choice 
  * Can be USB-wired, wireless (with a dongle), or Bluetooth (with or without a dongle. Pi 3 and later models have built-in bluetooth and won't need a dongle)
  * The [Control Block](http://blog.petrockblock.com/2014/12/29/controlblock-power-switch-and-io-for-the-raspberry-pi/) can use original SNES controllers

### Optional

* Raspberry Pi case - **highly recommended**
* Wifi dongle or ethernet cable to connect to the internet for [Updating](Updating-RetroPie) and [Transferring ROMs](Transferring-Roms) (see [wifi dongle compatible list](http://elinux.org/RPi_USB_Wi-Fi_Adapters). Wifi is built-in for the Pi 3 and later models and will not need a dongle.)
* USB Keyboard - to help with some configuration that cannot be done with a game controller, or you can use [SSH](SSH)

## Installation

### Plug in the MicroSD card

The [MicroSD card](https://user-images.githubusercontent.com/540857/107868231-830c6a00-6e50-11eb-85d1-9a6ada5f28b4.jpg) needs to be plugged into your PC, but most PCs don't have a port for it (although some laptops do). You'll need to insert the MicroSD card into an adapter, such as a [USB MicroSD card reader](https://user-images.githubusercontent.com/540857/107463579-68728200-6b2c-11eb-9612-05c4d1931882.jpg). This allows it to be plugged into any USB port on your PC. Once it's plugged into your PC, continue to the next step.
### Download
Download the official [Raspberry Pi Imager](https://www.raspberrypi.org/software/), which allows downloading the different OS versions of Retropie.

1. Click the **Choose OS** button
2. Select **Emulation and game OS**
3. Select **RetroPie**.
4. Select the image for the model of Raspberry Pi (RPI) that you have. For example, if you have a Raspberry Pi 4, select the RPI 4/400 option.

![rpi-imager](https://user-images.githubusercontent.com/540857/107868009-493a6400-6e4e-11eb-9272-7f45d569dc44.gif)

If you don't know which model Raspberry Pi you have, there are a few methods to find out:

* The [Raspberry Pi Wikipedia page](https://en.wikipedia.org/wiki/Raspberry_Pi#Connectors) has user-friendly graphics to help determine model by looking at the board itself.
* If you have SSH/commandline access, run `cat /proc/device-tree/model` and it will output your Pi's model

### Install

1. Click the **Choose SD Card** button. 
2. The MicroSD card you plugged in earlier should appear in this list. Select it to continue.
3. Once your "OS" and "SD card" have been chosen, select **Write**, and wait until the operation completes.
4. Remove the MicroSD card from your PC, slide it back into the slot on your Raspberry Pi, and turn it on.


**Note**: You can safely ignore Windows' warnings about this drive. You may see Windows complain that "There is a problem with this drive", but everything is fine. RetroPie is built on top of Raspberry Pi OS Buster (a Linux based OS for the Raspberry Pi) and as such the partition on the SD card is EXT4 (a linux filesystem). This partition is not visible on Windows systems, so the card will show up as a smaller size than usual and you won't be able to see everything on the card. 

## Configure Controllers

On first boot your filesystem will be expanded automatically, you will then be welcomed with the following screen- this menu will configure your controls for both EmulationStation and RetroArch Emulators:

![welcomescreen](https://cloud.githubusercontent.com/assets/10035308/9140482/cf42f25c-3cee-11e5-8f91-c1fc1c57175c.png)

Hold down any button on your keyboard or gamepad and the name will appear at the bottom and then open up into a configuration menu:

![welcomescreengamepadname](https://cloud.githubusercontent.com/assets/10035308/9140505/f5c19e38-3cee-11e5-965e-0e4e85ddaf56.png)

Follow the onscreen instructions to configure your gamepad- if you run out of buttons just hold down a button to skip each unused button. **When you get to OK press the button you have configured as "A"**.

![welcomescreengamepadconfigure](https://cloud.githubusercontent.com/assets/10035308/9140518/0263b9c8-3cef-11e5-922f-42f790f3be91.png)

If you wish to configure more than one controller, you can do so from the start menu of EmulationStation. For more details on manual controller configurations see this page [Here](RetroArch-Configuration).

See the following diagrams for reference:

| SNES Controller | 
|:---:|
|![snes_controller](https://cloud.githubusercontent.com/assets/10035308/22185414/f129dc28-e099-11e6-8524-93facf275eda.png)|

| XBox 360 Controller |
|:---:|
|![xbox360_controller](https://cloud.githubusercontent.com/assets/10035308/22185415/f12ff342-e099-11e6-8adb-d18e9c638e94.png)|

| PS3 Controller |
|:---:|
|![ps3_controller](https://cloud.githubusercontent.com/assets/10035308/22185413/f10f27de-e099-11e6-97a4-ecbbc82c9e46.png)|

### Hotkey

The Hotkey button enables you to press it in combination with another button to access functions such as saving, loading, and exiting in emulators. It is suggested to use the **Select** button as the hotkey. The following chart shows the default hotkey combinations. For example, if you chose Select as your Hotkey, that means you hold down Select while pressing the other button to execute the command. 

**Note** Hotkey combinations are specific to the retroarch/libretro based emulators.

|Hotkey Combination | Action|
| :---: | :---: |
| Hotkey+Start | Exit |
| Hotkey+Right Shoulder | Save |
| Hotkey+Left Shoulder | Load |
| Hotkey+Right | Input State Slot Increase |
| Hotkey+Left | Input State Slot Decrease |
| Hotkey+X | RGUI Menu |
| Hotkey+B | Reset |

For more information, see [Hotkeys](RetroArch-Configuration#hotkeys)

## EmulationStation

| **Where are the systems?**|
| :---: | 
**When you first see EmulationStation you may wonder why you don't see systems like the SNES or Game Boy- worry not- they are installed on the system, roms just need to be added to their respective rom folders before they will become visible. Transferring roms are described in the following steps.**|
|![firstboot](https://cloud.githubusercontent.com/assets/10035308/16217874/c6bbdb3a-3734-11e6-998f-8cc714a320ce.png)|

## Wifi

If you wish to use wifi to transfer roms over the network rather than a USB stick or Ethernet cable you'll need to setup your wifi- which can also be done from the RetroPie menu in EmulationStation:

| Connect to Wifi Network: |
|:---:|
|![wifi1](https://cloud.githubusercontent.com/assets/10035308/16217941/92b08b8c-3735-11e6-8f20-5d1550af0882.png)|

| Choose your SSID from a list: |
|:---:|
|![wifi2](https://cloud.githubusercontent.com/assets/10035308/16217942/92c5a8a0-3735-11e6-86ed-721c1bb81990.png)|

| Type your Wifi Password (may take a moment to connect) |
|:---:|
|![wifi3](https://cloud.githubusercontent.com/assets/10035308/16217943/92c64c24-3735-11e6-8f62-893f111c5bd2.png)|

|Once configured you will see your IP address|
|:---:|
|![wifi4](https://cloud.githubusercontent.com/assets/10035308/16217944/92cb07fa-3735-11e6-9239-66fba394c669.png)|

For more WiFi configuration options see this [page](Wifi)

## Installing additional Emulators
On RetroPie 4.0+, not everything is installed by default. The pre-made images contain the best working emulators for each system supported by the hardware. This should cover everything most users would be doing. Ports like quake and doom and some other emulators like ScummVM can be installed later.

Software can be installed from the RetroPie-Setup script - which is accessible from the RetroPie menu on EmulationStation. Once there you can navigate to "Manage Packages" where you will see various sections. In each section are lists of packages that can be installed (and it will show what is currently installed). Stable additional packages are under the "Optional" section, with more unstable packages listed under experimental. The packages are ordered first by type (emulators / libretro cores / ports), then alphabetically. By selecting a package you can choose to install it, or remove it. Some packages also have additional configurations.

## Transferring ROMs

You will not see any game systems (NES, n64, Playstation, etc) on the main menu until you add ROMs! Visit the [Transferring ROMs](Transferring-Roms) page to learn how to transfer ROMs to RetroPie.

## AUDIO

In general RetroPie audio will work out of the box without any tweaking, but if you have audio issues you should follow the instructions on the [Sound Issues Page](Sound-Issues) to fix them. You will most likely need to visit the [Sound Issues Page](Sound-Issues) if you are using a USB Audio device, or if you are using an aftermarket RPi HAT add-on audio device (such as a Justboom sound card).

## PLAY!

After you've added your roms you need to restart EmulationStation in order for them to show up. You can restart EmulationStation from the start menu, or by rebooting your pi with `sudo reboot`. 

See the rest of the [docs](https://retropie.org.uk/docs/) for more detailed information on individual emulators, advanced settings etc. If you still can't figure it out, the RetroPie community is very helpful on the [forum](https://retropie.org.uk/forum/). 

**The RetroPie Project is primarily maintained by a few developers who develop the project in their free time. If you have found the RetroPie project useful please consider donating to the project [here](https://retropie.org.uk/donate/). As you become more familiar with RetroPie, pay it forward by helping others on the forum. The RetroPie Project is what it is today because of the many contributions of the community.**

THANK YOU!
