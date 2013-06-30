### Folders and Locations

According to [this post](http://blog.petrockblock.com/forums/topic/intellivision-emulation/#post-2208):

I put my exec.bin and grom.bin in:
```shell
/usr/local/share/jzintv/rom
```
This is one of the two paths that the emulator is set to look in. The jzintv and subfolder rom did not exist so I had to create them..
```shell
cd /usr/local/share
sudo mkdir jzintv
sudo mkdir jzintv/rom
```
and then I moved the exec.bin and gbrom.bin file from my intellivision rom directory:
```shell
sudo mv ~/RetroPie/roms/intellivision/* /usr/local/share/jzintv/rom
```

Then I was able to launch my intellivision roms… hope this helps!