# Diagnostics Pages
Mesh Extenders have two diagnostics pages provided by both LBARD and Servald. These pages show the current status of the Mesh Extender at a glance and are instrumental to diagnosing problems with Mesh Extenders.

Both of these status pages are available at any of the Mesh Extender's IP addresses (Ethernet: `192.168.1.1` or `192.168.2.1`, Wi-Fi: `192.168.3.1`).

## LBARD status page
The LBARD status page is available on port `21506`.

It displays the Mesh Extender's SID, LBARD version, peers visible via radio, peers visible via Wi-Fi, and Rhizome bundle status (announced, in possession, and in transit) among others.
The LBARD status page is very useful for establishing the visibility of other devices around the Mesh Extender, and tracking Rhizome bundle movements throughout the network.

## Servald status page
The Servald status page is available on port `4110`.

It displays the current peers via Wi-Fi and Ethernet, Wi-Fi interface packet statistics, and the current Rhizome bundle transfer status.
This page is already encapsulated in the [LBARD status page](#lbard-status-page), but it may be useful for situations where only Servald is running.
