This tutorial assumes that you start with a fresh Raspbian image right after the first boot.
If not started automatically, run

    sudo raspi-config

and select

    expand_rootfs, finish, reboot

You can check your free disk space with

    df -h

/dev/root is your main partition. Then, I would recommend to update and upgrade the existing APT packages with

    sudo apt-get update; sudo apt-get upgrade;

After that, we install the needed packages for the RetroPie setup script:

    sudo apt-get install -y git dialog

Then we download the latest RetroPie setup script with

    cd
    git clone git://github.com/petrockblog/RetroPie-Setup.git

The script is executed with

    cd RetroPie-Setup
    chmod +x retropie_setup.sh
    sudo ./retropie_setup.sh

The screen should look like this then:

![Tutorial-Installation1](https://github.com/petrockblog/RetroPie-Setup/raw/master/wiki/images/tutorial_installation1.png)

For the first installation, we choose the binaries-based installation, which takes only a few minutes. We start the installation simply by pressing ENTER.

When everything is finished you will see this screen:

![Tutorial_Installation2](https://github.com/petrockblog/RetroPie-Setup/raw/master/wiki/images/tutorial_installation2.png)