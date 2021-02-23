
***
![](https://raw.githubusercontent.com/wiki/opentyrian/opentyrian/opentyrian_torm.png)

***
_OpenTyrian is a port of the DOS shoot-em-up Tyrian. Jason Emery generously gave the OpenTyrian developers a copy of the Tyrian 2.1 source code, which has since been ported from Turbo Pascal to C. The port uses SDL, making it easily cross-platform._

***
## Emulator: [OpenTyrian](https://github.com/opentyrian/opentyrian/wiki)

This emulator can be installed from the [Retropie Setup script](Updating-RetroPie#manage-packages)

## Controls:

```
ctrl-backspace -- kill OpenTyrian
alt-enter      -- fullscreen
ctrl-f10       -- ungrab mouse

arrow keys     -- ship movement
space          -- fire weapons
enter          -- toggle rear weapon mode
ctrl/alt       -- fire left/right sidekick
```

### Configuring Game Controllers

You can configure controllers in-game by starting a game in any mode, episode or difficulty - it doesn't matter which. From the pre-game menu, choose `Options` and then `Joystick`. If you have a game controller plugged in, then you will see a screen as below with buttons and axes already assigned.

![opentyrian-joystick](https://cloud.githubusercontent.com/assets/8166945/21713337/6231b3ba-d3f1-11e6-870c-cb090ed45ce5.png)

Bear in mind that the button and axes numbering in OpenTyrian is the number as reported by [jstest](RetroArch-Configuration#determining-button-values) +1. For example, button 0 on your controller will register as `BTN 1`.

To re-configure, use the arrow keys on a keyboard to select an action, FIRE, CHANGE FIRE etc. Press ENTER on a keyboard to highlight and then the button on your game controller that you wish to map. Repeat for other buttons.

To remove a default setting, press the relevant button for the action. For example, to remove the default setting of `BTN 1` for FIRE, navigate to FIRE with a keyboard, press ENTER and then press button 0 on your controller.

The settings will be saved to a configuration file, `opentyrian.cfg`, in the `/opt/retropie/configs/ports/opentyrian` folder. It is possible to manually edit this file if you prefer, just remember to add one to the button or axis number as reported by jstest.
