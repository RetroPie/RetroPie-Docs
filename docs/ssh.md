# SSH

SSH stands for secure shell. You can remotely connect to the raspberry pi terminal with an SSH client. A popular ssh client is [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

When you first start putty you can sign in with the following credentials:

![putty](https://cloud.githubusercontent.com/assets/10035308/10655671/23eaa6b2-7834-11e5-8c85-9266c5ab808a.png)

You can also use your raspberry pi's ip address instead of `retropie`

### Default Login:

username: **pi**

password: **raspberry**

### User Root

If you wish to log in as user root you first need to set the root password from the terminal with

`sudo passwd root`

and type your new root password.

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
**Retropie Setup Script:**
```
cd RetroPie
sudo ./retropie_setup.sh
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