# Introduction
Db9_gpio_rpi is a driver (kernel module) for DB9 joysticks and gamepads connected to Raspberry Pi's GPIO. The driver is adapted from parport-targeted db9 kernel module to GPIO, and has some additions and modifications. Connection of db9 joysticks to RPi's GPIO requires no extra hardware in most cases, providing easy and cheap way for using retro joysticks with RPi.

# Controller support
The list of supported db9 joysticks is below. Since the number of GPIO pins is limited, only 2 joysticks can be used simultaneously.
* Atari, Commodore, Amiga etc. db9 multisystem joysticks (1-3 buttons)
* Sega Mega Drive (Genesis) pads
* Sega Saturn controllers (Note: custom connector instead of db9)
* Amiga CD32 pads

# GPIO interface
The available GPIOs are divided into 2 ports, PORT1 and PORT2. Both use 7 data pins, which are in identical locations on both rev1 and rev2 Pi boards. Additionally, the joysticks require either ground, or both ground and power pins depending on the type. These pins are common for both ports.

Pi's GPIO data pins operate at 3.3V and aren't 5V tolerant (see [this](http://elinux.org/RPi_Low-level_peripherals)), so 3.3V '''must''' be used for pads requiring power even though they'd be designed for 5V. However, some TTL-based joysticks may not function correctly using 3.3V supply. If they need to be powered from 5V, level shifters must be added between output pins of joystick and GPIO input pins. For example, 74LVC245 is an IC which can be used for this downconversion.

The following image shows the pins used by the driver, and are listed in the table below.

![GPIO interface for db9](http://www.niksula.hut.fi/~mhiienka/Rpi/images/db9_gpio_rpi.png)

Button/Function | PORT1 GPIO pin | PORT2 GPIO pin
----------------|----------------|---------------
UP              | 4              | 15
DOWN            | 7              | 17
LEFT            | 8              | 18
RIGHT           | 9              | 22
FIRE1           | 10             | 23
FIRE2 / SELECT1 | 11             | 24
FIRE3 / SELECT0 | 14             | 25

# Usage
The module is loaded and configured with modprobe. This is explained shortly in the parent page and in detail in the driver README (/usr/share/doc/db9_gpio_rpi/README.gz).

# Questions and feedback
Related [thread](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=78&t=15787) in Raspberry Pi forum.

# FAQ
* Q: I get these errors when loading the module: "ERROR: could not insert 'db9_gpio_rpi': Exec format error", "db9_gpio_rpi: disagrees about version of symbol module_layout"
* A: This means that the module has not been built against the current kernel version. This can happen if the fw is not up-to-date during installation, or by a fw update afterwards. To fix this, run "Install/update db9"-option in RetroPie.


# Version history
### 0.7 (28.4.2013)
* first release