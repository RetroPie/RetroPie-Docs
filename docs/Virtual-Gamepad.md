![Virtual Gamepad](https://github.com/miroof/node-virtual-gamepads/raw/resources/screenshots/standalone.png?raw=true)
***
_This project is the result of hard work from Miroof. https://github.com/miroof/node-virtual-gamepads_
***

Install from the experimental menu of the setup script (may only work well with a rpi2)

## Usage

Once the nodejs application is launched, you just have to plug your gamepad controller by connecting your device on the same local network and by reaching the address _http://node_server_adress_ (i.e. your Raspberry Pi's IP address) on your choice of web browser (Chrome Mobile is recommended).

## Use it as a Smartphone Application (Chrome for Android)

With the add to homescreen chrome feature, you can easily use virtual gamepads application without launching the browser each time you want to play.

With only 3 clicks, virtual gamepads web application becomes a standalone application.

![](https://github.com/miroof/node-virtual-gamepads/raw/resources/screenshots/standalone_step1.png?raw=true) | ![](https://github.com/miroof/node-virtual-gamepads/raw/resources/screenshots/standalone_step2.png?raw=true)

Then a shortcut is added on your homescreen and the application will be launched outside the browser.

![](https://github.com/miroof/node-virtual-gamepads/raw/resources/screenshots/standalone_step3.png?raw=true) | ![](https://github.com/miroof/node-virtual-gamepads/raw/resources/screenshots/standalone_step4.png?raw=true)

## Enjoy Haptic Feedbacks

Because it's difficult to spot the right place in a touch screen without looking at it, the touch zone of each button was increased. LT button was moved at the center of the screen to let as much space as possible for the joystick and avoid touch mistakes.

![Virtual Gamepad Layout](https://github.com/miroof/node-virtual-gamepads/raw/resources/schemas/touch_zones.png?raw=true)

To know if we pressed a button with success, the web application provides an haptic feedback which can be easily deactivated by turning off the vibrations of the phone.

**You will need to configure your controller with EmulationStation and RetroArch just like you would any other controller.**


You can also install manually using these steps:

```
### Install Node.js

sudo apt-get update && sudo apt-get upgrade
wget http://node-arm.herokuapp.com/node_latest_armhf.deb
sudo dpkg -i node_latest_armhf.deb


### Install Virtual Gamepad (Must Be Run As Root!)

su
git clone https://github.com/miroof/node-virtual-gamepads
cd node-virtual-gamepads
npm install


### Enable Virtual Gamepad on Boot

sudo npm install pm2 -g
sudo pm2 start main.js
sudo pm2 startup
sudo pm2 save
```