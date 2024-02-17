# ThinkDeck

A Penkesu-inspired portable PC that incorporates my favourite design elements of old ThinkPads

![](https://github.com/jchitpin/think-deck/blob/main/images/profile.jpg?raw=true)
![](https://github.com/jchitpin/think-deck/blob/main/images/profile-angled.jpg)

## Why would you want one?

1. It looks cool and you like the (slightly chunky) form factor.
2. You need a small(-ish) Linux box, possibly for connecting with other IoT devices.
3. You want a portable computing/note taking device with support for full-sized key switches/keycaps.

## Features

1. Full-sized key switches/keycaps in a 40% ortho layout.
2. Panel mounted I/O ports for (i) micro B charging, (ii) HDMI display, and (iii) USB A 2.0 port.
3. Capactive touch screen display.
4. Visible LED indicators for battery management status (from the PowerBoost 1000C).
5. Power switch enclosed within the case to prevent accidental power toggling.
6. Dimensions are 232x98x55mm (L x W x H).
7. INSERT WEIGHT! (printed in PETG)

Insert pictures here (TBD).

## Design comprises compared to the original Penkesu

1. Several millimetres longer in all dimensions compared to the original Penkesu.
2. Display is relatively small because most electronics are enclosed in the top chassis.
3. No 3.5mm headphone jack. Bluetooth audio required unless connected to a monitor via HDMI.
4. No trackpoint. :(
5. Kickstand required to prevent the device from tipping onto the screen at a normal viewing angle.

# Materials

* Cables and connectors
  * Break-away 0.1" 2x20-pin strip dual male header (or a Raspberry Pi with a presoldered header).
  * Micro B male OTG to USB A female cable (15cm length).
  * Micro B male to USB A female cable (15cm length).
  * USB A Y-splitter cable (make sure it can transfer data;  30cm length).
  * USB A male to USB C right angle female connector (make sure the right angle connection is fairly slim; 30cm length).
  * Micro HDMI male to HDMI female cable (15cm length).
* Case
  * 6mm wide plastic/wooden/metal dowels or Gameboy Advance SP replacement hinges.
  * 3D printed parts.
* Electronics
  * Raspberry Pi Zero 2 W (or possibly a Raspberry Pi Zero W).
  * Adafruit PowerBoost 1000C.
  * HyperPixel 4.0 (rectangle) display.
  * 3.7V 606090 or up to 755590 Li-Po battery. Dimensions may not exceed 91×55×7.5mm (length x width x depth).
  * SPDT Slide Switch (for powering the device). Dimensions should not exceed 8.5x3.5mm (length x width).
* Fasteners
  * For HDMI holder (optional)
    * 4 M2x6x3.5mm or M2x8x3.5mm threaded inserts.
    * 4 M2x6mm or M2x8mm screws.
  * For USB-A holder (optional)
    * 4 M2x6x3.5mm or M2x8x3.5mm threaded inserts.
    * 4 M2x6mm or M2x8mm screws.
  * For screen cover
    * 4 M2x6x3.5mm or M2x8x3.5mm threaded inserts.
    * 4 M2x6mm or longer screws (to a max length of 16mm).
  * Middle hinge cover (threaded inserts required with M2 screws!)
    * 2 M2x4x3.5mm threaded inserts.
    * 2 M2x4mm screws.
* Keyboard
  * BM40v2 hotswap PCB with included 2U Stabilizer from KPrepublic.
  * BM40v2 plate from KPrepublic. (Optional and you could also 3D print this)
  * 47 switches compatible with the PCB. (3pin RGB / 5pin RGB / 3pin SMD / 5pin SMD)
  * 47 keycaps. (Cherry profile or lower recommended but 11.9mm OEMs should fit without touching the upper case when closed)
* Miscellaneous
  * Micro SD card with Raspberry Pi OS installed (16GB minimum; Bullseye legacy version recommended as of 2023-10-24 for compatibility with the HyperPixel 4.0 rectangle).
  * A phone kickstand. (I used an ESR branded kickstand.)
  * Kapton tape to secure PowerBoost 1000C and battery to the top chassis.
  * Epoxy or super glue for glueing the hinge covers and hinge mechanisms.
  * Soldering iron, solder, and wire.
  * Utility knife.
  * Cable ties. (Optional)
 
# Hardware/software build guide

The build instructions are split into the following sections: 

## Modifying the 3D prints (optional)

You may need/want to modify the chassis design depending on the size of your components. These include:

1. Modifying the micro B connector panel cutout.
2. Modifying the HDMI panel cutout.
3. Modifying the USB A panel cutout.
4. Modifying the chassis dimensions to accommodate the length/width of your keyboard.
5. Adding your own custom screen cover design rather than the standard 30 degree grill.

Because many cable connectors have similar dimensions, you could also shave the plastic housing to fit inside the panel cutouts.

## Assembling the keyboard

Those with an existing 40% keyboard should consider modifying the chassis to accommodate their own board.
For mechanical keyboard novices such as myself, the instructions are straightforward for the hotswap PCB:

1. If using a keyboard plate, pop the switches into the plate with the pins in the same direction and aligned with the PCB. You should hear each switch snap into place.
2. After checking the switch pins are straight, snap the plate+switches into the hotswap PCB. You should see the pins making contact with each socket on the backside of the PCB.
3. Plug the board into a computer and test whether each switch is correctly installed. Keys that do not register most likely correspond to switches with bent pins that are not contacting the socket.
4. It is recommended to flash your keyboard before installing it in the case because it can be tricky to enter the bootloader afterwards.
  * Bootmagic reset: Hold down the key at (0,0) in the matrix (the top left key) and plug in the keyboard.
  * Physical reset button: Briefly press the button labeled 'RST' on the back of the PCB.

## Flashing the keyboard

1. Install QMK and follow their instructions to flash your own keyboard.
2. See the following link for details:
  * https://github.com/rgoulter/qmk_firmware/tree/bm40hsrgb_rev2/keyboards/kprepublic/bm40hsrgb/rev2
  * https://docs.qmk.fm/#/
3. Configure your keyboard locale:
  * `$sudo raspi-config`
  * 5 Localisation Options
  * L3 Keyboard
  * Generic (any one works).
  * Pick one (English (US) for my keymapping).
  * The default for the keyboard layout.
  * Choose one (I picked No compose key).
  * Chose one (I picked <No>).

## Assembling the Raspberry Pi and HyperPixel

1. Solder the 2x20 break-away header to the Raspberry Pi (unless you bought the presoldered version like I did).
2. Gently connect the HyperPixel to the Raspberry Pi 2x20 header. The display manufacturer Pimoroni recommends holding the display at the edges.
3. Insert your microSD card into the Raspberry Pi and power the device. See below if this results in a black screen...

### Installing HyperPixel drivers if the HyperPixel & Pi boots to a black screen

1. I successfully got the display working with a legacy version of Raspberry OS (based on Bullseye dated 2023-12-05 rather than Bookworm).
4. Install the HyperPixel drivers and correct the touchscreen orientation by adding the following lines to the config file. (See: https://github.com/pimoroni/hyperpixel4/issues/177#issuecomment-1932650705)

## Cable testing and modifications

I recommend testing whether all of your cables work before installing them into the the chassis. These include the micro HDMI to HDMI connector, the USB splitter, micro B panel connector, and USB C to USB A cable.
Because the cables need to fit into the top chassis, it is recommended to (carefully!) strip the outer plastic sheathing to reduce cable bulk. See the final assembly pictures for more details.

## Assembling the ThinkDeck chassis

1. Carefully trim off supports from the 3D prints. A pair of needle nosed pliers is great for removing supports inside the panel cutouts.
3. Insert the GBA hinges or dowels into the bottom chassis hinge holes.
4. Carefully epoxy/superglue the exposed GBA hinges/dowels to the hinge grooves of the top chassis. Make sure the glue does not seep into the bottom chassis hinge holes!
5. When dried (roughly 5 minutes), epoxy/superglue the left and right 3D printed hinge caps to enclose the hinges/dowels.
6. Optional: sand/prime/sand/paint/clear coat. (I just didn't bother because I liked the look).

## Fit-testing cable panel cutouts

1. You will probably need to sand/shave down the cable enclosures to fit snugly inside the top chassis.
1. A pair of curved needle nose pliers is great pushing the USB/HDMI connectors into their respective cutouts.

## PowerBoost 1000C soldering

Consult the PowerBoost 1000C documentation for pinouts and assembly instructions: https://cdn-learn.adafruit.com/downloads/pdf/adafruit-powerboost-1000c-load-share-usb-charge-boost.pdf

1. Solder the included USB header to the PowerBoost 1000C PCB.
2. Connect the battery to the PowerBoost 1000C via the JST connector or solder the wires directly to the board (what I did).
3. Solder the on/off switch (SPDT Slide Switch) to the PowerBoost 1000C. 

## Assembling the ThinkDeck

I followed the order of operations described below, but feel free to assemble in the order you see fit.

### Top chassis steps

1. Insert the battery coupled to the PowerBoost 1000C and slide switch into the top chassis with the microB charging cable facing the battery (left).
2. Mount the microB cable into its cutout and connect the microB cable to the PowerBoost 1000C, routing excess cable to the bottom of the chassis.
3. Mount the USB splitter cable and HDMI cable into their panel cutouts. 
4. Plug the mini HDMI to HDMI, microB, and microB OTG cables into the HyperPixel/Raspberry Pi. Make sure the microB OTG cable is cable managed such that it pokes out the top left part of the HyperPixel display.
5. Insert the microB charging cable into the PowerBoost 1000C USB header.
6. Insert the HyperPixel/Raspberry Pi + cables into the top chassis.
7. Install the USB and HDMI holders to prevent the panel cutouts from moving.
8. Carefully insert the on/off switch into the "cup holder" of the HDMI holder.
9. Connect the USB splitter to the USB OTG cable.

### Bottom chassis steps

1. Connect the USB cable to the keyboard PCB and install into the bottom chassis.
2. Route the USB A connector to the top chassis and in between the Raspberry Pi and HyperPixel, emerging just below the USB OTG connector.
3. Secure the excess keyboard USB cabling inside the bottom chassis compartment using cable ties.
4. Insert the keyboard divider into the bottom chassis to hide the excess keyboard USB cabling.
5. Insert cardstock/paper spacers surrounding the keyboard if there is excess PCB wiggle room inside the bottom chassis.
6. Connect the keyboard USB A header to the USB splitter.

### Finishing touches

1. Tape down any wires that are sticking out.
2. Tape down the USB A headers to the battery.
3. Insert the 4 threaded inserts to fasten the top chassis screen cover using a soldering iron. Take care not to melt the chassis walls!
5. Insert the 2 threaded inserts to fasten the bottom chassis middle hinge cover.
6. Fasten the screen cover to the top chassis with M2 screws.
7. Fasten the middle hinge cover to the bottom chassis with M2 screws.
8. Install the quickstand to the back of the bottom chassis. It should come with 3M tape so additional glue shouldn't be necessary.

# Conclusion

Congratulations you have successfully built your very own ThinkDeck! I'd like to give a shout out to Penk for inspiring me to build my own cyberdeck.

