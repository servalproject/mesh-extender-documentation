# System Time
Mesh Extenders have two primary sources of time synchronisation: NTP and LBARD. NTP is viable in the lab environment and also for small mesh networks where each node has connectivity to another via Wi-Fi. LBARD synchronisation aims to make time synchronisation over a larger area more feasible, but as of right now it is not without issues.

## NTP
By default, Mesh Extenders will try to synchronise their time by sending NTP requests to `192.168.2.54`.
Setting up an NTP server (such as `ntpd` or `chrony`) at that endpoint will allow Mesh Extenders on the same network to synchronise their time from there.

The NTP daemon (`ntpd`) is started on boot by `/etc/rc.d/S98sysntpd` using the NTP server list found in `/etc/config/system` under the `config timeserver 'ntp'` section. More servers can be added by inserting a line similar to `list server '<address>'`, where `<address>` is the NTP server address. The order they are present in the config file is the order in which they will be queried. There is no limit to the number of NTP servers that can be specified.

To start the NTP daemon manually, run `ntpd -p <address>`, where `<address>` is the address of an NTP server to query. Multiple servers can be specified by adding additional `-p <address>` pairs.

## LBARD
**NOTE:** This feature has been known to [cause problems](https://github.com/servalproject/openwrt-packages/pull/22#issue-337137051) when the system clock source is unstable. A single device can corrupt the entire network if left unchecked.

LBARD has a built-in startup argument that allows it to set the system time based on the timestamps from packets its observed. In theory this should allow a single, decentralised time source to be set up for an LBARD mesh and have the time propagated outward.

To enable this feature, start LBARD with the `timeslave` argument. You will need to modify the runscript located at `/etc/serval/runlbard` to enable timeslave on boot.
