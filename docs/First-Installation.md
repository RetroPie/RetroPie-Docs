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

* Computer (or laptop)
* [Raspberry Pi](https://retropie.org.uk/about/building/)
* [MicroSD card](https://user-images.githubusercontent.com/540857/108582784-5f8b6880-7303-11eb-9652-26a0680f9cae.jpg) (see [compatible SD cards](http://elinux.org/RPi_SD_cards))
* MicroSD card reader - a way to plug the MicroSD card into your computer or laptop
  * Some laptops have this functionality in the form of an SD card slot ([example #1](https://user-images.githubusercontent.com/540857/107868575-6f163780-6e53-11eb-9943-faec57cbf48e.png), [example #2](https://user-images.githubusercontent.com/540857/107868592-94a34100-6e53-11eb-91ed-e645be9827aa.jpg)).
  * A [USB MicroSD card reader](https://user-images.githubusercontent.com/540857/107463579-68728200-6b2c-11eb-9612-05c4d1931882.jpg) can be plugged into any USB port
* Screen (TV, computer monitor, projector, etc) - anything with HDMI or RCA
* Video cable
  * Pi 4 will need a [Micro HDMI to HDMI](https://user-images.githubusercontent.com/540857/107463741-c3a47480-6b2c-11eb-8402-7313a490e234.jpg) cable
  * Pi 1, 2, and 3 will need a full-size [HDMI](https://user-images.githubusercontent.com/540857/107463845-ff3f3e80-6b2c-11eb-8031-3d0ed5563861.jpg) cable
  * Pi Zero will need a [Mini HDMI to HDMI](https://user-images.githubusercontent.com/540857/107686191-e3de4b80-6c72-11eb-8162-07a82afaac7b.jpg) cable
  * [4-Pole RCA to 3.5mm](https://user-images.githubusercontent.com/540857/107688722-f3ab5f00-6c75-11eb-9837-ffe7f385b1c5.jpg) is also an option for older screens
* Power supply
  * View the official [Raspberry Pi Power](https://www.raspberrypi.org/documentation/computers/raspberry-pi.html#power-supply) documentation for each model
* Game controller of your choice 
  * Can be USB-wired, wireless (with a dongle), or Bluetooth (with or without a dongle. Pi 3 and later models have built-in Bluetooth and won't need a dongle)
  * The [Control Block](http://blog.petrockblock.com/2014/12/29/controlblock-power-switch-and-io-for-the-raspberry-pi/) can use original SNES controllers

### Optional

* Raspberry Pi case - **highly recommended**
* Wifi dongle or ethernet cable to connect to the internet for [Updating](Updating-RetroPie) and [Transferring ROMs](Transferring-Roms) (see [wifi dongle compatible list](http://elinux.org/RPi_USB_Wi-Fi_Adapters). Wifi is built-in for the Pi 3 and later models and will not need a dongle.)
* USB Keyboard - to help with some configuration that cannot be done with a game controller, or you can use [SSH](SSH)

## Installation

1. First, insert the MicroSD card into into your computer
2. [Download the RetroPie .img.gz image](https://retropie.org.uk/download/) from the official website for your Raspberry Pi model.
   * If you use [Raspberry Pi Imager](https://www.raspberrypi.org/software/) (recommended), you can omit this step and simply choose RetroPie from the list of included images ([example](https://user-images.githubusercontent.com/540857/107868009-493a6400-6e4e-11eb-9272-7f45d569dc44.gif)). If needed, official instructions for using the Raspberry Pi Imager are [here](https://www.raspberrypi.org/documentation/computers/getting-started.html#using-raspberry-pi-imager)
   * Select the image for the model of Raspberry Pi (RPI) that you have. For example, if you have a Raspberry Pi 4, select the *RPI 4/400* image
     * If you don't know which model Raspberry Pi you have, the [Raspberry Pi Wikipedia page](https://en.wikipedia.org/wiki/Raspberry_Pi#Connectors) has user-friendly graphics to help determine model by looking at the board itself. If you have SSH/commandline access, run `cat /proc/device-tree/model` and it will output your Pi's model
3. Download a program to write the RetroPie *.img.gz* image to your MicroSD card
   * For Windows: [Raspberry Pi Imager](https://www.raspberrypi.org/software/), [Etcher](https://www.balena.io/etcher/), or [Win32DiskImager](https://sourceforge.net/projects/win32diskimager/)
     * Win32DiskImager requires an .img file extracted from the *.img.gz* image downloaded in step #2. You can use a program like [7zip](https://www.7-zip.org/download.html) to do this
   * For macOS: [Raspberry Pi Imager](https://www.raspberrypi.org/software/), [Etcher](https://www.balena.io/etcher/), [Apple Pi Baker](https://www.tweaking4all.com/hardware/raspberry-pi/applepi-baker-v2/), or the `dd` command
   * For Linux: [Raspberry Pi Imager](https://www.raspberrypi.org/software/), [Etcher](https://www.balena.io/etcher/), or the `dd` command
    * MacOS/Linux users can optionally extract the .img image from the downloaded .img.gz by using `gunzip` (macOS users can also simply double-click it)
4. Once the program's image/OS and SD card have been chosen, *write* it to the SD card and wait until the operation completes
5. Remove the MicroSD card from your computer, slide it back into the slot on your Raspberry Pi, and turn it on

## Configure Controllers

On first boot you will be welcomed with the screen below. This menu will configure your controls for EmulationStation, all RetroArch emulators, and select standalone emulators:

![welcomescreen](https://cloud.githubusercontent.com/assets/10035308/9140482/cf42f25c-3cee-11e5-8f91-c1fc1c57175c.png)

Hold down any button on your controller or keyboard. While holding, its name will appear at the bottom of the window for a few seconds and then open up into a configuration menu:

![welcomescreengamepadconfigure](https://cloud.githubusercontent.com/assets/10035308/9140518/0263b9c8-3cef-11e5-922f-42f790f3be91.png)

Follow the onscreen instructions to configure your gamepad. If your controller doesn't have a button that you're being asked to define, just hold down any button to skip it.

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

More info at [RetroArch Controller Configuration](RetroArch-Configuration)

### Hotkey

The Hotkey Enable button enables you to press it in combination with another button to access functions such as saving states, loading states, opening the RetroArch GUI (RGUI), and exiting back to EmulationStation. It is recommended to define an unused button or key as your Hotkey Enable button. For example, the **Home** button on some controllers such as the center "X" on Xbox controllers. If your controller doesn't have an unused button, the **Select** button is a good alternative.

The following chart shows the default hotkey combinations.

**Note** Hotkeys are specific to the RetroArch/Libretro based emulators and may not work on other emulators.

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

**When you get to "OK" at the end, press the button you have configured as "A" (East) to complete this step**.

## EmulationStation

| **Where are the systems?**|
| :---: | 
**When you first see EmulationStation you may wonder why you don't see systems like the SNES or Game Boy. Worry not - the emulators are installed on the system, but ROMs will need to be added to their respective rom folders before they will become visible**|
|![firstboot](https://cloud.githubusercontent.com/assets/10035308/16217874/c6bbdb3a-3734-11e6-998f-8cc714a320ce.png)|

## Transferring ROMs

You will not see any game systems (NES, n64, Playstation, etc) on the system list until you add ROMs! Visit the [Transferring ROMs](Transferring-Roms) page to learn how to transfer ROMs to RetroPie.

## Audio

In general RetroPie audio will work out-of-the-box without any tweaking if using HDMI, but if you have audio issues you should follow the instructions on the [Sound Issues Page](Sound-Issues) to fix them. You will most likely need to visit this page if you are using a USB audio device, or if you are using an aftermarket RPi HAT add-on audio device (such as a Justboom sound card).

## PLAY!

After you've transferred your ROMs, you need to restart EmulationStation in order for them to show up. You can restart EmulationStation by pressing Start > Quit > Restart EmulationStation, or with SSH access by rebooting your pi with `sudo reboot`. Once rebooted, you should see the game systems appear on the system list.

## Additional Setup Options

* [Configure Wifi](Wifi)
* [Enable SSH](SSH)
* Configure more controllers. This can be done after plugging in the new controller and pressing *Start* on your controller and selecting *Configure Input*
* In RetroPie, not everything is installed by default. The pre-made images contain the best-working emulators for the more common systems supported by the hardware. This should cover typical use, but if you want to install additional emulators or ports, the [Updating RetroPie](https://retropie.org.uk/docs/Updating-RetroPie/#updatinginstalling-individual-packages) page has this information. 
* [Cheat codes](Cheats)!

See the rest of the [RetroPie documentation](https://retropie.org.uk/docs/) for more detailed information on individual emulators, advanced settings, etc. If you're having trouble, you may find answers in the [FAQ](FAQ). Also, the RetroPie community is very helpful on the [RetroPie forum](https://retropie.org.uk/forum/). 

**The RetroPie Project is primarily maintained by a few developers who develop the project in their free time. If you have found the RetroPie project useful please consider donating to the project [here](https://retropie.org.uk/donate/). As you become more familiar with RetroPie, pay it forward by helping others on the forum. The RetroPie Project is what it is today because of the many contributions of the community.**

THANK YOU!
