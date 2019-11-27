# Capturing packets
The Mesh Observer firmware comes with a capture program ready to use.
The capture client program (`capture`) will capture packets from the Mesh Observer's Wi-Fi interface and the Mesh Extender's radio via the UHF breakout.
The captured packets are sent to the capture server program (`svrCap`) which will dissect each packet, classify them by type and/or payload, and draw them on a [UML Sequence Diagram](../images/timing-diagram.png) for analysis.

## Setting up a capture server
To start capturing with the capture server program:
1. Run`svrCap`
2. Press `Ctrl+C` to stop capturing and generate a sequence diagram.

The capture server should start listening at port `3940/udp` on all interfaces and begin processing incoming packets captured by clients. To stop the capture server, press `Ctrl+C` and the program will briefly generate a diagram of the captured output and halt.

For more information on the capture server program, see [its README](https://github.com/servalproject/serval-mesh-observer-packet-capture#server).

## Setting up a capture client
Capturing packets on a Mesh Observer is quite simple, however due to SSH limitations, it does require that you are connected to the device for the duration of the capture. This can be avoided by using the start-stop-daemon program packaged with the Mesh Observer firmware: `start-stop-daemon -Sbx capture <args…>`.

1. Log in to the Mesh Observer via SSH
2. Run `iw phy phy0 set channel 11` to listen on Wi-Fi channel 11 (Serval's default channel)
3. Run `capture <server_ip> -f 'ether host <mac>'`, where `<server_ip>` is the IP address of the capture server and `<mac>` is the MAC address of the attached Mesh Extender's Wi-Fi interface.

The Mesh Observer should start capturing packets and sending them to the capture server at the specified IP address. To stop capturing, press `Ctrl+C` and the program should halt.

**NOTE:** There are several useful options available for the capture client program not listed here. Running `capture --help` will list each of them with a description of the effect they have.

For more information on the capture client program, see [its README](https://github.com/servalproject/serval-mesh-observer-packet-capture#client).
