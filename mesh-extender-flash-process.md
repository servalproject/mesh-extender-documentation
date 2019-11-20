# Flashing a Mesh Extender
These flashing instructions are tailored for Ubuntu 18.04.2. Your mileage may vary.

## Prerequisites
You will need the following to flash a Mesh Extender with a new bootloader and/or firmware:
- A [Mesh Extender Programming Cable](programming-cable.md)
- A copy of the [Mesh Extender firmware](mesh-extender-firmware-build.md)
- (Optional) A copy of the [Mesh Extender bootloader](mesh-extender-bootloader-build.md)
- An Ethernet cable
- A TFTP server ([Ubuntu](https://help.ubuntu.com/community/TFTP), [Fedora](https://docs.fedoraproject.org/en-US/Fedora/html/Installation_Guide/pxe-tftpd.html))
- A Mesh Extender

## Process
1. Install and configure a TFTP server
2. Copy the firmware file into the TFTP directory and name it 'openwrt-domino.bin'
3. *(Optional)* Copy the bootloader file into the TFTP directory and name 'uboot_for_domino.bin'
4. Clone the [Serval OpenWRT package repository](https://github.com/servalproject/openwrt-packages)
5. Checkout the `MeshExtender2.0` branch
7. Configure your computer's Ethernet interface to use the IP address `192.168.1.2` with netmask `255.255.255.0`
8. Connect the Ethernet cable between the Mesh Extender and your computer
9. Connect a Mesh Extender Programming Cable to your computer. This will cause a USB serial port to appear, possibly '/dev/ttyUSB0' if you have no others connected
10. Open the `auto-flash` directory in a terminal
11. Build the auto-flash utility: `make`
12. Run the auto-flashing utility with the serial port you found in step 9: `./auto-flash /dev/ttyUSB0`
13. Connect the programming cable to the Mesh Extender

This should automatically flash the Mesh Extender with the new firmware and bootloader if required. The process takes about 3 minutes. When the process is complete, the Mesh Extender will boot and start filling the terminal with log messages, at which point it is safe to disconnect the Ethernet and programming cables.

You can program as many Mesh Extenders as you wish in this way by **moving the Ethernet cable first** and then the Mesh Extender programming cable to the each Mesh Extender to be flashed.
