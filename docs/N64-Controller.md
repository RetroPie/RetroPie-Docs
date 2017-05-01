From [here](http://blog.petrockblock.com/2012/10/21/the-retropie-gpio-adapter/#comment-841277725):

I recently started messing with it again and used an n64 controller instead. not only does it have more buttons, it also has less to connect, just + at pin 1 and at 6, and data at pin 7. as long as you put in

```shell
gamecon_gpio_rpi map=0,0,6,0
```

in 

```shell
/etc/modules
```

It starts right up on boot. You also need to then run

```shell
cd ~/RetroPie/emulators/RetroArch/tools
./retroarch-joyconfig
```

Then save the output to your Retropie config file (this is a lot easier if you do it by ssh, with copy paste into vi/nano) to:

```shell
~/RetroPie/configs/all/retroarch.cfg
```
