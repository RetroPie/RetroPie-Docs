Just redirected the output of the wolf3d-binary:

> Wolf4SDL was not compiled for these data files:
> vgahead.wl6 contains a wrong number of offsets (159 instead of 150)!

> Please check whether you are using the right executable!
> (For mod developers: perhaps you forgot to update NUMCHUNKS?)

So it turns out that this compiled version will only run with files from version 1.4 of the game.
(It seems that it also could be recompiled somehow so that it will work with the different version.)