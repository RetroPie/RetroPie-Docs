From [here](http://blog.petrockblock.com/2012/10/21/the-retropie-gpio-adapter/#comment-841277725):

i recently started messing with it again, and used an n64 controller instead. not only does it have more buttons, it also has less to connect, just + at pin 1 gnd at 6, and data at pin 7. as long as you put in

```shell
gamecon_gpio_rpi map=0,0,6,0
```

in 

```shell
/etc/modules
```

it starts right up on boot. you also need to run

```shell
cd ~/RetroPie/emulators/RetroArch/tools
./retroarch-joyconfig
```

and save the output to your retropie config file (this is a lot easier if you do it by ssh, with copy paste into vi/nano) to

```shell
~/RetroPie/configs/all/retroarch.cfg
```
