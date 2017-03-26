Draft page...

"Overscan" is the term used to describe the practice of TVs hiding the extreme edges of the picture they receive. In old CRT TVs this was because the edge of the tube would have produced a bad image, so the viewable area was reduced. This has since become a broadcast standard so there is often garbage and computer signals carried on the border of television broadcasts, so even HDTVs presume these extreme edges should be hidden. You can read more about overscan [here](https://www.engadget.com/2010/05/27/hd-101-overscan-and-why-all-tvs-do-it/).

The various components of RetroPie typically don't account for overscan, and will often include important information across the entire image. For this reason, overscan can be an issue.

## My image is cut off!

For this reason, a common scenario is that part of the image is 'cut off'. For example:

![](https://retropie.org.uk/forum/uploads/files/1486482968213-upload-fc5e98db-7e40-4375-8033-9ca4afeed159.png)

The easiest way to fix it is to adjust your TV. Modern HDTVs will usually have a setting somewhere in the options that displays the entire 1080p image, including the areas that would be ignored as "overscan". For example:
### Samsung
Menu > Picture > Screen Adjustment > Picture Size > change to "Screen Fit"
### Pioneer
Look for "Dot by Dot". 

(please add more examples if you work it for your TV!)

## My image has a border!

This should be a rarer scenario. In this case you need to do some configuration changes ...