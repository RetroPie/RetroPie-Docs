## Location of the BIOS
## Updated by FreezX 12/06/13 with confirmed working BIOS configuration

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