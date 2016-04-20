### Memory Split

***NOTE:*** Earlier versions of RetroPie included a default EmulationStation theme with large image files, that would eventually cause a 'white screen' when too many systems were active. Now the default theme ('Carbon') is much lighter so there is no reason to change the split unless you choose a heavier theme. Emulation itself uses very little video memory.

Also note that in order to ensure sensible memory splits across Pi models, RetroPie utilises the gpu_mem_256, gpu_mem_512 and gpu_mem_1024 overrides, which apply to Pis with that amount of memory (for example, the Pi 2 has 1024MB memory, so will use the gpu_mem_1024 setting). This setting **_overrides_** the gpu_mem setting that is described below, so if you still want to adjust the memory split, you will have to manually edit /boot/config.txt and adjust the relevant value, or delete the lines entirely.

***

Since the raspberry pi is a SoC the CPU and GPU share the same amount of RAM. The following option allows you to choose how much RAM you allocate to the GPU compared to the CPU.

![advanced](https://cloud.githubusercontent.com/assets/10035308/10713851/061f690e-7a93-11e5-9ed1-86981e7c9325.png)

![advanced2](https://cloud.githubusercontent.com/assets/10035308/10713853/290b82cc-7a93-11e5-92ec-0b94aaa60185.png)

You can choose a split from 16/32/64/128/256 (the settings may be different depending on the version of pi you have)

![gpu](https://cloud.githubusercontent.com/assets/10035308/10713855/53c539b8-7a93-11e5-9016-2117e8a890ad.png)