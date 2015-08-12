It's the Select button in RetroArch. By default, it's right shift.

Sometimes there are conflicts between the hotkeys and insert coin buttons so they need to be swapped manually in the retroarch.cfg in order for the select key to insert coins properly.

For example you can switch the hotkey button to a button that you don't use:

so in mame retroarch.cfg
```
/opt/retropie/configs/mame-mame4all/retroarch.cfg
```

you could add 
```
input_enable_hotkey_btn = 5
```
which would make the hotkey the left bumper (on my controller- may be a different button for yours) then the select key should work for inserting coins. but in the future in order to exit mame I would then have to press left bumper+start as i changed my hotkey to the left bumper. 

You can do the same thing for fba-libretro
```
/opt/retropie/configs/fba/retroarch.cfg
```
