## Step 0. (Optional) Skip building and use the release binaries instead

See the [README](https://github.com/monero-project/kovri/blob/master/README.md) to download pre-built kovri and checksum file. Simply install and start kovri, then off you go!

## Step 1. If building, minimum requirements

### Linux / MacOSX / FreeBSD 11 / OpenBSD 6
- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58 (see platform-specific version caveats)
- [OpenSSL](https://openssl.org/) (always the latest stable version)

### Windows
- [MSYS2](https://msys2.github.io/)
- [MinGW-w64](http://mingw-w64.org/doku.php)

Optional:

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 or higher on FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6 (Recommeded if you are behind a NAT without access to it)
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

### MacOSX
- [Homebrew](http://brew.sh/)

#### Note: a minimum of 1 GiB of RAM is suggested for build environments (see [#403](https://github.com/monero-project/kovri/issues/403) for details)

## Step 2. Install dependencies

#### Note: for container options (like Docker and snapcraft), see the [User Guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/user_guide.md)

### Ubuntu Xenial (16.04)
Required dependencies:
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ and libssl installed by default
```
Optional dependencies:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For users behind a restrictive NAT
```

### Ubuntu Trusty (14.04)
You can either build Boost from source or use PPA
Below are instructions for PPA:

Required dependencies:
```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo add-apt-repository ppa:kojoley/boost
$ sudo apt-get update
$ sudo apt-get install libboost-{chrono,log,program-options,date-time,thread,system,filesystem,regex,test}1.58-dev
$ sudo apt-get install git g++-4.9 cmake libboost-all-dev libssl-dev libssl1.0.0
```
Optional dependencies:
```bash
$ sudo apt-get install clang-3.5
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For users behind a restrictive NAT
```

### Debian-9 (stretch/stable)
Required dependencies:
```bash
$ sudo apt-get install git g++ cmake libboost-all-dev libssl-dev libssl1.0.0
```
Optional dependencies:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For users behind a restrictive NAT
```

### Arch Linux
Required dependencies:
```bash
$ sudo pacman -Syu cmake boost  # gcc/g++ and openssl installed by default
```
Optional dependencies:
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc #For users behind a restrictive NAT
```

### Mac OSX
Required dependencies:
```bash
$ brew install cmake boost openssl # clang installed by default
```
Optional dependencies:
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc #For users behind a restrictive NAT
```

### FreeBSD 11
Required dependencies:
```bash
$ sudo pkg install git cmake gmake clang36 boost-libs openssl
```
Optional dependencies:
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc #For users behind a restrictive NAT
```
**Note: see FreeBSD build instructions below**

### OpenBSD 6
Required dependencies:
```bash
$ sudo pkg_add bash git cmake gmake g++ llvm
```
Optional dependencies:
```bash
$ sudo pkg_add miniupnpc #For users behind a restrictive NAT
$ sudo pkg_add doxygen graphviz
```

# Build latest boost
```bash
# Get latest boost
$ wget [latest boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd latest_boost/

# Download and apply patches
# https://svn.boost.org/trac/boost/attachment/ticket/12575/boost-1.62-asio-libressl.patch
# https://gist.githubusercontent.com/laanwj/bf359281dc319b8ff2e1/raw/92250de8404b97bb99d72ab898f4a8cb35ae1ea3/patch-boost_test_impl_execution_monitor_ipp.patch

# Build boost
$ echo 'using gcc : : eg++ : "-fvisibility=hidden -fPIC" "" "ar" "strip"  "ranlib" "" : ;' > user-config.jam
$ config_opts="runtime-link=shared threadapi=pthread threading=multi link=static variant=release --layout=tagged --build-type=complete --user-config=user-config.jam -sNO_BZIP2=1"
$ ./bootstrap.sh --without-icu --with-libraries=chrono,log,program_options,date_time,thread,system,filesystem,regex,test
$ sudo ./b2 -d2 -d1 ${config_opts} --prefix=${BOOST_PREFIX} stage
$ sudo ./b2 -d0 ${config_opts} --prefix=${BOOST_PREFIX} install
```
**Note: see OpenBSD build instructions below**

### Windows (MSYS2/MinGW-64)
* Download the [MSYS2 installer](http://msys2.github.io/), 64-bit or 32-bit as needed, and run it.
* Use the shortcut associated with your architecture to launch the MSYS2 environment. On 64-bit systems that would be the MinGW-w64 Win64 Shell shortcut. Note that if you are running 64-bit Windows, you will have both 64-bit and 32-bit environments.
* Update the packages in your MSYS2 install:
```
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
* For those of you already familiar with pacman, you can run the normal ```pacman -Syu``` to update, but you may get errors and need to restart MSYS2 if pacman's dependencies are updated.
* Install dependencies: ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Optional: ```mingw-w64-x86_64-doxygen```  (you'll need [Graphviz](http://graphviz.org/doc/winbuild.html) for doxygen)
* Note: You'll need  ``` mingw-w64-x86_64-miniupnpc``` if you are behind a restrictive NAT firewall.
* Note: Ensure ```C:\<path-to>\msys64\mingw64\bin``` (or mingw32) is on your environment path when running MSYS2 bash from PowerShell

## Step 3. Build

### 1. Clone the repository
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### 2. Build kovri and submodule dependencies with one command
```bash
$ make release-static # to decrease build-time, run `make -j <available CPU cores>`. Example: `make -j4`
```

### 3. Install
```bash
$ make install
```

- End-users MUST run `make install` for new installations
- Developers SHOULD run `make install` after a fresh build

### Other options you can use in place of step 2:

For an accurate and complete list of options, see the targets in the [Makefile](https://github.com/monero-project/kovri/blob/master/Makefile).

#### Notes
- All build output (including Doxygen) will be in the build output directory

### Clang
To build with clang, you **must** export the following:

```bash
$ export CC=clang CXX=clang++  # replace ```clang``` with a clang version/path of your choosing
```

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36  # Or higher clang version
$ gmake && gmake install
```
- Replace ```make``` with ```gmake``` for all other build options


### OpenBSD
```bash
$ export CC=clang CXX=clang++  # clang recommended, otherwise egcc/eg++
$ gmake && gmake install
```
- Replace ```make``` with ```gmake``` for all other build options


### (Optional) Custom data path
You can customize Kovri's data path to your liking. Simply export ```KOVRI_DATA_PATH```; example:

```bash
$ export KOVRI_DATA_PATH=$HOME/.another-kovri-data-path && make && make install
```

## Step 4. Proceed to the user guide
Read the [user guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/user_guide.md) to get started

## Docker

Alternatively, if you use Docker, the following will build the image for you.

```bash
$ docker build -t geti2p/kovri .
```

## Fuzz testing

From [reference](http://llvm.org/docs/LibFuzzer.html) : "LibFuzzer is under active development so you will need the current (or at least a very recent) version of the Clang compiler"

Get a recent version of clang:

```bash
$ cd ~/ && mkdir TMP_CLANG && git clone https://chromium.googlesource.com/chromium/src/tools/clang TMP_CLANG/clang
$ ./TMP_CLANG/clang/scripts/update.py
$ cd --
```

Get libFuzzer:

```bash
$ git clone https://chromium.googlesource.com/chromium/llvm-project/llvm/lib/Fuzzer contrib/Fuzzer
```

Build kovri with fuzz testing enabled:

```bash
$ PATH="~/third_party/llvm-build/Release+Asserts/bin:$PATH" CC=clang CXX=clang++ make fuzz-tests
```

Usage (Example for RouterInfo):

```bash
mkdir RI_CORPUS MIN_RI_CORPUS
find ~/.kovri/core/network_database/ -name "router_info*" -exec cp {} RI_CORPUS \;
./build/kovri-util fuzz --target=routerinfo -merge=1 MIN_RI_CORPUS RI_CORPUS
./build/kovri-util fuzz --target=routerinfo -jobs=2 -workers=2 MIN_RI_CORPUS
```
