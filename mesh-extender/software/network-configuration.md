# Network Configuration
The Mesh Extender network interface configuration is located in `/etc/config/network` and `/etc/config/network.template`. All changes should be made in the template which are applied at the next boot (see below).

When booting, the `/etc/rc.d/S13pre_wireless_setup` and `/etc/rc.d/S15wireless_setup` scripts will fill in the template file with Wi-Fi interface IP and MAC addresses then write the result to `/etc/config/network`. This will overwrite any changes made to `/etc/config/network` since the last boot.

The Ethernet interface configuration can also be set via the [setup-meshex script](https://github.com/servalproject/serval-mesh-observer-packet-capture/blob/master/scripts/setup-meshex.sh). (This also enables persistent SSH access)
