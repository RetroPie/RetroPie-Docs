# Configuring Wifi

First check to see if your wifi dongle is [compatible](http://elinux.org/RPi_USB_Wi-Fi_Adapters):

There are 4 main methods to configure Wifi.

## Method 1 (Easiest)

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

## Method 2 (INTERFACES)

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

```shell
auto lo

iface lo inet loopback
iface eth0 inet dhcp

allow-hotplug wlan0
auto wlan0

iface wlan0 inet static 
   wpa-ssid "NETWORK_NAME" #(set these lines for their respective encryption type- wpa, wep, etc.)
   wpa-psk "NETWORK_PASSWORD"
address 192.168.0.110 #(This is the IP you want your raspberry pi to have)
netmask 255.255.255.0 #(This is almost always the same)
gateway 192.168.0.1 #(almost always the same as well. you can verify with netstat -nr)
```

`sudo reboot`

on reboot (if configured correctly) your wifi will be working.

## Method 3 (wpa_supplicant.conf)

**Taken from the Raspberry Pi Foundation [here](http://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md):**

This method is suitable if you do not have access to the graphical user interface normally used to set up WiFi on the Raspberry Pi. It is especailly suited for use with a serial console cable if you don't have access to a screen or wired Ethernet network. Also note that no additional software is required; everything you need is already included on the Raspberry Pi.

### GETTING WIFI NETWORK DETAILS

To scan for WiFi networks, use the command `sudo iwlist wlan0` scan. This will list all available WiFi networks along with other useful information. Look out for:

1. `ESSID:"testing"`. This is the name of the WiFi network.

2. `IE: IEEE 802.11i/WPA2 Version 1`. This is the authentication used; in this case it is WPA2, the newer and more secure wireless standard which replaces WPA1. This guide should work for WPA or WPA2, but may not work for WPA2 enterprise; for WEP hex keys see the last example [here](http://netbsd.gw.com/cgi-bin/man-cgi?wpa_supplicant.conf+5+NetBSD-current). 
You will also need the password for the WiFi network. For most home routers this is located on a sticker on the back of the router. The ESSID (ssid) for the network in this case is `testing` and the password (psk) `testingPassword`.

### ADDING THE NETWORK DETAILS TO THE RASPBERRY PI

Open the `wpa-supplicant` configuration file in nano:

`sudo nano /etc/wpa_supplicant/wpa_supplicant.conf`

Go to the bottom of the file and add the following:
```shell
network={
    ssid="The_ESSID_from_earlier"
    psk="Your_wifi_password"
}
```
In the case of the example network, we would enter:

### WPA/WPA2

```shell
network={
    ssid="testing"
    psk="testingPassword"
}
```

### WEP

```shell
network={
     ssid="NETWORK_NAME"
     key_mgmt=NONE
     wep_tx_keyidx=0 #this forces it to use wep_key0
     wep_key0=YOURWEPKEY
}
```

### Open Network

```shell
network={
    ssid="NETWORK_NAME"
    key_mgmt=NONE
}
```

### Hidden SSID

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

## Method 4 (Wicd-Curses) 

Note that this may cause a small amount of background cpu usage, which can stop the CPU from scaling to lowest frequency.

you first need to install it with `sudo apt-get install wicd wicd-curses` and then typ wicd-curses in the terminal to open it.

_(of course you'll need to be connected by ethernet to install it)_

![](http://atastypixel.com/blog/wp-content/uploads/2011/09/Screen-Shot-2011-09-24-at-14.37.111.png)

Navigate to your wireless network and Press the `RIGHT` arrow to configure your wifi

![untitled drawing 2](https://cloud.githubusercontent.com/assets/10035308/7425946/1efa7e56-ef78-11e4-92fb-cf83a6b59e85.png)

check automatically connect to this network (by pressing enter) and type in your wifi password where it says "key" press `F10` to save and then press `SHIFT+c` to connect and press `Q` to exit back to the terminal. 

There are some noted issues with the daemon using some CPU and preventing the Pi from scaling to lowest frequency, so if that's the case you can remove wicd-curses by typing `sudo apt-get remove wicd-curses` and proceed to setup your wifi using method 2 or 3.