The XGaming X-Arcade encoder is one of the few encoders that defaults as a keyboard encoder. This means that the controls send down keyboard commands instead of being registered as gamepad. This makes setup a breeze and opens up additional possibilities not possible with most joystick driver based encoders, especially in RetroArch.

XGaming's most popular joystick is the ready made Tankstick but you can also buy just the encoder boards separately from them for your own DIY cabinet. Since it is just a keyboard encoder, there is no special setup needed when using it. Simply plug it in to the usb port on the raspberry pi, and it is immediately recognized as a keyboard. From here you can map control within EmulationStation. The encoder board supports 28 inputs which gives you 2 joysticks and 20 buttons. Each input sends out a different default keyboard stroke, but also allows you to reprogram which keys that are mapped in case you need something more custom.

One good point about keyboard encoders is that you can set RetroArch to work in non-hotkey mode and assign single commands for admin buttons. With gamepad-based encoders there doesn't appear to be a way to map a single button to hotkeys like Exit, reset, save, load, etc. That gives this encoder a leg up on the others depending on your joypanel build out.

Alternatively, a driver has been written for the X-arcade encoder to act as a joystick called Xarcade2Jstick

## The user-space driver Xarcade2Jstick

### Motivation

The Linux kernel registers the joysticks and the buttons of the Xarcade Tankstick as a single USB keyboard device. If you are connecting the according USB connector for the arcade trackball with your host machine, the kernel registers it as an USB mouse.
Because a keyboard is probably the most basic input device for a computer and every emulator supports the keyboard as input device this approach gives the user a huge amount of freedom regarding the configuration and application of the Tankstick when used with emulators. There is, however, at least one situation, in which it would be of advantage when the Tankstick would be registered as, say, two game pad devices instead of a single keyboard. More specifically, I came into this situation when I thought about a way for switching automatically to the Tankstick as input device when it is connected to a computer with a RetroPie installation: The front-end EmulationStation looks for game pad devices for its assisted input configuration. Also, all emulated systems that rely on the RetroArch emulator make use of the auto-configuration functionality. This function loads an input configuration depending on the currently connected game pads. Last but not least some other emulators like PiFBA come with a ready-to-go game pad configuration.

These points were the motivation for developing Xarcade2Jstick. The next section describes the functions and also gives a brief overview about its software architecture.

Functionalities and Architecture
The use cases for the Xarcade2Jstick daemon are as following:

Detect a connected Xarcade Tankstick
When starting, the tool detects a connected Xarcade Tankstick.
Map Xarcade Tankstick event to game pad event
The tool listens to the events of the Tankstick and maps every received event to an according game pad event.
Map alternative function event to keyboard event
If certain button combinations are pressed on the Tankstick, alternative keyboard events are generated.
The following diagram shows the dependencies between the modules:

![](http://blog.petrockblock.com/wp-content/uploads/2014/06/xarcade2jstick1.png)

The Xarcade Tankstick is abstracted by the module “input_xarcade”. The input_xarcade” module, in turn, is using the Linux “input” module. These modules are responsible for capturing the original keyboard events from the Tankstick. Most of the keyboard events are mapped to corresponding game pad events. Certain key combinations are mapped to keyboard presses: COIN1+Start1 is mapped to TAB and COIN2+START2 is mapped to ESC. These virtual game pad and keyboard presses are abstracted by the modules “uinput_gamepad” and “uinput_kbd”. These two modules are using the Linux “uninput” module for realizing these user-space input events.

The following diagram shows the program flow of Xarcade2Jstick:

![](http://blog.petrockblock.com/wp-content/uploads/2014/06/xarcade2jstick2.png)

First of all, the Xarcade Tankstick is identified and opened exlusively by Xarcade2Jstick. Afterwards, two game pads and a keyboard are registered via the uinput module. Then the main loop is started. It consists of reading the events of the Xarcade device and of mapping the events to the virtual game pads and the keyboard.

### Installation and Usage
The following installation and usage manual is taken from the Github site of the tool:

### Downloading

If you would like to download the current version of Xarcade2Jstick from its Github repository, you can use this command:
`git clone https://github.com/petrockblog/Xarcade2Jstick`

### Building and Installation

To build Xarcade2Jstick follow these commands:

`cd Xarcade2Jstick`
`make`

If everything went fine you can install with the command

`sudo make install`

Installation as Service

You can install Xarcade2Jstick as daemon with this command:

`sudo make installservice`

### Usage

Xarcade2Jstick looks for an Xarcade device when it is started. That means you need to connect your Xarcade before Xarcade2jstick is started. When using Xarcade2jstick as a service, you could shutdown the RPi, connect the Xarcade and start your Rpi again.

Uninstalling the service and/or the binary

You can uninstall the daemon with this command:

`sudo make uninstallservice`

You can uninstall the binary with this command:

`sudo make uninstall`

### Support in the RetroPie-Setup Script

If you would like to use Xarcade2Jstick in combination with a RetroPie installation:

The RetroPie-Setup Script supports the Xarcade2Jstick configuration from within the “Setup” menu. Furthermore, it contains a configuration file for the auto-config functionality of RetroArch. RetroPie is fully prepared to seamlessly work with Xarcade2Jstick.

### Conclusion
If you would like the Xarcade Tankstick to be registered as two individual game pads on a Linux machine, the program Xarcade2Jstick might be a solution for you. It exclusively captures the original keyboard events and maps these to the corresponding game pad events. Furthermore, the Shift-key functionality is also made available by Xarcade2Jstick, so that virtual keyboard presses of TAB and ESC are still possible.
Xarcade2Jstick can easiliy be installed and can also be installed and configured with the RetroPie-Setup Script.


