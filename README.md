# ThinkDeck

A Penkesu-inspired portable PC that incorporates my favourite design elements of old ThinkPads

![](https://github.com/jchitpin/think-deck/blob/main/images/profile.jpg)
![](https://github.com/jchitpin/think-deck/blob/main/images/profile-angled.jpg)
![](https://github.com/jchitpin/think-deck/blob/main/images/action-shot.jpg)

## Why would you want one?

1. It looks cool and you like the (slightly chunky) form factor.
2. You need a small(-ish) Linux box, possibly for connecting with other IoT devices.
3. You want a portable computing/note taking device with support for full-sized key switches/keycaps.

## Features

1. Full-sized key switches/keycaps in a 40% ortho layout.
2. Panel mounted I/O ports for (i) micro B charging, (ii) HDMI display (and therefore audio via monitor), and (iii) USB A 2.0 port.
3. Capactive touch screen display.
4. Visible LED indicators for battery management status (from the PowerBoost 1000C).
5. Power switch enclosed within the case to prevent accidental power toggling.
6. Dimensions are 232x98x55mm (L x W x H).
7. INSERT WEIGHT! (PETG)

Insert pictures here (TBD).

## Design compromises compared to the original Penkesu

1. Several millimetres longer in all dimensions.
2. Display is relatively small because most electronics are enclosed in the top chassis.
3. Kickstand required to prevent the device from tipping onto the screen at a normal viewing angle.

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
 
# Build guide

## Modifying the 3D prints (optional)

You may need/want to modify the chassis design depending on the size of your components. These include:

1. Modifying the micro B connector panel cutout.
2. Modifying the HDMI panel cutout.
3. Modifying the USB A panel cutout.
4. Modifying the chassis dimensions to accommodate the length/width of your keyboard.
5. Adding your own custom screen cover design rather than the standard 30 degree grill.

## Cable testing and modifications

I recommend testing whether all of your cables work before installing them into the the chassis. These include the micro HDMI to HDMI connector, the USB splitter, micro B panel connector, and USB C to USB A cable.
I also recommend (carefully!) stripping the outer plastic sheathing to reduce cable bulk and wrapping with a thin layer of Kapton tape. Shaving plastic off the USB connectors may also be needed to fit them inside the panel cutouts.

## Assembling the top and bottom ThinkDeck chassis

1. Carefully trim off supports from the 3D prints. A pair of needle nose pliers is great for removing supports inside the panel cutouts.
2. Insert the GBA hinges or dowels into the bottom chassis hinge holes.
3. Carefully epoxy/superglue the exposed GBA hinges/dowels to the hinge grooves of the top chassis. Make sure the glue does not seep into the bottom chassis hinge holes!
4. When dry, epoxy/superglue the left and right 3D printed hinge caps to enclose the hinges/dowels.
5. Optional: sand/prime/sand/paint/clear coat.

## Bottom chassis

### Heat-setting the threaded brass inserts

5. Insert the two threaded inserts that fasten the middle hinge cover using a hot soldering iron.

### Assembling the keyboard

Those with an existing 40% keyboard should consider modifying the chassis to accommodate their own board.
For mechanical keyboard novices such as myself, the instructions are straightforward for the hotswap PCB:

1. If using a keyboard plate, pop the switches into the plate with the pins in the same direction and aligned with the PCB. You should hear each switch snap into place.
2. After checking the switch pins are straight, snap the plate+switches into the hotswap PCB. You should see the pins making contact with each socket on the backside of the PCB.
3. Plug the board into a computer and test whether each switch is correctly installed. Keys that do not register most likely correspond to switches with bent pins that are not contacting the socket.
4. It is recommended to flash your keyboard before installing it in the case because it can be tricky to enter the bootloader afterwards.
  * Bootmagic reset: Hold down the key at (0,0) in the matrix (the top left key) and then plug the keyboard into the Pi.
  * Physical reset button: Briefly press the button labeled 'RST' on the back of the PCB.

### QMK flashing

1. Install QMK and follow their instructions to flash your own keyboard.
2. See the following link for details:
  * https://github.com/rgoulter/qmk_firmware/tree/bm40hsrgb_rev2/keyboards/kprepublic/bm40hsrgb/rev2
  * https://docs.qmk.fm/#/
Note: make sure your keyboard locale is correctly configured! You can specify the locale when installing Raspbian or via `sudo raspi-config`.

### Mounting keyboard to bottom chassis

1. Connect the USB cable to the keyboard PCB and lower them into the bottom chassis.
2. Route the USB A connector approximately 2-3 inches out of the bottom chassis hinge opening. This cable will connect to the Pi in the top chassis via a USB splitter.
3. Secure the excess keyboard USB cabling inside the bottom chassis compartment using cable ties.
4. Insert the keyboard divider into the bottom chassis to hide the excess keyboard USB cabling.
5. Insert cardstock/paper/rubber spacers surrounding the keyboard if there is excess PCB wiggle room inside the bottom chassis.

## Top chassis

### Heat-setting the thereaded brass inserts

1. Insert the 4 threaded inserts that fasten the top chassis screen cover using a hot soldering iron. Take care not to melt the chassis walls!
   
### Mounting cable connectors

1. Install the microB charging cable into its cutout with the two included screws. 
2. Install the USB splitter cable and HDMI cable into their respective panel cutouts.
4. Friction mount the 3D printed USB and HDMI holders to prevent the cable connectors from moving.

![](https://github.com/jchitpin/think-deck/blob/main/images/chassis-port-cables.jpg)
Fit-testing port cable cutouts on an older prototype model. This was before I realized I needed to remove the plastic sheathing.

### Assembling the Raspberry Pi and HyperPixel

1. Solder the 2x20 break-away header to the Raspberry Pi (unless you bought the presoldered version like I did).
2. Gently connect the HyperPixel to the Raspberry Pi 2x20 header. The display manufacturer Pimoroni recommends holding the display at the edges.
3. Insert your microSD card into the Raspberry Pi and power the device. See below if this results in a black screen...

### Installing HyperPixel drivers if the Pi boots to a black screen

I successfully got the display working with a legacy version of 64-bit Raspbian (based on Bullseye dated 2023-12-05 rather than Bookworm).
1. Edit Raspbian `/boot/config.txt` file and add the following lines to the top of the screen:
  * `dtoverlay=vc4-kms-dpi-hyperpixel4`
  * `dtparam=rotate=90,touchscreen-swapped-x-y,touchscreen-inverted-x`
2. Booted into the Pi with the Hyperpixel 4.0 display working (albeit in portrait mode with inverted touchscreen controls).
3. Ran the `Pi Screen Configuration` application in the drop down menu and changed the screen orientation.
  * Right-clicked on the display and set orientation to `left`.

### Soldering the PowerBoost 1000C to the battery and Pi + HyperPixel

Consult the PowerBoost 1000C documentation for pinouts and assembly instructions: https://cdn-learn.adafruit.com/downloads/pdf/adafruit-powerboost-1000c-load-share-usb-charge-boost.pdf

1. Solder the included USB header to the PowerBoost 1000C PCB (or directly solder the PowerBoost 1000C PCB to the Pi).
2. Connect the battery to the PowerBoost 1000C via the JST connector or solder the wires directly to the board (what I did).
3. Solder the on/off switch (SPDT Slide Switch) to the PowerBoost 1000C with enough wire to position the switch on the right chassis compartment.

### Installing all electronics in the top chassis

1. Plug the microB charging cable into the PowerBoost 1000C USB header, routing excess cable through the bottom of the chassis.
2. Connect one of the two USB splitter ports to the USB A panel cutout cables.
3. Plug the mini HDMI, microB charging, and microB OTG cables into the Pi. Make sure the microB OTG cable is cable managed such that it pokes out of the top left part of the HyperPixel display.
4. Connect the USB splitter to the USB OTG cable. Routing the cable headers so that they face left on top of the battery is ideal.
5. Install the battery into the the left compartment of the chassis with the PowerBoost 1000C lying horizontally at the bottom compartment. The microB charging cable on the PowerBoost should face left towards the battery.
6. Carefully insert the on/off switch connected to the PowerBoost 1000C into the "cup holder" of the HDMI holder.

![](https://github.com/jchitpin/think-deck/blob/main/images/chassis-upper-guts.jpg)
Assembled top chassis. Cable management is extremely important. The thicker HDMI cable is bent to rest against to the PowerBoost 1000C USB port. The latest 3D printed files add an additional 0.75mm depth to the battery compartment to give the USB connectors extra clearance from bulging against the screen cover. 

### Finishing touches

1. Insert the keyboard USB connector into the remaining USB splitter port.
2. Tape down any wires that are sticking out.
3. Tape down the two USB A splitter headers to the battery.
4. Remove the protective film on the HyperPixel.
5. Fasten the screen cover to the top chassis with M2 screws.
6. Fasten the middle hinge cover to the bottom chassis with M2 screws.
7. Install the quickstand to the back of the bottom chassis. It should come with 3M tape so additional glue shouldn't be necessary.

![](https://github.com/jchitpin/think-deck/blob/main/images/front-face-no-fasteners.jpg)
Assembled ThinkDeck prior to heat setting the brass inserts and fastening screws.

# Conclusion

Congratulations you have successfully built your very own ThinkDeck! I'd like to give a shout out to Penk for inspiring me to build my own cyberdeck.


