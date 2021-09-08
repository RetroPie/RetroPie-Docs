# Configuring WiFi

If you have a Raspberry Pi 3, WiFi is built into the Pi, if you have a Pi2 or earlier model, then you'll need a wifi dongle. You can check to see if your wifi dongle is compatible [here](http://elinux.org/RPi_USB_Wi-Fi_Adapters). You may want to use an USB WiFi dongle, then see [here](#using-an-external-dongle).

*NOTE:* In order to use the WiFi on the Raspberry Pi, you will need to first configure the **WLAN Country** via `raspi-config`. It’s under menu _5 Localisation options_ in `raspi-config`. You can start `raspi-config` from the `RetroPie` menu in EmulationStation or from the command line with `sudo raspi-config`.

There are 5 main methods to configure Wifi:

1. [Wifi Module](#wifi-module)
2. [Connecting to Wifi Without a Keyboard](#connecting-to-wifi-without-a-keyboard)
3. [Manual Configuration (Interfaces)](#manual-configuration-interfaces)
4. [Manual Configuration (WPA_Supplicant)](#manual-configuration-wpa_supplicant)
5. [WICD-Curses](#wicd-curses)

## WiFi Module

You can access this from the Retropie menu in emulationstation (you can also access it from option 3 in the RetroPie setup script):

![retropiemenuwifi](https://cloud.githubusercontent.com/assets/10035308/9141387/7ed23ec0-3cf5-11e5-9944-a8f7870cc6c0.png)

It will open into this menu:

![wifi1](https://cloud.githubusercontent.com/assets/10035308/9141521/96ceb142-3cf6-11e5-9ba4-2b23a8b52480.png)

Choose your SSID from a list:

![wifi2](https://cloud.githubusercontent.com/assets/10035308/9141549/cd763742-3cf6-11e5-836e-a257e888bfb2.png)

Type your Wifi Password (You may need to wait a bit after you finish for the configurations to save)

![wifi3](https://cloud.githubusercontent.com/assets/10035308/9141565/f2252120-3cf6-11e5-9eeb-e9ad88e77977.png)

After it's done configuring you should see your wifi info in the original menu:

![wifiinfo](https://cloud.githubusercontent.com/assets/10035308/9141742/226f50de-3cf8-11e5-8b6b-328f2110e655.png)

## Connecting to WiFi Without a Keyboard

If you wish to connect to wifi without needing an extra keyboard you can add a file to the boot partition of the sd card called `wifikeyfile.txt`

place your network details here (note only works on WPA networks)
```
ssid="NETWORK_NAME"
psk="NETWORK_PASSWORD"
```

You can then access the wifi module and select the option to "Import wifi credentials from `/boot/wifikeyfile.txt`"

![wifi_text](https://cloud.githubusercontent.com/assets/10035308/21238882/8fe42822-c2b9-11e6-9506-ddfc41fa2016.png)

## Connecting to WiFi Without a Keyboard

Starting with Raspbian Stretch, loading the wifikeyfile from the setup script is not necessary.

Create a file called `wpa_supplicant.conf` in the boot partition using the following template. (This will be moved at boot 
to the `/etc/wpa_supplicant directory`).

```

country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

# RETROPIE CONFIG START
network={
    ssid="your_real_wifi_ssid"
    psk="your_real_password"
}
# RETROPIE CONFIG END
```

Make sure to include the ```RETROPIE CONFIG ...``` lines as shown to ensure that the RetroPie-Setup wifi configuration module will be able to cleanly edit/delete your configuration if you wish to change it later.

Wifi will not start up if you have an hard wired ethernet connection. After disconnecting the ethernet cable you'll need to reboot to get Wifi started.

If you want ssh to be enabled by default as well you can create a blank file called `ssh` in the boot partition too. This is a 'flag' file and will be deleted during boot after ssh is enabled.

## Manual Configuration (Interfaces)

`sudo nano /etc/network/interfaces`

### WPA/WPA2

```shell
auto lo

iface lo inet loopback
iface eth0 inet dhcp

allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
   wpa-ssid "NETWORK_NAME"
   wpa-psk "NETWORK_PASSWORD"
```
you can also add `wireless-power off` at the end if you have issues with your wifi dongle turning off and on a lot and not being able to maintain a connection.

### WEP

```shell
auto lo

iface lo inet loopback
iface eth0 inet dhcp

allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
   wireless-essid NETWORK_NAME
   wireless-key NETWORK_PASSWORD
```

### Open Network

```shell
auto lo

iface lo inet loopback
iface eth0 inet dhcp

allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
  wireless-essid NETWORK_NAME
  wireless-mode managed
```

### Hidden SSID

```
auto lo

iface lo inet loopback
iface eth0 inet dhcp

allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
   wpa-ssid "NETWORK_NAME"
   wpa-psk "NETWORK_PASSWORD"
   wpa-scan-ssid 1
```

### Static IP

The following only applies to Raspbian Jessie

You can use the default `/etc/network/interfaces`
```shell
# interfaces(5) file used by ifup(8) and ifdown(8)

# Please note that this file is written to be used with dhcpcd
# For static IP, consult /etc/dhcpcd.conf and 'man dhcpcd.conf'

# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d

auto lo
iface lo inet loopback

iface eth0 inet manual

allow-hotplug wlan0
iface wlan0 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

allow-hotplug wlan1
iface wlan1 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```
Then you'll need to edit `/etc/dhcpcd.conf` and add at the top modifying it for your own router and IP address:

```
interface wlan0
 static ip_address=192.168.0.120/24
 static routers=192.168.0.1
 static domain_name_servers=8.8.8.8
```
If you want a static IP with ethernet then change it to:
```
interface eth0
 static ip_address=192.168.0.120/24
 static routers=192.168.0.1
 static domain_name_servers=8.8.8.8
```

`sudo reboot` for changes to take effect.

on reboot (if configured correctly) your wifi will be working.

## Manual Configuration (WPA_Supplicant)

**Taken from the Raspberry Pi Foundation [here](https://www.raspberrypi.org/documentation/computers/configuration.html#wireless-networking-command-line):**

> This method is suitable if you do not have access to the graphical user interface normally used to set up WiFi on the Raspberry Pi. It is especailly suited for use with a serial console cable if you don't have access to a screen or wired Ethernet network. Also note that no additional software is required; everything you need is already included on the Raspberry Pi.

### Getting Network Details

To scan for WiFi networks, use the command `sudo iwlist wlan0` scan. This will list all available WiFi networks along with other useful information. Look out for:

1. `ESSID:"testing"`. This is the name of the WiFi network.

2. `IE: IEEE 802.11i/WPA2 Version 1`. This is the authentication used; in this case it is WPA2, the newer and more secure wireless standard which replaces WPA1. This guide should work for WPA or WPA2, but may not work for WPA2 enterprise; for WEP hex keys see the last example [here](https://www.freebsd.org/cgi/man.cgi?query=wpa_supplicant.conf&apropos=0&sektion=5&manpath=NetBSD+9.2&arch=default&format=html). 
You will also need the password for the WiFi network. For most home routers this is located on a sticker on the back of the router. The ESSID (ssid) for the network in this case is `testing` and the password (psk) `testingPassword`.

### Adding Network Details to Raspberry Pi

First you'll need to ammend `/etc/network/interfaces` to point to wpa-supplicant if it isn't already:

```
auto lo

iface lo inet loopback
iface eth0 inet dhcp

allow-hotplug wlan0
auto wlan0
iface wlan0 inet manual
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
#The following line specified in /etc/network/interfaces will activate and configure each 'default' network in wpa_supplicant.conf with DHCP upon a successful connection to an access point (this line needs to be here for wpa-roam)
iface default inet dhcp
```
We've changed it to wpa-roam so that it will reconnect if the connection drops.

Open the `wpa-supplicant` configuration file in nano:

`sudo nano /etc/wpa_supplicant/wpa_supplicant.conf`

Go to the bottom of the file and add the following:
```shell
network={
    ssid="The_ESSID_from_earlier"
    psk="Your_wifi_password"
}
```

The following are different ways of configuring your network depending on what encryption your router is configured to.

#### WPA/WPA2

```shell
network={
    ssid="NETWORK_NAME"
    psk="NETWORK_PASSWORD"
}
```

#### WEP

```shell
network={
     ssid="NETWORK_NAME"
     key_mgmt=NONE
     wep_tx_keyidx=0 #this forces it to use wep_key0
     wep_key0=YOURWEPKEY
}
```

#### Open Network

```shell
network={
    ssid="NETWORK_NAME"
    key_mgmt=NONE
}
```

#### Hidden SSID

```shell
network={
    ssid="NETWORK_NAME" # it can be any encryption type, just make sure to add the "scan_ssid=1" line after your settings.
    key_mgmt=NONE
    scan_ssid=1
}
```
Now save the file by pressing **ctrl+x** then **y**, then finally press **enter**.

At this point,` wpa-supplicant` will normally notice a change has occurred within a few seconds, and it will try and connect to the network. If it does not, either manually restart the interface with `sudo ifdown wlan0` and `sudo ifup wlan0`, or reboot your Raspberry Pi with `sudo reboot`.

You can verify if it has successfully connected using `ifconfig wlan0`. If the `inet addr` field has an address beside it, the Pi has connected to the network. If not, check your password and ESSID are correct.

## WICD-Curses 

Note that this may cause a small amount of background cpu usage, which can stop the CPU from scaling to lowest frequency.

you first need to install it with `sudo apt install wicd wicd-curses` and then type `wicd-curses` in the terminal to open it.

_(of course you'll need to be connected by ethernet to install it)_

![](http://atastypixel.com/blog/wp-content/uploads/2011/09/Screen-Shot-2011-09-24-at-14.37.111.png)

Navigate to your wireless network and Press the `RIGHT` arrow to configure your wifi

![untitled drawing 2](https://cloud.githubusercontent.com/assets/10035308/7425946/1efa7e56-ef78-11e4-92fb-cf83a6b59e85.png)

check automatically connect to this network (by pressing enter) and type in your wifi password where it says "key" press `F10` to save and then press `SHIFT+c` to connect and press `Q` to exit back to the terminal. 

There are some noted issues with the daemon using some CPU and preventing the Pi from scaling to lowest frequency, so if that's the case you can remove wicd-curses by typing `sudo apt remove wicd-curses` and proceed to setup your wifi using method 2 or 3.

# Using an external dongle

You may want to use an external Wifi dongle: maybe your pi case is blocking or slowing the signal (with a metal case it's pretty common), for instance.

The easiest way is to first configure wifi with the internal controller, using one of the above methods.  
Plug your dongle, reboot, and make sure it's connected using `ifconfig` : it should appear as wlan1, and have an IP address.  
Then, disable the onboard wifi by editing `/boot/config.txt` and adding `dtoverlay=pi3-disable-wifi`.  
That's it :)
