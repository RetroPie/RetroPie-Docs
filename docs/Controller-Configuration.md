RetroPie supports many popular controllers out of the box. On first boot you will be prompted to configure a controller in EmulationStation. Once you finish configuring your controller, multiple configuration profiles will be automagically generated for most of the systems in RetroPie. 

Some emulators will still require manual controller configuration which will be detailed on their respective system page here in the documentation. 

You can also configure controls for individual systems and individual games. For more advanced controller configuration with libretro cores (any emulator that starts with `lr`) see the [RetroArch-Configuration](Retroarch-Configuration) page.  

**Note** that some controllers (primarily wireless or bluetooth controllers) may require special drivers to be installed through the RetroPie Setup Script which are detailed on their individual controller page.

## Controller Configuration

On first boot this menu in EmulationStation will configure your controls for both Emulationstation and RetroArch Emulators:

![welcomescreen](https://cloud.githubusercontent.com/assets/10035308/9140482/cf42f25c-3cee-11e5-8f91-c1fc1c57175c.png)

Hold down any button on your keyboard or gamepad and the name will appear at the bottom and then open up into a configuration menu:

![welcomescreengamepadname](https://cloud.githubusercontent.com/assets/10035308/9140505/f5c19e38-3cee-11e5-965e-0e4e85ddaf56.png)

Follow the onscreen instructions to configure your gamepad- if you run out of buttons just hold down a button to skip each unused button. **When you get to OK press the button you have configured as "A"**.

![welcomescreengamepadconfigure](https://cloud.githubusercontent.com/assets/10035308/9140518/0263b9c8-3cef-11e5-922f-42f790f3be91.png)

If you wish to configure more than one controller, you can do so from the start menu of emulationstation. For more details on manual controller configurations see this page [Here](RetroArch-Configuration).

See the following diagrams for reference:

| SNES Controller | 
|:---:|
|![snes_controller](https://cloud.githubusercontent.com/assets/10035308/22185414/f129dc28-e099-11e6-8524-93facf275eda.png)|

| XBox 360 Controller |
|:---:|
|![xbox360_controller](https://cloud.githubusercontent.com/assets/10035308/22185415/f12ff342-e099-11e6-8adb-d18e9c638e94.png)|

| PS3 Controller |
|:---:|
|![ps3_controller](https://cloud.githubusercontent.com/assets/10035308/22185413/f10f27de-e099-11e6-97a4-ecbbc82c9e46.png)|

### Hotkeys

Hotkeys enable you to press a combination of buttons to access functions such as saving, loading, and exiting emulators. The following chart shows the default hotkey combinations. By default, the hotkey is select so that means you hold down select while pressing another button to execute a command. **Note** that hotkeys are only specific to the retroarch/libretro based emulators.

|Hotkeys | Action|
| :---: | :---: |
| Select+Start | Exit |
| Select+Right Shoulder | Save |
| Select+Left Shoulder | Load |
| Select+Right | Input State Slot Increase |
| Select+Left | Input State Slot Decrease |
| Select+X | RGUI Menu |
| Select+B | Reset |