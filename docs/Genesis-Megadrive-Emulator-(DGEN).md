![Sega Genesis](http://upload.wikimedia.org/wikipedia/en/1/12/GenesisLogo.png)![Megadrive](http://upload.wikimedia.org/wikipedia/en/a/a8/Megadrive_logo.png)
***
The Emulator for the Sega Genesis/Megadrive is DGEN. See the source here: http://dgen.sourceforge.net/

CONTROLLER CONFIGS

**Method 1**

Setting up an "exit"-button (from [here](http://blog.petrockblock.com/forums/topic/dgen-over-composite-video/#post-1770) ):

I edit the dgenrc file in ```/RetroPie/configs/all/```:

```shell
# Quit DGen or switch to the next ROM on the command-line.
key_quit = escape
joy_quit = joystick0-button12
```


**Method 2**

Edit the retroarch.cfg file in ```/RetroPie/configs/all/```:

```shell
input_exit_emulator = "escape"
-input_exit_emulator_btn = "nul"
+input_exit_emulator_btn = "7"
```