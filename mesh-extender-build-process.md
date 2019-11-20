# Assembling an indoor-only Mesh Extender
The following procedure will step you through assembling an indoor-only (red) Serval Mesh Extender.
The procedure is much the same to assemble weather-resistant Mesh Extenders (white), but they require
some extra gaskets and a breathing hole cover to improve its ruggedness.

## Parts
You will need the following parts:
- 1x Mesh extender board
- 1x USB flash drive (bigger is better)
- 1x Mesh Extender housing (red)
- 2x RP-SMA male-female connectors
- 3x Plastite 45 M4x12mm screws
- 4x 4mm jack screws
- 2x Nuts to accommodate the 4mm jack screws
- 1x RFD900+ long-range UHF radio modem
- 1x u.fl to RP-SMA female connector *and* 1x external Wi-Fi antenna **OR**
- 1x u.fl Wi-Fi antenna
- 2x 900MHz UHF antennas
- (optional, testing only) 1x CAT5/e+ RJ45/8P8C Ethernet cable

## Board preparation
1. The board will initially need to be flashed with new firmware.
   Follow the steps [here](mesh-extender-firmware-build.md) to build and flash new firmware onto the Mesh Extender board.
2. Format the flash drive so that it is empty and has no partitions
3. Plug the USB flash drive into one of the USB ports on the Mesh Extender board
4. (Optional) Connect the u.fl Wi-Fi antenna to the port on the Domino. The port should be on the corner of a large, rectangular chip with a metal housing located on the underside of the board.

## Housing preparation
1. Insert and screw in the two RP-SMA male to female connectors to both of the holes on either side of the upper housing
2. (Optional) Insert and screw in the u.fl to RP-SMA connector into the centre hole of the upper housing (if using an external Wi-Fi antenna)
3. Screw both RP-SMA male to female connectors to the RP-SMA jacks on the RFD900+ modem

## Final assembly
1. (Optional, testing only) Pass the Ethernet cable through the hole in the lower housing and connect it to one of the RJ45 jacks on the Mesh Extender board
2. Insert the Mesh Extender board into the lower housing so that the DSub ports are poking out
3. Screw two of the 4mm jack screws into the the two holes either side of the DSub-15 port (smaller port)  
The next two jack screws are a bit tricky because the DSub-25 port does not have threaded holes on either side.  
4. Carefully locate a nut behind one of the holes beside the DSub-25 port (larger port)
5. While holding the nut in place, screw in a 4mm jack screw and tighten the nut (you may need two socket tools for this)
6. Repeat on the other side of the DSub-25 port

The Mesh Extender board should now be firmly attached to the lower housing and the jack screws should be fastened tightly.
Next we will insert the RFD900+ modem and seal both halves together.

7. Slide the RFD900+ modem heatsink-side-up into the receptacle on the Mesh Extender board
8. Tuck the connector cables *above* the board and gently slide the two halves together until they meet. Be careful to slide the board into the two notches within the upper housing as they will provide extra structural support for the board.
9. Holding both halves together, screw in the three Plastite 45 screws into the holes around the edge of the lower housing
10. Attach two UHF antennas to both of the exposed RP-SMA ports
11. (Optional) Attach a Wi-Fi antenna to the centre RP-SMA port (if using an external Wi-Fi antenna)

The Mesh Extender is now completely assembled.
