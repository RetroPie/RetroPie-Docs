From [here](https://github.com/petrockblog/RetroPie-Setup/issues/130#issuecomment-14105633):

Setting
```
disable_overscan=1
```
in `/boot/config.txt` might solve video problems for certain setups (removes black bars around the edges). If you have installed from NOOBS, there might be 4 other lines relating to overscan directions in the config.txt, such as `overscan_left`, `overscan_top`, etc. You should deactivate these lines by placing a `#` as the first character on these lines. 

Also, setting
```
hdmi_drive=2
```
seems to solve issues related to HDMI in some cases.