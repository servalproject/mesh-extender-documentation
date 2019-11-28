# Building a UHF Breakout
For Mesh Observers to capture UHF traffic, they need a way of intercepting the transmissions.
The devices themselves don't have a built-in UHF radio, so instead we leverage the [Mesh Extender power port](http://developer.servalproject.org/dokuwiki/doku.php?id=content:meshextender:me2.0_standard_power_cable_pinout) and tap into the radio serial data lines.
These serial lines are looped back via the power cable, so by attaching a probe here we can see exactly what the Mesh Extender sees.

## Making the breakout board
The breakout board is a simple board with a male and female DB25 connector on either end with each of the 25 lines exposed by a pair of pins.
Each pair of pins are jumpered together to connect the lines when not connected to anything else.
This design allows us to transparently shim the Mesh Observer into an existing Mesh Extender setup without modifying or replacing the power cable.

**NOTE:** When soldering the board together, make sure that the male connector is placed as J1 and the female connector is placed as J2. The pinout is *not* symmetrical and *will* cause damage if soldered the wrong way around and plugged in.

<img src="../images/breakout-top-down.jpg" width="49%"></img>
<img src="../images/breakout-female.jpg" width="49%"></img>

## Making the wires
The breakout is connected to several USB-UART adaptors through some custom-made wires. These connect a single line to two adaptors so that they can be monitored at two serial speeds simultaneously.
The wires have a 2-pin DuPont connector on the breakout-end and two single-pin DuPont connectors on the USB-end.
Between them is a single wire that connects each of the pins together.

1. Cut four short lengths of wire (around 5-10cm)
2. Cut one long length of wire (arbitrary length, it's just to give space between the USB adaptors and the breakout)
3. Strip both ends of each wire
4. Solder one end of two short wires to form a pair
5. Repeat for the other two short wires
6. Crimp two single-pin female DuPont connectors onto the ends of one short pair
7. Crimp one 2-pin female DuPont connector onto the end of the other short pair
8. Slide two short lengths of heatshrink onto the long wire (~3cm, long enough to cover the solder joint)
9. Solder one pair of short wires onto one end of the long wire
10. Repeat for the other end with the other pair
11. Shrink the heatshrink with a heat gun (or a lighter if you don't have a heat gun, just be careful of burning yourself or the wire)
12. Repeat steps 1-11 an additional 3 times for a full set of wires

The final result should look like the pictures below:  
<img src="../images/wires-joined.jpg" width="32%"></img>
<img src="../images/wires-set.jpg" width="32%"></img>
<img src="../images/wires-split.jpg" width="32%"></img>

## Putting it all together
1. Connect the 2-pin connector end of one wire to pin 1 of the breakout
2. Connect both of the single-pin ends of the same wire to the ground pins of two USB adaptors
3. Repeat steps 1 and 2 with another wire connected between pin 4 of the breakout and ground of two more USB adaptors
4. Connect the 2-pin connector end of one wire to pin 5 of the breakout
5. Connect both of the single-pin ends of the same wire to the 'RX' pins of two USB adaptors
6. Repeat steps 4 and 5 with another wire connected between pin 6 of the breakout and 'RX' of the other two USB adaptors
7. Insert all four USB adaptors into a USB hub

The final result should look like the pictures below:  
<img src="../images/jig.jpg" width="32%"></img>
<img src="../images/jig-breakout-closeup-angled.jpg" width="32%"></img>
<img src="../images/jig-usbhub-closeup.jpg" width="32%"></img>