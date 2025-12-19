## Minecraft TTF

This python script converts Minecraft: Java Edition [font definition files](https://minecraft.wiki/w/Font#Providers) to [TrueType Fonts (TTFs)](https://en.wikipedia.org/wiki/TrueType).

By default, the script downloads the latest snapshot jar, reads all the font definitions, and generates regular, bold, italic, and bold italic font files corresponding to each. Currently, that includes `default` (the normal game font), `alt` (the enchantment table font), `illageralt` (an unused font from Minecraft Dungeons), and `uniform` (which is empty, see below).

Other Minecraft TTFs floating around tend to be outdated (using the pre-1.13 bitmap) or don't contain the complete set of characters. Using this script will ensure you have a perfectly matching set.

The `ttf` and `unihex` providers are not supported. Vanilla does not use the `ttf` provider, but it does use the `unihex` provider to create the `uniform` font and add fallbacks to the `default` font. Merging in the entirety of [GNU Unifont](https://en.wikipedia.org/wiki/GNU_Unifont) is useful for vanilla text, but is contrary to the goals of this project.

### Display Tips

These fonts are very accurate, and should look good in any program that uses vector graphics to draw text at any scale. When rasterizing text in programs like [GIMP](https://en.wikipedia.org/wiki/GIMP), the font will be pixel-perfect accurate when its height is set to a multiple of 12 pixels. Make sure the line and letter spacing are whole integers.

These TTFs can be imported back into Minecraft with a `ttf` provider, and perfectly match the vanilla fonts. Make sure to use a `size` of 12 instead of the default 11. Italic text will be antialiased; you can increase `oversample` to around 4 to make it a closer match.

***
made this so i could make fonts for my kobo libra2's koreader's ui lol <br>
i just added some notes and instructions - so someone like me, who hasnt touched programming or python before, could understand this somehow 😗

## using the python script

1. install python 3.11.x from (https://python.org/downloads/windows) <br>***(from the stuff i've found, it said it needed python 3.13, but 3.11.9 worked for me anyways)***
> make sure u've checked
> - "add python to PATH"
> - "pip"
> - "py launcher"
> - "install for all users"
> - and "precompile standard library"

2. open command prompt and run `python -m pip install --upgrade pip` twice
3. run `python -m pip install fonttools`, `python -m pip install pillow`, `python -m pip install pygame`, and `python -m pip install requests` <br>
   **order doesn't matter**
4. download this repo's zip file and extract its contents into a new folder - *i put mine in `"C:\mcfonts_converter"`*, 

   <img src="https://github.com/mcantc/minecraft-ttf/blob/master/github%20code%20zip%20download.png?raw=true" width="270" align="centre">

   > your folder (`mcfonts_converter`) should contain `.gitignore`, `README.md`, `main.py`, `pyproject.toml`, and `uv.lock`
   >
   ><img src="https://github.com/mcantc/minecraft-ttf/blob/master/repo%20folder%20preview.png?raw=true" width="540" align="centre">

5. open cmd and run `python main.py`

   <img src="https://github.com/mcantc/minecraft-ttf/blob/master/file%20explorer%20cmd%20search%20bar.png?raw=true" width="540" align="centre">

   if it had run successfully, it should end in a "Done!" and have two new folders called `cache` and `out` in `mcfonts_converter` <br>
   with your .ttf font file(s) - in my case - in `C:\mcfonts_converter\out`
   
## choosing your texture pack font to convert

open `\cache\minecraft.jar` with 7zip

replace `\assets\minecraft\textures\font\ascii.png` to your texture pack's desired font texture (must also be "ascii.png")

change main.py's `letter_spacing` and `chatbox_height`'s values for font formatting preferences
> optional: leave as is for 16x texture packs but might cut off the top of the glyph

|texturepack / ascii.png res|chatbox_height|
| --- | --- |
| <b>16x pack<br>128x128 | 16 |
| <b>32x pack<br>256x256 | 20 |
| <b>64x pack<br>512x512 | only found how to use<br> up to 32x so far |

then do step 5 and recheck `C:\mcfonts_converter\out` for your new font
