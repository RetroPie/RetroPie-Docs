
# Introduction

Gamecon_gpio_rpi is a kernel module which allows interfacing various retro gamepads with Raspberry Pi's GPIO. It's based on the gamecon module from Linux Input Driver project, but has some additions and modifications. The goal is make the driver simple but versatile, making it easy and cheap to use gamepads with Pi. Most pads can be connected with just a few wires, although controller sockets provide a more lasting way for those who have them.

# Controller support
The driver supports up to 4 controllers of the following types (can be mixed freely):
* NES gamepads
* SNES gamepads and mouses
* PSX/PS2 gamepads, wheels and DDR controllers
* N64 gamepads
* Gamecube gamepads

# GPIO interface
Depending on the number and type of pads, the interface needs 3 to 11 gpio pins. Pi's GPIO data pins operate at 3.3V, and 3.3V power pin is rated at max. 50mA (see [here](http://elinux.org/RPi_Low-level_peripherals) for more info). This generates a few very important rules, which should be read before connecting any gamepads.

1. All gamepads must use 3.3V supply regardless which they were designed for. Some older controllers (e.g. NES, SNES) are speficied for 5V, but they should operate fine with 3.3V. 5V power pin shouldn't be used without using level shifters on the data pins, so don't use it unless you know what you are doing.

2. The current limit is sufficient for 4 normal controllers, but e.g. 3rd party pads with extra leds, fans etc. should be avoided.

The pinout summary can be seen below. The power and ground pins are common for all pads, thus requiring splitters (e.g. a breadboard) when using multiple pads. Detailed information on connecting the pads can be found at the module's README (/usr/share/doc/gamecon_gpio_rpi/README.gz).

![GPIO interface for gamecon](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_gpio_rpi.png)

The actual interconnect (NES/SNES/N64) can be made from female-to-female jumper wires and a single conductor wires with the other end folded in double (see [here](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_n64.jpg) and [here](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_wires.jpg)). For PSX pads, the jumper wires are enough [by themselves](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_psx.jpg). The only hard one is GC pad, which must be opened to make a good connection for the wires.

# Installation and usage
The easiest way to install the module is with RetroPie-script. Just remember to upgrade your firmware before installing the module, as it is built automatically using the configuration data from the newest kernel. Loading the module is done with modprobe, which is explained in detail in the README  (/usr/share/doc/gamecon_gpio_rpi/README.gz).

# TODO
* add support for the changed pinout of [rev2 board](http://www.raspberrypi.org/archives/1929#comments)
* add support for N64's rumble pak

# Version history
### 0.5
* first DKMS-enabled version
* added support for GC and PSX controllers

### 0.3
* first release