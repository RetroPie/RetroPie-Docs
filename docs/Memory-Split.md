### Memory Split

***NOTE:*** Earlier versions of RetroPie included a default EmulationStation theme with large image files, that would eventually cause a 'white screen' when too many systems were active. This 'white screen' bug has been fixed as of RetroPie 4.2, and since emulation itself uses very little video memory: **there is no benefit to raising the video memory split**.

Also note that in order to ensure sensible memory splits across Pi models, the RetroPie Pi image uses the `gpu_mem_256`, `gpu_mem_512` and `gpu_mem_1024` overrides, which apply to Pis with that amount of memory (for example, the Pi 2 has 1024MB memory, so will use the `gpu_mem_1024` setting). These settings **_override_** the `gpu_mem` setting that is described below, so if you still want to adjust the memory split, you will have to manually edit _/boot/config.txt_ and adjust the relevant value, or delete the lines entirely. 

**Note**: If you don't use the RetroPie provided image for Raspberry Pi and you install using the [manual installation method](Manual-Installation), you have to adjust the memory split settings manually before installation to reserve at enough video memory for running Emulationstation without problems. The default values used by the RetroPie image are:

~~~~
gpu_mem_256=128
gpu_mem_512=256
gpu_mem_1024=256
~~~~

A complex display of the GPU memory usage can be viewed with:

~~~
sudo vcdbg reloc
~~~


***

Since the raspberry pi is a SoC the CPU and GPU share the same amount of RAM. The following option allows you to choose how much RAM you allocate to the GPU compared to the CPU.

![advanced](https://cloud.githubusercontent.com/assets/10035308/10713851/061f690e-7a93-11e5-9ed1-86981e7c9325.png)

![advanced2](https://cloud.githubusercontent.com/assets/10035308/10713853/290b82cc-7a93-11e5-92ec-0b94aaa60185.png)

You can choose a split from 16/32/64/128/256 (the settings may be different depending on the version of pi you have)

![gpu](https://cloud.githubusercontent.com/assets/10035308/10713855/53c539b8-7a93-11e5-9016-2117e8a890ad.png)