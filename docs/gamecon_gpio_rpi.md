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

The pinout summary can be seen below. The power and ground pins are common for all pads, thus requiring splitters (e.g. a breadboard + pinheaders) when using multiple pads. Detailed information on connecting the pads can be found at the module's README (/usr/share/doc/gamecon_gpio_rpi/README.gz).

NOTE: Board revision 2 has different GPIO ID:s for PAD1 & PAD2 pins, which must be taken into account when loading the driver.

![GPIO interface for gamecon](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_gpio_rpi.png)

The actual interconnect (NES/SNES/N64) can be made from female-to-female jumper wires and a single conductor wires with the other end folded in double (see [here](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_n64.jpg) and [here](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_wires.jpg)). For PSX pads, the jumper wires are enough [by themselves](http://www.niksula.hut.fi/~mhiienka/Rpi/images/gamecon_psx.jpg). The only hard one is GC pad, which must be opened to make a good connection for the wires.

# Installation and usage
The easiest way to install the module is with RetroPie-script. Just remember to upgrade your firmware before installing the module, as it is built automatically using the configuration data from the latest RPi kernel. This also means that a fw update afterwards can break the compatibility, but this is easily fixed by reconfiguration/update of the module (see FAQ). Loading the module is done with modprobe, which is explained in detail in the README  (/usr/share/doc/gamecon_gpio_rpi/README.gz). In addition of install/update, Retropie also contains an option to permanently enable configuration for 2 SNES pads connected to PAD2 & PAD3 pins (designed for RetroPie GPIO Adapter). Permanent configuration can be done manually by adding a corresponding configuration line (e.g. "gamecon_gpio_rpi map=0,2") to /etc/modules .

# Questions and feedback
Related [thread](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=78&t=15787) in Raspberry Pi forum.

# TODO
* add support for N64's rumble pak

# FAQ
* **Q: I get these errors when loading the module: "ERROR: could not insert 'gamecon_gpio_rpi': Exec format error", "gamecon_gpio_rpi: disagrees about version of symbol module_layout"**
* A: This means that the module has not been built against the current kernel version. This can happen if firmware is not up-to-date during installation, or by a firmware update afterwards. To fix this, run "Install/update multi-console gamepad drivers for GPIO"-option in RetroPie.

* **Q: NES pads only report A-button correctly, or do not react at all**
* A: NES controllers are designed to be used with 5V supply, and are not guaranteed to work dirctly with 3.3V supply. Based on various reports, pads tested seem to fall into 3 categories:

1. _Fully 3.3V compliant_. The pads falling into this category can be powered directly from 3.3V supply as described above, and do not need any extra hardware.

2. _3.3V logic level compatible_. These pads need to be powered from 5V supply (pin P1-02 on the RPi pin header) for correct operation, but RPi output pins (NES_CLK, NES_LTC) can be directly connected to corresponding pad input pins. A protection circuit is strongly recommended between pad output data pin and RPi input pin (PAD1-4), since output logic level is now 5V and input pins are not 5V-tolerant. It can be built from a [3.3V zener diode and resistor](http://www.daycounter.com/Circuits/Level-Translators/Level-Translator-Zener-Clamp.gif), or by using an IC such as 74LVC245.

3. _Only 5V compliant_. Otherwise same as previous, but NES_CLK and NES_LTC must be converted to 5V logic level to be recognizable by the pad. That can be done with 74HCT244 - see [this](http://www.raspberrypi.org/forums/viewtopic.php?f=78&t=15787&start=214) post for more info.

* **Q: PSX pads do not operate reliably or at all**
* A: Try raising psx pad access delay with "psx_delay"-option (see README). Default value is set to 10 (us) to minimize the performance penalty caused by the driver, and with 25 all pads should be guaranteed to work.

* **Q: N64/GC pads do not operate reliably**
* A: These pads use an asynchronous communication prototol, and the bitbanging done by the driver assumes a fixed CPU frequency within certain limits. Power-saving features may break the operation, and should be disabled when using N64/GC pads. You can check whether frequency scaling is active by looking at /sys/devices/system/cpu/cpu0/cpufreq/scaling_* -nodes. It can be disabled by selecting "performance"-governor - see [this](https://wiki.debian.org/HowTo/CpuFrequencyScaling) page for more info.

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