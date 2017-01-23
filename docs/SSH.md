# SSH

SSH stands for secure shell. You can remotely connect to the raspberry pi terminal with an SSH client. A popular ssh client is [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) 

**NOTE** Your Raspberry Pi needs to be connected to the same network (either via Ethernet or Wifi Dongle) as the computer you are accessing it from. 

When you first start putty you can sign in with the following credentials:

![putty](https://cloud.githubusercontent.com/assets/10035308/10655671/23eaa6b2-7834-11e5-8c85-9266c5ab808a.png)

You can also use your raspberry pi's ip address instead of `retropie`

### Default Login:

username: **pi**

password: **raspberry**

See [here](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-cant-i-ssh-as-root-anymore) if you wish to log in as root.

## Some common terminal commands:

**Reboot:** 
```
sudo reboot
```
**Shutdown:** 
```
sudo shutdown -h now
```
**Change Directory**
```
cd /path/to/directory
```
**list Files in Current Directory**
```
ls
```
**Retropie Setup Script:**
```
sudo /home/pi/RetroPie-Setup/retropie_setup.sh
```
**Edit Files with Nano:** 
```
sudo nano /path/to/file.txt
```
**Change owner to Pi:**
```
sudo chown pi:pi filetobechanged
```
**Change owner of folder and all files in folder to Pi:**
```
sudo chown -R pi:pi /folder/to/be/changed
```

**Make shell script executable:**
```
sudo chmod +x yourshellscript.sh
```

### Extra Configurations

If you find that you are getting weird characters on the dialog gui for the RetroPie Setup script you can change the font encoding to make it look pretty again.

![font encoding](https://cloud.githubusercontent.com/assets/10035308/14335542/4353385c-fc19-11e5-98a3-abc555191190.PNG)
![font encodingfinal](https://cloud.githubusercontent.com/assets/10035308/14335541/43404ed6-fc19-11e5-8b7c-12c9321edb4b.PNG)
