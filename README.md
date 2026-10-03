# GarfieldXBM

Small bitmap icons (XBM source + BMP preview) for boot splash screens and
status icons on ESP8266/Arduino OLED projects, used by
[ESP8266-Functions-Common](https://github.com/bobhuang1/ESP8266-Functions-Common)'s
`BootSplashBitmap` library and the
[ESP12-GeigerCounter](https://github.com/bobhuang1/ESP12-GeigerCounter-SPI-New12864)
/ [ESP12-PianoHumidityControl](https://github.com/bobhuang1/ESP12-PianoHumidityControl-SPI-Mini12864-zh)
sketches.

| File | Used for |
|---|---|
| `Garfield.xbm` / `.bmp` | 66x64 boot splash screen |
| `mute.xbm` / `.bmp` | 12x12 mute-status icon |
| `speaker.xbm` / `.bmp` | 12x12 sound-on-status icon |
| `nuclear.xbm` / `.bmp` | 12x12 radiation/alert icon (Geiger counter sketch) |

## Usage

Each `.xbm` file is C source: a `static const unsigned char <name>_bits[]
U8X8_PROGMEM` array plus `<name>_width` / `<name>_height` macros, where
`<name>` is `garfield`, `mute`, `speaker` or `nuclear`. `U8X8_PROGMEM` keeps
the bitmap in flash (required on AVR, where u8g2 reads XBM data with
`pgm_read_byte`, and it saves RAM on ESP8266), so include the file after
`U8g2lib.h`, then draw it with u8g2's `drawXBM()`:

```cpp
#include <U8g2lib.h>
#include "Garfield.xbm" // garfield_bits, garfield_width, garfield_height
display.drawXBM(31, 0, garfield_width, garfield_height, garfield_bits);
```

The `.bmp` files are the source images the `.xbm` files were converted from -
handy if you want to re-convert at a different size/threshold.

## Copyright note

Garfield is a trademark of and © Paws, Inc. All rights reserved.
`Garfield.xbm` and `Garfield.bmp` are **not** covered by this repository's GPL
license: they are a fan-made conversion of a copyrighted character for
personal, non-commercial hobby use only. Replace them with your own artwork
for anything you distribute.


## License

This project is free software, released under the **GNU General Public License v3.0**, except for the Garfield files described above. You may redistribute and/or modify it under those terms; see [LICENSE.md](LICENSE.md) for the full text.

Contributors: run `git config core.hooksPath .githooks` once to enable the repository's commit-message hook.
