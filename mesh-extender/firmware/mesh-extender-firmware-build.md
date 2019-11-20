# Building Serval OpenWRT Firmware
These build instructions are tailored for Ubuntu 18.04.2. Your mileage may vary.
## Prerequisites
The following tools are required to build the firmware:
- G++
- GCC
- Git
- ncurses
- OpenSSL libraries (use `libssl1.0-dev`, newer versions are unsupported)
- zlib
- Make
- Python 2.x
- Subversion
- Unzip

These can all be installed in one fell swoop with apt: `sudo apt install g++ gcc git libncurses-dev libssl1.0-dev libz-dev make python subversion unzip`

Additionally, if you're using the `MeshExtender2.0` branch:
- csh
- awk

Which can be installed alongside the above with: `sudo apt install csh gawk`


## Build process
### The `master` way
1. Clone the repo: `git clone https://github.com/servalproject/openwrt.git serval-openwrt`
2. `cd` into the repo: `cd serval-openwrt`
3. Run `./scripts/feeds update serval`
4. Run `./scripts/feeds install -p serval`  
   **NOTE:** You may get persistent errors about missing `git` despite having it installed. A dirty fix to get past that is to edit `include/prereq-build.mk` and comment out lines 147-148.
5. Run `./scripts/feeds install -a serval`
6. Finally make the firmware: `make world`  
   Depending on your hardware, this could take a long time.  
   **NOTE:** An internet connection is required throughout the build process, as some parts may download additional repositories.  
   **NOTE:** If you have Perl 5.26+, you will encounter an issue while compiling Automake due to a change in how Perl handles regular expressions (discovered [here](https://github.com/raspberrypi/noobs/issues/470#issuecomment-376256295)). To get around it, open `build_dir/host/automake-1.15/bin/automake.in`, go to line 3938, and replace `$text =~ s/\${` with `$text =~ s/\$\{`  
   **NOTE:** Make sure you are using `libssl1.0-dev` and not a newer version, as the `tools/mkimage` make target requires an old version
7. The built firmware images will be available in `bin/ar71xx/`

### The `MeshExtender2.0` way
1. Clone the repo: `git clone https://github.com/servalproject/openwrt.git serval-openwrt`
2. `cd` into the repo: `cd serval-openwrt`
3. Switch to the `MeshExtender2.0` branch: `git checkout MeshExtender2.0`
4. Run `./update`
   **NOTE:** An internet connection is required throughout the build process, as some parts may download additional repositories.  
   **NOTE:** You may get persistent errors about missing `git` despite having it installed. A dirty fix to get past that is to edit `include/prereq-build.mk` and comment out lines 147-148.  
   **NOTE:** If you have Perl 5.26+, you will encounter an issue while compiling Automake due to a change in how Perl handles regular expressions (discovered [here](https://github.com/raspberrypi/noobs/issues/470#issuecomment-376256295)). To get around it, open `build_dir/host/automake-1.15/bin/automake.in`, go to line 3883, and replace `$text =~ s/\${` with `$text =~ s/\$\{`  
   **NOTE:** Make sure you are using `libssl1.0-dev` and not a newer version, as the `tools/mkimage` make target requires an old version  
5. The built firmware images will be available in `bin/ar71xx/`
