## Wireless Receiver

To use wireless Xbox 360 controllers, you will also need a USB wireless receiver plugged into your Raspberry Pi. The Official Microsoft Xbox 360 receiver or a generic brand like zettaguard, VicTsing will work. You can pair multiple controllers to a single wireless receiver. Play and charging cables will not work.

To pair your controller(s) with the wireless receiver:

- turn on your wireless Xbox 360 controller (hold down the _Guide_ button)
- press the connect button on the receiver (green light will start flash)
- then press the tiny connect button on the top of the controller
- you will need to repeat these steps to pair each additional controller

## Automatic Configuration
### Xpad Linux kernel driver

Starting with the RetroPie 4.1 SD image, the `xpad` driver is already installed by default, manual installation is not necessary when starting with the Raspberry Pi image. 

You access the driver through **Manage packages ➤ Manage driver packages ➤ xpad ** and the driver can be installed/updated from source. After the installation, a reboot is necessary and then the gamepad can be configured in EmulationStation.

An example working config (that was generated from the EmulationStation configuration) is listed below at `/opt/retropie/configs/all/retroarch-joypads/Xbox360WirelessReceiver(XBOX).cfg`

``` ini
input_device = "Xbox 360 Wireless Receiver (XBOX)"
input_driver = "udev"
input_r_y_plus_axis = "+4"
input_l3_btn = "9"
input_r_x_minus_axis = "-3"
input_l_btn = "4"
input_load_state_btn = "4"
input_start_btn = "7"
input_exit_emulator_btn = "7"
input_l_y_minus_axis = "-1"
input_up_btn = "13"
input_r_y_minus_axis = "-4"
input_a_btn = "1"
input_b_btn = "0"
input_reset_btn = "0"
input_down_btn = "14"
input_l_x_plus_axis = "+0"
input_l_y_plus_axis = "+1"
input_r_btn = "5"
input_save_state_btn = "5"
input_r2_axis = "+5"
input_r3_btn = "10"
input_right_btn = "12"
input_state_slot_increase_btn = "12"
input_x_btn = "3"
input_menu_toggle_btn = "3"
input_select_btn = "6"
input_enable_hotkey_btn = "6"
input_l_x_minus_axis = "-0"
input_y_btn = "2"
input_left_btn = "11"
input_state_slot_decrease_btn = "11"
input_r_x_plus_axis = "+3"
input_l2_axis = "+2"
```

### Xpad driver options

The `xpad` kernel module has the option to interpret the shoulder triggers as button inputs instead of treating the trigger as Axis type inputs. This kind of configuration was default in RetroPie until April 2024 to fix an incompatibility with older EmulationStation version, but since this configuration causes conflicts with SDL's gamepad mappings for Xbox wired controllers, it has been removed.

If you wish to retain the previous behavior or to fix the detection of buttons for gamepads that just mimic an Xbox 360 controller (in order to maintain compatibility with Windows), then running the following command will add back the 'trigger to buttons' option to the `xpad` configuration:

``` sh
echo "options xpad triggers_to_buttons=1" | sudo tee  /etc/modprobe.d/xpad.conf 
```
After the command is executed, reboot the system or reload the `xpad` driver in order for the `xpad` configuration to be applied.

## Xboxdrv userspace driver

/// warn | Note
There are known incompatibilities with this driver when used in it's default configuration with the latest Linux kernels. The `xpad` driver is currently the best option to simply make an Xbox 360 or Xbox One controller operational in RetroPie.

These incompatibilities are not an issue when [using xboxdrv as a calibration and key-mapping tool](Universal-Controller-Calibration-&-Mapping-Using-xboxdrv) for almost any gamepad, including the Xbox 360 controller. When used this way, it's even possible for both xpad and xboxdrv to coexist together.
///

Access the [RetroPie Setup Script](Updating-RetroPie) and navigate to **Manage Packages ➤ Manage driver packages ➤ xboxdrv**.

![xboxdrv](https://cloud.githubusercontent.com/assets/10035308/12218229/d397607e-b6d6-11e5-8a99-f3106d60425a.png)

After installation, the following the options are available to configure the driver:

1. **Enable xboxdrv:** This will configure the `xboxdrv` service to start automatically, by adding the start-up command to `/etc/rc.local`.
2. **Disable xboxdrv:** This will disable the driver by removing the start-up commoand from `/etc/rc.local`.
3. **Set Number of Controllers To Enable:** Default number of controllers is 2 (If you have more than two controllers, set this first before you enable xboxdrv).
4. **Set Analog Stick Deadzone:** Smaller number = more responsive, Larger number = less responsive.

After you have enabled the driver and rebooted you'll need to reconfigure your controller(s) in EmulationStation as described on the [first installation page](First-Installation#controller-configurations).
