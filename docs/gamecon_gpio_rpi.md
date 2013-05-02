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

1. All gamepads must use 3.3V supply regardless which they were designed for. Some older controllers (e.g. NES, SNES) are speficied for 5V, but they should operate fine with 3.3V (with a few exceptions - see FAQ). 5V power pin shouldn't be used without using level shifters or clamps on the input data pins, so don't use it unless you know what you are doing.

2. The current limit is sufficient for 4 normal controllers, but e.g. 3rd party pads with extra leds, fans etc. should be avoided, if they are powered from the main supply.

The pinout summary can be seen below. The power and ground pins are common for all pads, thus requiring splitters (e.g. a breadboard + headers) when using multiple pads. Detailed information on connecting the pads can be found at the module's README (/usr/share/doc/gamecon_gpio_rpi/README.gz).

NOTE: Board revision 2 has different GPIO ID:s for PAD1 & PAD2 pins, which must be taken into account when loading the driver.

![GPIO interface for gamecon](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_gpio_rpi.png)

The actual interconnect (NES/SNES/N64) can be made from female-to-female jumper wires and a single conductor wires with the other end folded in double (see [here](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_n64.jpg) and [here](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_wires.jpg)). For PSX pads, the jumper wires are enough [by themselves](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_psx.jpg). The only hard one is GC pad, which must be opened to make a good connection for the wires.

# Installation and usage
The easiest way to install the module is with RetroPie-script. Just remember to upgrade your firmware before installing the module, as it is built automatically using the configuration data from the latest RPi kernel. This also means that a fw update afterwards can break the compatibility, but this is easily fixed by reconfiguration/update of the module (see FAQ). Loading the module is done with modprobe, which is explained in detail in the README  (/usr/share/doc/gamecon_gpio_rpi/README.gz). In addition of install/update, Retropie also contains an option to permanently enable configuration for 2 SNES pads connected to PAD2 & PAD3 pins (designed for RetroPie GPIO Adapter).

# Questions and feedback
Related [thread](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=78&t=15787) in Raspberry Pi forum.

# TODO
* add support for N64's rumble pak

# FAQ
* Q: I get these errors when loading the module: "ERROR: could not insert 'gamecon_gpio_rpi': Exec format error", "gamecon_gpio_rpi: disagrees about version of symbol module_layout"
* A: This means that the module has not been built against the current kernel version. This can happen if the fw is not up-to-date during installation, or by a fw update afterwards. To fix this, run "Install/update gamecon"-option in RetroPie.

* Q: Nes pad(s) do not react
* A: Some NES pad revisions don't work with 3.3V supply. You can use 5V supply if you build a protection circuit for the input data pin. An example circuit from a common 1N4148 diode and resistor is shown [here](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=78&t=15787&p=263001#p263001). The clamp can also be built from a [zener diode and resistor](http://www.daycounter.com/Circuits/Level-Translators/Level-Translator-Zener-Clamp.gif).

* Q: PSX pads do not operate reliably or at all
* A: Try raising the psx pad access delay with "psx_delay"-option (see README). Default value is set to 10 (us) to minimize the performance penalty caused by the driver.


# Version history
### 0.9 (17.10.2012)
* added support for rev.2 board gpio pins
* improved robustness with N64 / GC pad reads
* improved performance with PSX controllers
* restore _psx_delay_-option for setting psx access delay

### 0.5 (27.8.2012)
* first DKMS-enabled version
* added support for GC and PSX controllers

### 0.1 (7.8.2012)
* first release