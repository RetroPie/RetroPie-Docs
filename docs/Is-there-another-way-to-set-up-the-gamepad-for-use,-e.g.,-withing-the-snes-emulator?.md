In terminal, browse to the folder where the retroarch-joyconfig is. Default should be 

    cd /home/pi/RetroPie/RetroArch-Rpi/tools

Then use the command 

    ./retroarch-joyconfig

This will get the joyconfig running. The output of this tool must be appended to the file ~/RetroPie/configs/all/retroarch.cfg.

By default, retroarch-joyconfig just dumps to the console. You can specify for retroarch-joyconfig to write to a file with the -o argument, e.g.:

    ./retroarch-joyconfig -o ~/RetroPie/configs/all/retroarch.cfg