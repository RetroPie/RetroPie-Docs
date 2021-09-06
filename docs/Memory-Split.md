## Memory Split

Raspberry Pi systems use a shared memory architecture, allocating memory for GPU (2d, 3d and video) and CPU tasks. It is possible to manually set this allocation, however there is typically no reason to adjust it as the defaults are correct. As per the [official documentation](https://www.raspberrypi.org/documentation/computers/config_txt.html#memory-options):
> Unlike GPU's found on x86 machines, where increasing memory can improve 3D performance, the architecture of the VideoCore means **there is no performance advantage from specifying values larger than is necessary, and in fact it can harm performance**.

### Adjusting the Memory Split

**NOTE**: Please be mindful of the platform-specific notes below, before changing any settings.

![advanced](https://cloud.githubusercontent.com/assets/10035308/10713851/061f690e-7a93-11e5-9ed1-86981e7c9325.png)

![advanced2](https://cloud.githubusercontent.com/assets/10035308/10713853/290b82cc-7a93-11e5-92ec-0b94aaa60185.png)

You can choose a split from 16/32/64/128/256 (the settings may be different depending on the version of Pi you have)

![gpu](https://cloud.githubusercontent.com/assets/10035308/10713855/53c539b8-7a93-11e5-9016-2117e8a890ad.png)

### Raspberry Pi 4

On the Raspberry Pi 4 the 3D component of the GPU has its own memory management unit (MMU), and does not use memory from the `gpu_mem` allocation. Instead memory is allocated dynamically within Linux. Increasing this amount can ***harm*** emulation performance.

#### Kodi

Previously, the FKMS driver still utilised the memory split for certain media tasks, e.g., hardware video decoding for 4K (HEVC) video. If you have issues with 4K videos in Kodi, upgrade to the latest kernel/firmware, for example via _RetroPie-Setup -> Configuration / Tools -> raspbiantools -> Upgrade Raspbian packages_.

### Raspberry Pi 0-3

If you don't use the RetroPie provided image, and you install using the [manual installation method](Manual-Installation), you have to adjust the memory split settings manually before installation to reserve at enough video memory for running Emulationstation without problems. The default values used by the RetroPie image are:
~~~~
gpu_mem_256=128
gpu_mem_512=256
gpu_mem_1024=256
~~~~

In order to ensure sensible memory splits across older Pi models, the RetroPie Pi image uses the `gpu_mem_256`, `gpu_mem_512` and `gpu_mem_1024` overrides, which apply to Pis with that amount of memory (for example, the Pi 2 has 1024MB memory, so will use the `gpu_mem_1024` setting). These settings **_override_** the `gpu_mem` setting, so if you still want to adjust the memory split, you will have to manually edit `/boot/config.txt` and adjust the relevant value, or delete the lines entirely. 

These defaults should be adequate, and you can test via observing the GPU memory usage whilst an emulator is running. A complex display of the GPU memory usage can be viewed with:
~~~
sudo vcdbg reloc
~~~
