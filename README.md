# Template

![](./examples/mosaic.webp)

## template.bmp

`template.bmp` is a bare-bones template showing where GBA content will go.

You can use it to start a new GIMP project or whatever it is that you use to edit images.

> [!WARNING]  
> Remember to use the locked color palette!
> 
> In GIMP, do `Image` -> `Mode` -> `RGB` (if you don't, your exports won't have the correct colors)

## template.xcf

template.xcf is a GIMP project with a modularly-designed assortment of frames.

![](./examples/gimp.png)

# Conversion

After editing your boder you can export it and run this fixer command to ensure compatibility with GBARunner3:

```bash
magick image.bmp \
    +repage \
    -alpha off \
    -depth 8 \
    -type Palette \
    -colors 256 \
    -compress none \
    BMP3:border.bmp
```

Save this in `/_gba/border.bmp` on your cart and enjoy.  

> [!TIP]
> 
> You can set per-game borders by placing borders in `/_gba/borders/<GAME_ID>.bmp` (e.g., `/_gba/border/BPRE.bmp` sets a border for Pokémon FireRed)

# Background Information

The DS screen (256x192) is slightly larger than the GBA screen (240x160), so there's empty black space around the edges:

- Top: 16 pixels
- Bottom: 16 pixels
- Left: 8 pixels
- Right: 8 pixels

We can provide a background image that is 256x192 bmp (uncompressed with version 3 header) with 8-bit color depth to fill in the margins.

> [!IMPORTANT]  
> GBARunner3 places the game **on top** of the image! **It isn't an overlay!**
> 
> You are literally *only* filling in the gaps at the edges!

