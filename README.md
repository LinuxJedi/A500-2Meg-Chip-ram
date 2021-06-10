# Amiga 500/2000 2MB Chip RAM Mod

This is an adapter board to retrofit a 2MB Agnus into an Amiga 500/2000 and also includes 2MB of chip ram. It is based on [LIV2's design](https://github.com/LIV2/A500-2Meg-Chip-ram) but is easier to solder and has been remade in KiCad 6.

At present this particular design has only been tested on an Amiga 2000. It should, however, work on Amiga 500s as well, with the caveat that it might get in the way of the keyboard in the revision 5 Amiga 500 (if you try this please let me know).

**NOTE**: You need KiCad 5.99 or higher to be able to edit this project.

![PCB Top](Images/top.png?raw=True)
![PCB Bottom](Images/bottom.png?raw=True)

## Assembly Steps
1. Solder the DRAM, U4, U3
2. Solder the Capacitors & Resistor (Only fit VBB capacitor if your Agnus says VBB on the top!)
3. Solder the PLCC Socket making sure that the socket aligns exactly with the outline on the top of the PCB!
4. Prepare the pin headers by removing a pin from this corner of each as indicated here:<br/>
![remove](Images/header.png?raw=True)
5. Solder the pin headers.
6. Solder a wire to A20 and connect the other end at one of the following locations:
   * Gary pin 36
   * CPU pin 48
   * JP5 Top left pad (Amiga 500 Rev 6)
7. Apply motherboard fixes required in the section below
8. Carefully desolder & remove the Agnus socket
9. Remove the same corner pin from each pin socket and solder them in replacing the agnus socket.
10. Insert the adapter

    **To make sure it is installed the correct way, pay attention to the marking of "1" on the PCB and on the Amiga they must match**

    On a Rev 6A Amiga 500 this means that the ram will be on the right hand side, on a Rev 5 it will be pointing downwards instead.

    Look from the sides to make sure the pins are going in to the headers.

    The following image is the installation in an Amiga 2000.

![installed](Images/installed.jpg?raw=True)

## Motherboard Fixes

### Amiga 500

Make sure that JP2 is set as shown:

![jp2](Images/JP2.png?raw=True)

### Amiga 2000

If you have 512KB of Chip RAM before installing the device you need to switch the position of J101, which is located near the power supply connector, to its opposite position.

You then need to remove J500, which is located near Gary. On some motherboard this will be a case of removing a jumper, some will be desoldering a bridge and some will require cutting a trace between the jumper pads.

## Jumper Settings
The default jumper settings do not need to be changed and will work on all systems. 

Rev 6A Amiga 500's have jumpers that can be used to provide the A20 signal on pin 35 instead of XCLK
This allows us to use this adapter without having to add the wire to A20 but note **this will mean you cannot use a genlock on this Amiga!**

In this case you must set J1 to 28M to bypass the XCLK/28M Mux then set J2 of the adapter to A20<br />
If you wish to do this then you will also need to change the jumper settings at J5 on your A500 motherboard

![jp5](Images/JP5.png?raw=True)

## Bill of materials

The components required are identical to LIV2's original design, but please be aware their locations have changed.

|Component|Location|QTY|Link|
|---------|--------|---|------|
|Ceramic Capacitor, 0.1uF, 0805|C1-7|6|[Mouser](https://www.mouser.com/ProductDetail/710-885012207098)|
|Ceramic Capacitor, 22pF, 0805|C7|1|[Mouser](https://www.mouser.com/ProductDetail/710-885012007053) |
|Resistor, 150 Ohm, 0805|R1|1|[Mouser](https://www.mouser.se/ProductDetail/652-CR0805JW-151ELF)|
|74AHC1G08 Single 2-Input AND Gate, SOT-23-5|U3|1|[Mouser](https://www.mouser.com/ProductDetail/595-SN74AHC1G08DBVR)|
|74AHCT158 Quad 2-input Multiplexer, SOIC-16|U4|1|[Mouser](https://www.mouser.com/ProductDetail/595-SN74AHCT158D) |
|PLCC-84 Socket, Through-hole|U2|1|[Mouser](https://www.mouser.com/ProductDetail/437-5408808424008) |
|5V, 1Mx16 EDO/FPM DRAM, SOJ-42<br>- K4F151611<br>- K4E151611<br>- GM71C18163C<br>- AS4C1M16E5|U5|1|eBay, Aliexpress etc|
|22-Pin, 2 Row Female header||4|[Mouser](https://www.mouser.se/ProductDetail/517-929975-01-11-RK)
|22-Pin, 2 Row Male header||4|[Mouser](https://www.mouser.se/ProductDetail/649-77313-118-22LF)

**Note**: Only solder C2 if the 8375 you are installing is marked with "VBB".
