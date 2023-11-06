# ThinkDeck

A Penkasu-inspired portable PC that incorporates my favourite design elements of old ThinkPads. Dimensions are 232x98x55mm (L x W x H).

## Why would you want one?

1. It looks cool and you like the (chunky) form factor.
2. You need a small(-ish) Linux box, possibly for connecting with other IoT devices.
3. You want a portable computing device with support for full-sized key switches/keycaps.

## Features

1. Full-sized key switches/keycaps in a 40% ortho layout.
2. Sturdy panel mounted I/O ports for a (i) micro B, (ii) full-sized HDMI, and (iii) USB A 2.0 for connecting a wireless mouse or flash drive.
3. Display with a capacitive touch screen.
4. Visible LED indicators for battery management status (from the PowerBoost 1000C).

## Design compromises

1. Several millimetres longer in all dimensions compared to the original Penkesu.
2. Display is relatively small because most of the electronics are enclosed in the top chassis.
3. No 3.5mm headphone jack. Bluetooth audio required unless connected to a monitor via HDMI.
4. No trackpoint. :(
5. The keyboard USB is outside the case because of internal space constraints. But this also means the ThinkDeck doubles as a portable keyboard!

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
  * 3.7V 606090 (or similar sized) Li-Po battery. Dimensions may not exceed 91×55×7.5mm (length x width x depth).
  * SPDT Slide Switch (for powering the device). Dimensions should not exceed 8.5x3.5mm (length x width).
* Fasteners
  * HDMI holder
    * 4 M2x6x3.5mm or M2x8x3.5mm threaded inserts.
    * 4 M2x6mm or M2x8mm screws.
  * USB-A holder
    * 4 M2x6x3.5mm or M2x8x3.5mm threaded inserts.
    * 4 M2x6mm or M2x8mm screws.
  * Screen cover 
    * 4 M2x6x3.5mm or M2x8x3.5mm threaded inserts.
    * 4 M2x6mm or longer screws (to a max length of 16mm).
  * Middle hinge cover
    * 2 M2x4x3.5mm threaded inserts.
    * 2 M2x4mm screws.
* Keyboard
  * BM40v2 hotswap PCB with 2U Stabilizer from KPrepublic.
  * BM40v2 plate from KPrepublic (optional. You could also 3D print this).
  * 47 switches compatible with the PCB (3pin RGB / 5pin RGB / 3pin SMD / 5pin SMD).
  * 47 keycaps (Cherry profile or lower recommended but 11.9mm OEMs should fit without touching the upper case when closed).
* Miscellaneous
  * Micro SD card with Raspberry Pi OS installed (16GB minimum; Bullseye legacy version recommended as of 2023-10-24 for compatibility with the HyperPixel 4.0 rectangle).
  * Kapton tape to secure PowerBoost 1000C and battery to the top chassis.
  * Soldering iron, solder, and wire.
  * Cable ties for cable management (optional).
 
# Hardware/software build guide

The build instructions are split into chunks to identify/troubleshoot possible problems. 

## Modifying the 3D prints (optional)

You may need/want to modify the chassis design depending on the size of your components. These include:

1. Modifying the micro B connector panel cutout.
2. Modifying the HDMI panel cutout.
3. Modifying the USB A panel cutout.
4. Modifying the chassis dimensions to accommodate the length/width of your keyboard.
5. Adding your own custom screen cover design rather than the standard 30 degree grill.

Because most cable connectors have standard sizes, you could also shave the plastic housing to fit inside the panel cutouts. This would avoid modifying the model.

## Assembling the keyboard

Those with an existing 40% keyboard should consider modifying the chassis to accommodate their own board.
For mechanical keyboard novices such as myself, the instructions are straightforward with the hotswap PCB:

1. If using a keyboard plate, pop the switches into the plate with the pins in the same direction and aligned with the PCB. You should hear each switch snap into place.
2. After checking the switch pins are straight, snap the plate+switches into the hotswap PCB. You should see the pins making contact with each socket on the backside of the PCB.
3. Plug the board into a computer and test whether each switch is correctly installed. Keys that do not register most likely correspond to switches with bent pins that are not contacting the socket.
4. It is recommended to flash your keyboard before installing it in the case because the hardware button to enter the firmware mode is located on the backside of the PCB.

## Assembling the Raspberry Pi and HyperPixel

1. Solder the 2x20 break-away header to the Raspberry Pi (unless you bought the presoldered version).
2. Gently connect the HyperPixel to the Raspberry Pi 2x20 header. The display manufacturer Pimoroni recommends holding the display at the edges.
3. Insert your microSD card into the Raspberry Pi and power the device. See below if this results in a black screen...

### Installing HyperPixel drivers

1. I successfully got the display working with a legacy version of Raspberry OS (based on Bullseye rather than Bookworm).
2. 

## Cable testing and modifications

I recommend testing whether all of your cables work before installing them into the the chassis. These include the micro HDMI to HDMI connector, the USB splitter, micro B panel connector, and USB C to USB A cable.
Because the cables need to fit into the top chassis, it is recommended to (carefully!) strip the plastic wrapping to reduce cable bulkiness. See the final assembly pictures for more details.

## Cleaning up 3D prints

1. Trim off supports.
2. Optional: sand/prime/sand/paint/clear coat. (I just didn't bother because I liked the raw "industrial" look).

## Fit-testing cable panel cutouts

1. You will probably need to sand/shave down the cable enclosures to fit snugly inside the top chassis.
2. A pair of curved needle nose pliers is great pushing the USB/HDMI connectors into their respective cutouts.

## Assembling the ThinkDeck

I followed the order of operations described below, but feel free to assemble in the order you see fit.

1. 

0. Use a soldering iron to insert the threaded inserts in each hole in the top/bottom chassis.
1. Insert the Gameboy Advance SP hinges into the bottom chassis and connect the top/bottom chasses.
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


