# Network Configuration
The Mesh Extender network interface configuration is located in `/etc/config/network` and `/etc/config/network.template`. All changes should be made in the template which are applied at the next boot (see below).

When booting, the `/etc/rc.d/S13pre_wireless_setup` and `/etc/rc.d/S15wireless_setup` scripts will fill in the template file with Wi-Fi interface IP and MAC addresses then write the result to `/etc/config/network`. This will overwrite any changes made to `/etc/config/network` since the last boot.

The Ethernet interface configuration can also be set via the [setup-meshex script](https://github.com/servalproject/serval-mesh-observer-packet-capture/blob/master/scripts/setup-meshex.sh). (This also enables persistent SSH access)

The below table summarises the default network configuration:

| Interface name   | Interface description                           | IP Addresses       |
| ---------------- | ----------------------------------------------- | ------------------ |
| `lo`             | Loopback                                        | `127.0.0.1./8`     |
| `eth0`           | Ethernet 0 (DB25 side)                          | `192.168.1.1/24`   |
| `eth1`           | Ethernet 1 (DB15 side)                          | `192.168.2.1/24`   |
| `wlan0`          | Wi-Fi with SSID `servalproject.org`             | `172.XXX.XXX.1/24` |
| `wlan1`          | Wi-Fi with SSID `MeshExtender-XXXXXXXXXXXX`     | `192.168.3.1/24`   |
| `adhoc0`         | Ad-Hoc Wi-Fi with SSID `mesh.servalproject.org` | `10.XXX.XXX.XXX/8` |
