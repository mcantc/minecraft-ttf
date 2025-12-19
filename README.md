made this so i could make fonts for my kobo libra2's koreader's ui lol <br>
i just added some notes - so someone like me, who hasnt touched programming or python before, could understand this to some point idk

## using python

1. install python 3.11.x from (https://python.org/downloads/windows) <br>***(from the stuff i found, it said it needed python 3.13, but 3.11.9 worked for me anyways)***
> make sure u've checked
> - "add python to PATH"
> - "pip"
> - "py launcher"
> - "install for all users"
> - and "precompile standard library"

2. `open command prompt` and run `python -m pip install --upgrade pip` twice
3. run `python -m pip install fonttools`, `python -m pip install pillow`, `python -m pip install pygame`, and `python -m pip install requests`
   -order doesn't matter

## choosing your texture pack font to convert
replace `\assets\minecraft\textures\font\ascii.png` to your texture pack's desired font texture (must also be "ascii.png")

open `\cache\minecraft.jar` with 7zip

change lines `114` and `130 's` values for font formatting preferences (letter spacing and height)

## Minecraft TTF

This python script converts Minecraft: Java Edition [font definition files](https://minecraft.wiki/w/Font#Providers) to [TrueType Fonts (TTFs)](https://en.wikipedia.org/wiki/TrueType).

By default, the script downloads the latest snapshot jar, reads all the font definitions, and generates regular, bold, italic, and bold italic font files corresponding to each. Currently, that includes `default` (the normal game font), `alt` (the enchantment table font), `illageralt` (an unused font from Minecraft Dungeons), and `uniform` (which is empty, see below).

Other Minecraft TTFs floating around tend to be outdated (using the pre-1.13 bitmap) or don't contain the complete set of characters. Using this script will ensure you have a perfectly matching set.

The `ttf` and `unihex` providers are not supported. Vanilla does not use the `ttf` provider, but it does use the `unihex` provider to create the `uniform` font and add fallbacks to the `default` font. Merging in the entirety of [GNU Unifont](https://en.wikipedia.org/wiki/GNU_Unifont) is useful for vanilla text, but is contrary to the goals of this project.

### Display Tips

These fonts are very accurate, and should look good in any program that uses vector graphics to draw text at any scale. When rasterizing text in programs like [GIMP](https://en.wikipedia.org/wiki/GIMP), the font will be pixel-perfect accurate when its height is set to a multiple of 12 pixels. Make sure the line and letter spacing are whole integers.

These TTFs can be imported back into Minecraft with a `ttf` provider, and perfectly match the vanilla fonts. Make sure to use a `size` of 12 instead of the default 11. Italic text will be antialiased; you can increase `oversample` to around 4 to make it a closer match.
