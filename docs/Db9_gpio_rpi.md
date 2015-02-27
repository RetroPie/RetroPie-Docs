# Introduction
Db9_gpio_rpi is a driver (kernel module) for DB9 joysticks and gamepads connected to Raspberry Pi's GPIO. The driver is adapted from parport-targeted db9 kernel module to GPIO, and has some additions and modifications. Connection of db9 joysticks to RPi's GPIO requires no extra hardware in most cases, providing easy and cheap way for using retro joysticks with RPi.

# Joystick support
The list of supported db9 joysticks is below. Since the number of GPIO pins is limited, only 2 joysticks can be used simultaneously.
* Atari, Commodore, Amiga etc. db9 multisystem joysticks (1-3 buttons)
* Sega Mega Drive (Genesis) pads
* Sega Saturn controllers (Note: custom connector instead of db9)
* Amiga CD32 pads

# GPIO interface
The available GPIOs are divided into 2 ports, PORT1 and PORT2. Both use 7 data pins, which are in identical locations on all RPi board variants. Additionally, the joysticks require either ground, or both ground and power pins depending on the type. These pins are common for both ports.

Pi's GPIO data pins operate at 3.3V and aren't 5V tolerant (see [this](http://elinux.org/RPi_Low-level_peripherals)), so 3.3V '''must''' be used for joysticks requiring power even though they'd be designed for 5V. However, some TTL-based joysticks may not function correctly using 3.3V supply. If they need to be powered from 5V, level shifters must be added between output pins of joystick and GPIO input pins. For example, 74LVC245 is an IC which can be used for this downconversion.

Below is an illustration which shows the pins used by the driver, with the mappings listed in a table next to it. Pin numbers are identical for all board revisions: the image represents the complete gpio block for A/B boards, and the top portion of the gpio block of A+/B+/Model B boards.
<table border=0><tbody><tr><td>
<img src="http://www.niksula.hut.fi/~mhiienka/Rpi/images/db9_gpio_rpi.png"></img>
</td><td>
<table border=1>
  <tbody>
    <tr>
      <td><b>Button/Function</b></td>
      <td><b>PORT1 GPIO pin</b></td>
      <td><b>PORT2 GPIO pin</b></td>
    </tr>
    <tr>
      <td>UP</td>
      <td>4</td>
      <td>15</td>
    </tr>
    <tr>
      <td>DOWN</td>
      <td>7</td>
      <td>17</td>
    </tr>
    <tr>
      <td>LEFT</td>
      <td>8</td>
      <td>18</td>
    </tr>
    <tr>
      <td>RIGHT</td>
      <td>9</td>
      <td>22</td>
    </tr>
    <tr>
      <td>FIRE1</td>
      <td>10</td>
      <td>23</td>
    </tr>
    <tr>
      <td>FIRE2 / SELECT1</td>
      <td>11</td>
      <td>24</td>
    </tr>
    <tr>
      <td>FIRE3 / SELECT0</td>
      <td>14</td>
      <td>25</td>
    </tr>
  </tbody>
</table>
</td></tr></tbody></table>

## Joystick connection matrix
| DB9 pin | Atari basic joystick | C64 joystick | MD/Genesis pad | Saturn controller (non-db9) | CD32 pad |
| ------- | -------------------- | ------------ | -------------- | --------------------------- | -------- |
| 1       | UP                   | UP           | UP             | -                           | UP       |
| 2       | DOWN                 | DOWN         | DOWN           | DOWN                        | DOWN     |
| 3       | LEFT                 | LEFT         | LEFT           | UP                          | LEFT     |
| 4       | RIGHT                | RIGHT        | RIGHT          | SELECT0                     | RIGHT    |
| 5       | -                    | -            | 3.3V           | SELECT1                     | SELECT0  |
| 6       | FIRE1                | FIRE1        | FIRE1          | 3.3V                        | SELECT1  |
| 7       | -                    | 3.3V         | SELECT0        | RIGHT                       | 3.3V     |
| 8       | GND                  | GND          | GND            | LEFT                        | GND      |
| 9       | -                    | -            | FIRE2          | GND                         | FIRE1    |

More information on the connections is provided in the driver README (/usr/share/doc/db9_gpio_rpi/README.gz).

# Usage
The module is loaded and configured with modprobe. This is explained shortly in the parent page and in detail in the driver README. The joystick IDs for modprobe are listed below:

| ID | Description                   |
| --- | ----------------------------- |
| 0  | (No joystick)                 |
| 1  | Multisystem 1-button joystick |
| 2  | Multisystem 2-button joystick |
| 3  | Multisystem 3-button joystick |
| 4  | MD/Genesis pad (3+1 buttons)  |
| 5  | MD/Genesis pad (5+1 buttons)  |
| 6  | MD/Genesis pad (6+2 buttons)  |
| 7  | Sega Saturn controller        |
| 8  | Amiga CD32 gamepad            |

# Questions and feedback
Related [thread](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=78&t=15787) in Raspberry Pi forum.

# FAQ
* Q: I get these errors when loading the module: "ERROR: could not insert 'db9_gpio_rpi': Exec format error", "db9_gpio_rpi: disagrees about version of symbol module_layout"
* A: This means that the module has not been built against the current kernel version. This can happen if the fw is not up-to-date during installation, or by a fw update afterwards. To fix this, run "Install/update multi-console gamepad drivers for GPIO"-option in RetroPie setup.


# Version history
### 1.0 (27.2.2015)
* Added support for RPi2
* Fixed issues with 3rd-party MD pads

### 0.7 (28.4.2013)
* first release