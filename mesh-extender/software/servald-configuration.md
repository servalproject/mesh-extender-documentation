# Configuring Servald

Servald configuration files can be found at both `/etc/serval/serval.conf` and `/serval-var/serval.conf`. The latter file is loaded by Servald when it starts. Servald needs to be restarted with `servald stop && servald start` for changes to take effect.

If `/serval-var/serval.conf` is not present at boot, `/etc/serval/serval.conf` is copied over by `/etc/rc.d/S49servald`.

See the [current default configuration file for Mesh Extenders](https://github.com/servalproject/openwrt-packages/blob/MeshExtender2.0/net/serval-mesh-extender/files/etc/serval/serval.conf) and the [Servald documentation](https://github.com/servalproject/serval-dna/blob/development/doc/Servald-Configuration.md) for details on the contents of the file.
