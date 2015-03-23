# Configuring Wifi

First check to see if your wifi dongle is [compatible](http://elinux.org/RPi_USB_Wi-Fi_Adapters):

There are two main methods to configure Wifi.

The first method is going to:

`sudo nano /etc/network/interfaces`

Then change the files to look like this:

```shell
sudo nano /etc/network/interfaces

Configuration File:
auto lo
iface lo inet loopback
iface eth0 inet dhcp
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
   wpa-ssid "Your Wireless Network Name"
   wpa-psk "Your Wireless Network Password"
```
you can also add "wireless-power off" at the end (without quotations) if you have issues with your wifi dongle turning off and on a lot and not being able to maintain a connection.

The second method is listed here:

http://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md

