# Notes on flashing esp32s-01

## Install the CH340 USB-to-Serial Driver (important)

Your ESP-01 programmer uses a CH340 chip.
macOS does not include a CH340 driver, so the serial port won't show up until you install it.

WCH official macOS CH340/CH341 driver:

https://www.wch-ic.com/downloads/CH34XSER_MAC_ZIP.html


### After installation:

Reboot macOS

Plug in the ESP-01 programmer

You should see a device like:

/dev/cu.wchusbserialXXXX

## Install esptool (for flashing any firmware)

uv pip install esptool

## Put ESP-01S into flash mode

Short IO0  GND, while plugging in

Bottom row: pins 2 and 4

## Test connection

Run:

uv run esptool --port /dev/cu.wchusbserial* chip_id
should see:

Detecting chip type... ESP8266
Chip ID: 0xXXXXXXXX

## Flash firmware

Example (for a firmware.bin at address 0x00000):

uv run esptool --port /dev/cu.wchusbserial* write_flash 0x00000 firmware.bin

# WLED notes:

I used this controller: https://www.tindie.com/products/gumslone/neopixel-ws2812sk6812-wled-fastled-controller/

## Panel setup
256 leds, GRB, start at top right, serpentine
Button configured for IO0 button. In Macros, short press set to 1, to activate Playlist 1 which uses toggle function

# STL notes:
I used this 3d print as a base: https://makerworld.com/en/models/122272-16x16-led-matrix-frame-with-diffuser-grid?from=search#profileId-131744
I had to modify the depth of the back to support the thickness of the circuit on its side, and make room for it to be pressed against the side for the button to be accessible.
The stand gets in the way with both of the obvious holes necessary for the power cord. I just drilled a 4mm hole rather than fix it.
The diffuser and front are unchanged. Diffuser was printed in cold white pla, and the rest in matte black PLA.
