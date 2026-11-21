# view

An image viewer: PNG (any kind: grey, colour, palettes, transparency,
interlaced; 16 bits read as 8), BMP (24 and 32 bits, 8 and fewer with a
palette, uncompressed) and Netpbm (PPM, PGM, PBM, as text or binary).
MyNOS reads no JPEG.

```
mynos:/$ view /disk/picture.png &
```

The image fits the window; `+` and `-` zoom, `1` shows it at its own
size, `0` fits it again; the arrows, the wheel or a drag move a large
one. Page Up and Page Down (or P and N) go to the previous or next image
of its folder; O opens another; Q quits.
