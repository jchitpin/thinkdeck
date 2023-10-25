# think-deck

A Penkasu-inspired portable PC based on a Raspberry Pi Zero 2 W, HyperPixel 4.0 display, and BM40v2 keyboard (hotswap) PCB from KPrepublic.
Dimensions are 232mm length by 98mm wide by 55mm height.

## Why would you want one?

1. It looks cool and you like the form factor!
2. You like building stuff in tiny enclosures.
3. Need a small Linux device for connecting with other IoT devices.
4. Want a portable computing device with full-sized key switches/keycaps.

## Features

1. Full-sized key switches/keycaps in a 40% ortho layout.
2. Sturdy panel mounted I/O ports for (i) micro B, (ii) full-sized HDMI, and (iii) USB A 2.0 for connecting a wireless mouse or flash drive.
3. Display with a capacitive touch screen.

## Design compromises

1. Several mm bigger in all dimensions compared to the original Penkesu.
2. Display is top aligned to increase the room below for cable management.
3. Display is relatively small because the top chassis must enclose most of the electronics.
4. No 3.5mm headphone jack. Bluetooth audio required unless connected to a monitor with a headphone jack.
5. No trackpad. :(

# Materials

* Cables and connectors
  * Break-away 0.1" 2x20-pin strip dual male header (or a Raspberry Pi with a presoldered header).
  * Micro B male OTG to USB A female cable (15cm length).
  * USB A Y-splitter cable (make sure it can transfer data; 30cm length).
  * USB A male to USB C right angle female connector (make sure the right angle connection is fairly slim; 30cm length).
  * Micro HDMI male to HDMI female cable (15cm length).
* Case
  * Gameboy Advance SP Replacement Hinges (design credit to Penk's Penkesu)
  * 3D printed parts (may require modifications depending on the part brands chosen below).
* Display
  * HyperPixel 4.0 (rectangle).
* Electronics
  * Raspberry Pi Zero 2 W (or possibly a Raspberry Pi Zero W).
  * Adafruit PowerBoost 1000C.
  * 3.7V 606090 (or similar sized) Li-Po battery.
  * SPDT Slide Switch (for powering the device).
* Fasteners
  * 14 M2x6 screws.
    * 4 screws for the screen cover.
    * 4 screws to hold the HDMI connector.
    * 4 screws to hold the USB A 2.0 connector.
    * 2 screws to hold the keyboard tray in place. 
  * 14 M2x6*3.5 threaded inserts for the screws above.
* Keyboard
  * BM40v2 hotswap PCB and 2U Stabilizer from KPrepublic.
  * BM40v2 plate from KPrepublic (optional. You could also 3D print this).
  * 47 switches (3pin RGB / 5pin RGB / 3pin SMD / 5pin SMD).
  * 47 keycaps (Cherry profile or lower recommended)

# Build guide

1. 

# Software guide
