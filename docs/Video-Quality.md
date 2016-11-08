# Why are my games so pixelated?

By default RetroPie displays games far crisper than an original console and cabling ever could. For some, this can appear jagged and harsh compared to their memories of the smoother, less refined output of old CRT televisions. Further, old games themselves were designed and tested using the same televisions, so the raw image RetroPie outputs by default may not be the original artists' intention. Fortunately, there are ways of emulating CRTs.

## What did CRTs televisions do?

### Scan lines

See https://en.wikipedia.org/wiki/Scan_line. Broadly this is the horizontal dark lines that appear when using a CRT, and also darkens the image slightly. As well as helping to look like a CRT, it also helps to make the pixels seem less jagged and helps provide definition:

![](https://retropie.org.uk/forum/uploads/files/1478613018469-upload-514e190e-162d-4917-b32d-a9e584094039-resized.png)

See also: [shadow mask](https://en.wikipedia.org/wiki/Shadow_mask)

### Bloom

This describes the effect of lighter colours (particulary white) bleeding into their surrounding pixels, again helping to make things look less jagged:

<img src="https://retropie.org.uk/forum/uploads/files/1478613483800-upload-9a6df26e-794d-42b0-a0af-feeb176b488f.png" width="25%" height="25%" />

### Signal distortion

The cabling used to connect consoles to CRTs was typically analogue and introduced noise to the image. This can have a pleasing effect by making the image smoother. Further, different broadcast regions had their own colour, resolutions, refresh and cabling standards, so a UK TV ('PAL' standard) would show the same game differently to a USA TV ('NTSC' standard).

### Curvature

Rather than today's flat screen displays, CRTs were not flat, and always featured some degree of curvature to the glass screen giving a 'fishbowl effect':

<img src="http://farm7.static.flickr.com/6163/6168494768_7cc6296f43_b.jpg" width="25%" height="25%" />

# RetroPie Alternatives

## Shaders

Shaders are small programs that a dedicated graphics chip (GPU) runs to alter the image. Unfortunately, the Raspberry Pi series features a fairly weak GPU that struggles to run complex or multiple shaders. Fortunately, user @davej has created a fantastic shader specifically for the pi, aimed at recreating a CRT appearance whilst still maintaining full speed at 1080p on even a Pi 1 (overclocked). It is highly configurable, but four presets are included in RetroPie.

### crt-pi.glslp
![](http://i.imgur.com/TuZvVXe.jpg)

### crt-pi-curvature.glslp
![](http://i.imgur.com/xsLAmVk.jpg)

The second two presets are `crt-pi-vertical.glslp` and `crt-pi-curvature-vertical.glslp`, described in (link to vertical section)

To install ....

### Vertical games

### crt-pi-vertical.glslp
![](http://i.imgur.com/oL7BOvk.jpg)

### crt-pi-curvature-vertical.glslp
![](http://i.imgur.com/I9X0SJr.jpg)

(upload cfg zip for mame2003)

## NTSC filters

## Video smooth