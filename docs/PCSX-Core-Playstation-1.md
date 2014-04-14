## Location of the BIOS

The default location for the BIOS file(s) is 
```shell
cd ~/RetroPie/emulatorcores
```

Just copying the BIOS file to that directory should be enough for it to be found by the emulator.

Alternatively you can use a different directory to store the BIOS files as follows

Create the directory to store BIOS files:

```shell
mkdir ~/RetroPie/BIOS
```

Make sure you copy your bios files into that directory with **no capitalization in any part of the name** _or_ **file extension**.

Once that is done, all you have to do is edit the pcsx core config file using this command:

```shell
nano ~/RetroPie/configs/psx/retroarch.cfg
```
and add the line:
```shell
system_directory = /home/pi/RetroPie/BIOS
```
To save file and quit type ctrl + x.

Then you will see:

Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES)?

Type Y, press return.

If you're unsure and want to check to see that the file really was changed use the command:
```shell
less ~/RetroPie/configs/psx/retroarch.cfg
```
Exit by typing x.

Reboot and it should find and use your BIOS.

## BIOS files

Add different bios' that you've tested and tell the community if it works or not.

Filename      | md5                               |        CRC32          | Comment
--------------|-----------------------------------|-----------------------|-------------------
scph1001.bin  | 924e392ed05558ffdb115408c263dccf  |    37157331           | 
scph7502(41a)  | b9d9a0286c33dc6b7237bb13cd46fdee  |    318178BF           | 

