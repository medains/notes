#ImageMagik

From @JitGo on twitter.

Blur an image from command line

```bash
convert $1 -channel RGBA -blur 0x$2 $1-blurred.jpg 
```

* $1 = name of file
* $2 = integer amount of blue, 20 works pretty well

