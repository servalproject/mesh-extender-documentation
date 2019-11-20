# Setting up SSH access
The Mesh Extenders have a built-in SSH server which is particularly useful for configuration and debugging in the field. Enabling and disabling the server is achieved by adding or removing a file from the `/dos/` partition and will take effect the next time the device is rebooted.

If access is desired after deployment, it is important that it is set up just after first flashing the device, as it will automatically disable the SSH server after it reboots. If the SSH server is disabled already, you can re-enable it by removing the USB from the device, mounting the first partition, and changing contents to satisfy the following conditions:

| `yesroot` | `noroot` | Result                                                               |
| --------- | -------- | -------------------------------------------------------------------- |
| Absent    | Absent   | SSH enabled on next boot, password is `root`, reverts following boot |
| Present   | Absent   | SSH enabled on next boot, password is contents of `yesroot`          |
| Present   | Present  | SSH enabled on next boot, password is contents of `yesroot`          |
| Absent    | Present  | SSH disabled on next boot                                            |
