# GarfieldXBM

Small bitmap icons (XBM source + BMP preview) used as boot splash screens and
status icons across this account's ESP8266/Arduino OLED sketches, via
[ESP8266-Garfield-Common](https://github.com/bobhuang1/ESP8266-Garfield-Common)
and the [ESP12-GeigerCounter](https://github.com/bobhuang1/ESP12-GeigerCounter-SPI-New12864)
/ [ESP12-PianoHumidityControl](https://github.com/bobhuang1/ESP12-PianoHumidityControl-SPI-Mini12864-zh)
sketches.

| File | Used for |
|---|---|
| `Garfield.xbm` / `.bmp` | 66x64 boot splash screen |
| `mute.xbm` / `.bmp` | 12x12 mute-status icon |
| `speaker.xbm` / `.bmp` | 12x12 sound-on-status icon |
| `nuclear.xbm` / `.bmp` | 12x12 radiation/alert icon (Geiger counter sketch) |

## Usage

The `.xbm` files are C source (`u8g2`/Arduino-compatible `static const uint8_t
name[] = {...}` byte arrays with `_width`/`_height` `#define`s) - include the
one you need directly in your sketch, or copy the array into your own header,
then draw it with u8g2's `drawXBM()`:

```cpp
#include "Garfield.xbm" // defines a byte array + width/height macros
display.drawXBM(31, 0, c0c2ac37ec5e4ca883599460dfb0490e_width, c0c2ac37ec5e4ca883599460dfb0490e_height, c0c2ac37ec5e4ca883599460dfb0490e_bits);
```

The auto-generated hex-string array/macro names come from the image
conversion tool used to produce these files (e.g. an online image-to-XBM
converter) - rename them to something readable if you'd rather not reference
them by their generated name, as `ESP8266-Garfield-Common` does (it copies
the `Garfield.xbm` bit array in under the name `garfield`).

The `.bmp` files are the source images the `.xbm` files were converted from -
handy if you want to re-convert at a different size/threshold.
