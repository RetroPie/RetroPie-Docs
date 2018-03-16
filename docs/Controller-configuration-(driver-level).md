# Controller configuration (driver level)
## Introduction
It can happen that a controller axis is inverted. In other words, When moving 'up' in Emulationstation or Attract mode it reports that is has mapped the 'Y-down' button of the controller. A situation where this can happen is with custom Arcade Controllers that are wired in a wrong way. This is not an issue for ES or AM, because they map the actual direction on the direction reported by the controller, but becomes an issue for applications that use the native driver output instead of the button configuration in RetroArch, Attract Mode or Emulationstation.

The driver button mapping, joystick axis and axis calibration can be changed with the commandline utilities _jstest_, _jscal_, _jscal-store_ and _jscal-restore_,which are part of the joystick input driver package. When the Pixel desktop environment is installed, life can be made easy by installing _jstest-gtk_. The mapping requires some persistance, but with a little patience it not a major task. Please refer to the appropriate Man pages for more information on these utilities. This instruction assumes that you are using _jstest-gtk_.

## **Prerequisites**
First install the appropriate packages (if not available):

`sudo apt-get install joystick`

`sudo apt-get install jstest-gtk `

## **Calibration with _jstest-gtk_**
Usage of jstest-gtk is straightforward. When running it, it will first show a page to select your joystick(s). 

![jscal-gtk-01](https://user-images.githubusercontent.com/1189058/37540633-0002f9f2-2958-11e8-8f90-8a559a32a0b6.png)

When selecting the appropriate device, a second screen is shown in which you can test the axes and button response. In the bottom of this screen there are two buttons, which will have you configure the button mapping and axes calibration.

![jscal-gtk-02](https://user-images.githubusercontent.com/1189058/37540634-002a7694-2958-11e8-815e-92053260fff7.png)

### Button and axis remapping 
Button remapping can be done, by dragging and dropping the appropriate buttons in a new order.

![jscal-gtk-03](https://user-images.githubusercontent.com/1189058/37540636-0056b5ce-2958-11e8-8b66-b3aee59e7c4d.png)

### Axis calibration
With axis calibration you can remove deadzones in your joystick. You can also invert the axis direction, if necessary, by ticking the box behind the axis number.

![jscal-gtk-04](https://user-images.githubusercontent.com/1189058/37540637-0070056a-2958-11e8-9908-52fca2e74b35.png)

### Calibration from the commandline
Calibration can also be done from commandline by using _jscal_. This is much less straightforward, so please study the manpages carefully on how to use these commands. Calibration and mapping is split in two separate commandline commands:

`jscal -c <device>` to calibrate axes

`jscal - u <device>` to change mappings

## Persistent saving of the settings
When using _jstest-gtk_, the settings are not permanently saved. In order to save your settings, you need to use some commandline commands:

`jscal-store <device>` will store the settings for the specified device in a separate file: _var/lib/joystick/joystick.state_. The information for each unique device is appended to the contents of this file. An example of the contents can be found below:

```
NAME="ControlBlock Arcade Gamepad"
jscal -u 2,0,1,12,304,305,306,307,308,311,309,310,312,313,314,315
jscal -s 2,1,0,2,2,-268427264,-268427264,1,0,2,2,-268427264,-268427264

NAME="USB Gamepad "
VENDOR="0079"
PRODUCT="0011"
jscal -u 2,0,1,10,288,289,290,291,292,293,294,295,296,297
jscal -s 2,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751
```  
When the appropriate device settings are stored in the _joystick.state_ file, the changes can be made persistent by using `jscal-restore <device>` in a 'UDEV' rule. A _60-joystick.rules_ file should be available in _/var/lib/udev/rules.d/_. The file contains an `UDEV` rule which uses 'jscal-restore' to load the _joystick.state_ file for joystick devices that are being attached. The contents of this file should be as follows:

```
# Restore any stored calibration for the device
ACTION=="add", KERNEL=="js*", RUN+="/lib/udev/jscal-restore %E{DEVNAME}"

# Avoid this specific gamepad disappearing (see
# https://bugs.launchpad.net/ubuntu/+source/joystick/+bug/448446)
ACTION=="add", KERNEL=="js*", ATTRS{name}=="ACRUX USB GAMEPAD 8116", RUN+="/lib/
udev/js-acrux %E{DEVNAME}"

```
## `UDEV` rules and device numbering /_dev/input/js_x_
Please note that the UDEV rule above maps the joystick to an arbitrary device number. The device number is mapped in order of connection. The first connected device is mapped as _/dev/input/js0_, the following _/js1_, etc.... It is not possible to use an UDEV rule to rename these mappings (although a lot of older websites say otherwise). 


# References
* image source: [https://pingus.seul.org/~grumbel/jstest-gtk/](https://pingus.seul.org/~grumbel/jstest-gtk/)
* Jstest-gtk [Manpage](http://manpages.ubuntu.com/manpages/artful/man1/jstest-gtk.1.html)
* jscal [Manpage](http://manpages.ubuntu.com/manpages/trusty/man1/jscal.1.html)
* jscal-store [Manpage](http://manpages.ubuntu.com/manpages/xenial/man1/jscal-store.1.html)
* jscal-restore [Manpage](http://manpages.ubuntu.com/manpages/xenial/man1/jscal-restore.1.html) 