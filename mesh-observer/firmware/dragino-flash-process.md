# Flashing a Dragino2-based Mesh Observer

1. Open the case of the Dragino by removing the screws under the rubber feet on the bottom
2. Find the GPIO header on the Dragino board (in-between the power and Ethernet jacks)
3. Connect the pins on the header to a USB-UART adaptor as shown below:
```
DRAGINO     USB-UART
UART_TX --> RX
UART_RX --> TX
    GND --> GND
```
4. Plug the USB-UART adaptor into your computer
5. Connect an Ethernet cable between the Dragino's LAN port and your computer
6. Configure your Ethernet interface to use the IP `192.168.255.2`
7. Open the USB-UART serial port at speed 115200 on your computer with a serial monitor program (e.g. [PuTTY](https://www.putty.org/) or [minicom](https://en.wikipedia.org/wiki/Minicom))
8. Connect power to the Dragino
9. When prompted, press any key to stop the boot process
10. Enter the following commands in order. **IT IS CRITICAL THAT YOU TYPE THESE OUT CORRECTLY!** You may brick your device if you make a mistake typing out these commands.
```
tftp 82000000 openwrt-dragino2.bin
erase 0x9f050000 +$filesize
cp.b 0x82000000 0x9f050000 $filesize
setenv bootcmd bootm 0x9f050000
saveenv
boot
```
Here are the above commands condensed into a single line for easy copy-pasting:  
`tftp 82000000 openwrt-dragino2.bin; erase 0x9f050000 +$filesize; cp.b 0x82000000 0x9f050000 $filesize; setenv bootcmd bootm 0x9f050000; saveenv; boot`  
11. Wait for the device to boot

The Dragino should have been flashed successfully and should now be running the custom Mesh Observer firmware.
It is now safe to disconnect the power, Ethernet, and serial cables and reassemble the Dragino.
