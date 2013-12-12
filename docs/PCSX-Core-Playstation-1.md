## Location of the BIOS

Create the directory to store BIOS files:

```shell
/home/pi/RetroPie/BIOS
```

Make sure you copy your bios files into that directory with **no capitalization in any part of the name** _or_ **file extension**.

Once that is done, all you have to do is edit the file:

```shell
/RetroPie/configs/psx/retroarch.cfg
```

and add the line:

```shell
system_directory = /home/pi/RetroPie/BIOS
```

Reboot and it should find and use your BIOS.

UPDATE: the above method did not work for me.
The following did work:

Make sure the bios file(s) have all lowercase filenames (mine are called scph?????.bin) and put them in
```shell
/home/pi/RetroPie/emulatorcores
```shell
