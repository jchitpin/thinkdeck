# ThinkDeck

A Penkasu-inspired portable PC based on a Raspberry Pi Zero 2 W, HyperPixel 4.0 display, and BM40v2 keyboard (hotswap) PCB from KPrepublic.
Dimensions are 232x98x55mm.

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
2. Keyboard PCB is held in place by friction and YMMV.
3. Display is top aligned to increase cable management space.
4. Display is relatively small because the top chassis must enclose most of the electronics.
5. No 3.5mm headphone jack. Bluetooth audio required unless connected to a monitor with a headphone jack.
6. No trackpad. :(

# Materials

* Cables and connectors
  * Break-away 0.1" 2x20-pin strip dual male header (or a Raspberry Pi with a presoldered header).
  * Micro B male OTG to USB A female cable (15cm length).
  * Micro B male to USB A female cable (15cm length).
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
  * 3.7V 606090 (or similar sized) Li-Po battery. Dimensions may not exceed 91×55×7.5mm.
  * SPDT Slide Switch (for powering the device). Dimensions should not exceed 8.5x3.5mm.
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
  * 47 keycaps (Cherry profile or lower recommended).
* Miscellaneous
  * Micro SD card with Raspberry Pi OS installed (16GB minimum; Bullseye legacy version recommended as of 2023-10-24 for compatibility with the HyperPixel 4.0).
  * Kapton tape to secure PowerBoost 1000C and battery to the top chassis.
  * Superglue to mount the slide switch.
  * Soldering iron, solder, and wire.
  * Cable ties for cable management (optional).
 
# Hardware/software build guide

The build instructions are split into smaller modules to make identifying/troubleshooting problems easier. 

## Assembling the keyboard

Those with an existing 40% keyboard may consider modifying the chassis to accommodate their own board.
For mechanical keyboard novices such as myself, the instructions are straightforward with the hotswap PCB:

1. If using a keyboard plate, pop the switches into the plate with the pins facing the top of the PCB (away from the spacebar). You should hear each switch snap into place.
2. After checking the switch pins are straight, snap the plate+switches into the hotswap PCB. You should see the pins making contact with each socket on the backside of the PCB.
3. Plug the board into a computer and test whether each switch is correctly installed. Keys that do not register most likely correspond to switches with bent pins.
4. It is recommended to flash your keyboard before installing it in the case because the hardware button to enter the firmware mode is located on the backside of the PCB.

## Assembling the Raspberry Pi and HyperPixel

1. Solder the 2x20 break-away header to the Raspberry Pi (unless you bought the presoldered version).
2. Gently connect the HyperPixel to the Raspberry Pi 2x20 header. The display manufacturer Pimoroni recommends holding the display at the edges.
3. Insert your microSD card into the Raspberry Pi and power the device. See below if this results in a black screen...

### Installing HyperPixel drivers

1. You'll need 

## Cable testing

I recommend testing whether all of your cables work before installing them into the the chassis. These include the micro HDMI to HDMI connector, the USB splitter, micro B panel connector, and USB C to USB A cable.

## Assembling the ThinkDeck

I followed the order of operations described below, but feel free to assemble in the order you see fit.

0. Use a soldering iron to insert the threaded inserts each hole in the top/bottom chassis.
1. Insert the Gameboy Advance SP hinges into the bottom chassis.
2. Connect the USB C cable to the keyboard and lower that into the bottom chassis.
3. Insert the battery into the top left chassis cutout with the cable facing down and Kapton tape in place.
4. Insert both mini HDMI, microB and microB OTG cables into the Raspberry Pi.
5. Place the Raspberry Pi and Display into the top chassis cutout.
6. Solder the USB header to the PowerBoost 1000C.
7. Solder two wires to the slide switch and the PowerBoost 1000C. The wire must be long enough for the switch to reach its designated cutout.
8. Install the slide switch into its cutout and superglue in place. It is recommended to Kapton tape the wires to avoid straining the connection.
9. Install the panel mounted microB cable and connect to the PowerBoost 1000C.
10. Connect the normal microB cable to the USB header of the PowerBoost 1000C.
11. Connect the battery wire to the PowerBoost 1000C.
12. Kapton tape the PowerBoost 1000C to the top chassis.
13. Insert the HDMI cable into its cutout and fasten with 4 M2 screws.
14. Connect the USB OTG cable with the USB splitter.
15. Route one of the splitter cables to its cutout and fasten with 4 M2 screws.
16. Connect the other USB splitter cable to the keyboard cable.
17. Cable manage by distributing extra keyboard cables into the bottom chassis cutout. Additional cables in the upper chassis can be distributed to the battery compartment if needed.
18. Slide the keyboard tray wall into the bottom chassis.
19. Pop on the left, middle, and right hinge covers. The midle hinge covers should be fastened with 2 M2 screws to hold the keyboard tray in place.
20. Fasten the screen cover with 4 M2 screws.


