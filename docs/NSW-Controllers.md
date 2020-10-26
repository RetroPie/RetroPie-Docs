## Installation

First, you need to install [dkms-hid-nintendo](https://github.com/nicman23/dkms-hid-nintendo), a Nintendo HID kernel module:

```shell
git clone https://github.com/nicman23/dkms-hid-nintendo
cd dkms-hid-nintendo
sudo dkms add .
sudo dkms build nintendo -v 3.0
sudo dkms install nintendo -v 3.0
```

Then, you need [joycond](https://github.com/DanielOgorchock/joycond), a userspace driver which manages the controllers and exposes their motion inputs:


```shell
git clone https://github.com/DanielOgorchock/joycond.git
cmake .
sudo make install
sudo systemctl enable --now joycond
```
## Usage

Just like in a Ninendo Switch, after you connect it to the Raspberry Pi, you'll need to press triggers to select the position. After you press any button and the player indicator lights start blinking, do the following:

|Position/Controller|Buttons to press|
|--|--|
| One Joycon, Horizontal |Press **SR+SL**  |
|One Joycon, Vertical |Press **L and ZL** or **R and ZR**  |
|Two Joycons/Pro Controller |Press **L or ZL** and **R or ZR**  |