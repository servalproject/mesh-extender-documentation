# Building the Serval Mesh Extender U-Boot Bootloader
These build instructions are tailored for Ubuntu 18.04.2. Your mileage may vary.
## Prerequisites
This guide assumes you have installed the prerequisites for building the Serval OpenWRT firmware (see below).  
The following additional tools are required to build the bootloader:
- Java JRE

Which can be installed through apt with: `sudo apt install default-jre`

As mentioned above, we will be using the toolchain found in the [Serval OpenWRT repository](https://github.com/servalproject/openwrt), so clone that first with `git clone https://github.com/servalproject/openwrt.git` and follow the [build instructions](mesh-extender-firmware-build.md).

## Build process
1. Clone the repository: `git clone https://github.com/servalproject/u-boot_mod.git`
2. `cd` into the repository: `cd u-boot_mod/u-boot-domino-2015/`
3. Open `Makefile` in a text editor
4. Replace line 4 with `export TOOLPATH=<toolchain_path>` where `<toolchain_path>` is the absolute path to the toolchain provided in the Serval OpenWRT repository. (e.g. `/home/user/openwrt/staging_dir/toolchain-mips_34kc_gcc-4.8-linaro_uClibc-0.9.33.2/`)
5. Run `make`  
   **NOTE:** If the build process fails on `fsdata.c` with an error like `fsdata.c:333:1: error: expected expression before ',' token`, open `u-boot-domino-2015/u-boot/httpd/fsdata.c` with a text editor, scroll to the line in question (line 333 in this case), and remove the comma before `0 };`.
6. The built U-Boot image will be at `u-boot-domino-2015/bin/uboot_for_domino.bin`
