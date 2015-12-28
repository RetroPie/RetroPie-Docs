# Why can't I SSH as root anymore?

Starting with RetroPie 3.0 BETA 3 the root password was disabled (as is the case for Raspbian by default and many other linux distros). 

If you would like to re-enable root access, in the terminal type:

```shell
sudo passwd root
```

see these posts for more details:

https://www.raspberrypi.org/documentation/linux/usage/root.md

http://elinux.org/R-Pi_Troubleshooting#I_don.27t_know_the_root_password


**RetroPie 3.0 Jessie Builds:**

before setting a root password, the following must be edited

```sudo nano /etc/ssh/sshd_config```

look for 

```PermitRootLogin without-password```

change it to

```PermitRootLogin yes```

then ctrl+x to save, next set your root password & restart your Pi