## Step 1. Requisiti minimi

Nota: A causa di [#403](https://github.com/monero-project/kovri/issues/403), è richiesto almeno un minimo di 1 GiB di RAM per i seguenti ambienti di compilazione..

### Linux / MacOSX / FreeBSD 10
- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58
- [OpenSSL](https://openssl.org/) (always the latest stable version)

### Windows
- [MSYS2](https://msys2.github.io/)
- [MinGW-w64](http://mingw-w64.org/doku.php)

Optional:

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 on FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6 (Recommeded if you are behind a NAT without access to it)
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

### MacOSX
- [Homebrew](http://brew.sh/)

## Step 2. Installa le dipendenze

### Ubuntu Xenial (16.04)
Dipendenze richieste:
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ and libssl installed by default
```
Dipendenze opzionali:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For users behind a restrictive NAT
```

### Ubuntu Trusty (14.04)
Puoi costruire Boost dal codice sorgente oppure usando PPA
Istruzioni per PPA:

Dipendenze richieste:
```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo add-apt-repository ppa:kojoley/boost
$ sudo apt-get update
$ sudo apt-get install libboost-{chrono,log,program-options,date-time,thread,system,filesystem,regex,test}1.58-dev
$ sudo apt-get install git g++-4.9 cmake libboost-all-dev libssl-dev libssl1.0.0
```
Dipendenze opzionali:
```bash
$ sudo apt-get install clang-3.5
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For users behind a restrictive NAT 
```

### Debian (stabile)
Dovremo togliere  ```testing``` per ```Boost 1.58+``` e per [broken CMake](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=826656). Per motivi di documentazione, toglieremo tutte le dipendenze da  ```testing```. Se non hai esperienza con apt-pinning, procedi con le seguenti istruzioni prima di installare le dipendenze:

- Crea e modifica ```/etc/apt/preferences.d/custom.pref```
- Salva il file con il seguente testo:

```
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650
```
- Crea e modifica ```/etc/apt/sources.list.d/custom.list```
```
# Stable
deb [Enter your mirror here] stable main non-free contrib
# Testing
deb [Enter your mirror here] testing main non-free contrib
```
- Sostituisci ```[Enter your mirror here]``` con il tuo mirror (guarda ```/etc/apt/sources.list```)
- Esegui ```$ sudo apt-get update```
- Installa le dipendenze con ```-t testing```:

Dipendenze richieste:
```bash
$ sudo apt-get -t testing install git g++ cmake libboost-all-dev libssl-dev libssl1.0.0
```
Dipendenze opzionali:
```bash
$ sudo apt-get -t testing install clang
$ sudo apt-get -t testing install doxygen graphviz
$ sudo apt-get -t testing install libminiupnpc-dev #For users behind a restrictive NAT 
```

### Arch Linux
Dipendenze richieste:
```bash
$ sudo pacman -Syu cmake boost  # gcc/g++ and openssl installed by default
```
Dipendenze opzionali:
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc #For users behind a restrictive NAT 
```

### Mac OSX
Dipendenze richieste:
```bash
$ brew install cmake boost openssl # clang installed by default
```
Dipendenze opzionali:
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc #For users behind a restrictive NAT 
```

### FreeBSD 10
Dipendenze richieste:
```bash
$ sudo pkg install git cmake gmake clang36 openssl
# Build latest boost (1.58 minimum)
$ wget [latest boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd latest_boost
$ ./bootstrap.sh --with-toolset=clang  # OK to build with clang 3.5
$ sudo ./b2 --toolset=clang install
```
Dipendenze opzionali:
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc #For users behind a restrictive NAT 
```
**Nota: guarda le istruzioni per la build FreeBSD qui sotto**

### Windows (MSYS2/MinGW-64)
* Scarica [MSYS2 installer](http://msys2.github.io/), 64 bit o 32 bit, dipende dal tuo computer ed eseguilo..
* Usa il collegamento associato con la tua architetura per lanciare l'ambiente MSYS2. Nota che se sei su Windows 64 bit, avrai tutti e due gli ambienti, 64 e 32 bit.
* Aggiorna i pacchetti con i seguenti comandi:
```
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
* For those of you already familiar with pacman, you can run the normal ```pacman -Syu``` to update, but you may get errors and need to restart MSYS2 if pacman's dependencies are updated.
* Install dependencies: ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Optional: ```mingw-w64-x86_64-doxygen```  (you'll need [Graphviz](http://graphviz.org/doc/winbuild.html) for doxygen)
* Note: You'll need  ``` mingw-w64-x86_64-miniupnpc``` if you are behind a restrictive NAT firewall.

## Step 3. Build   

### 1. Clone the repository
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```
### 2. Build kovri and submodule dependencies with one command
```bash
$ make # to decrease build-time, run make -j [available CPU cores]
```
### 3. Install resources (configuration files + package resources)
```bash
$ make install-resources
```

- End-users MUST run ```make install-resources``` for new installations
- Developers SHOULD run ```make install-resources``` after a fresh fetch

### Other options you can use in place of step 2:

- ```make upnp``` produces vanilla binary with UPnP support (requires [MiniUPnP](https://github.com/miniupnp/miniupnp/releases))
- ```make optimized-hardening``` produces optimized, hardened binary
- ```make all-options``` produces optimized, hardened, UPnP enabled binary
- ```make tests``` produces all unit-tests and benchmarks
- ```make tests-optimized-hardening``` produces all unit-tests and benchmarks with optimized hardening
- ```make static``` produces static binary

### Other available options
- ```make doxygen``` produces Doxygen documentation
- ```make clean``` cleans build directories and Doxygen output
- ```make help``` shows available CMake build options

#### Notes
- Doxygen output will be in ```doc``` directory
- All other build output will be in the ``build``` directory

### Clang
To build with clang, you **must** export the following:

```bash
$ export CC=clang CXX=clang++  # replace ```clang``` with a clang version/path of your choosing
```

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36
$ gmake && gmake install-resources
```
- Replace ```make``` with ```gmake``` for all other build options

### (Optional) Custom data path
You can customize Kovri's data path to your liking. Simply export ```KOVRI_DATA_PATH```; example:

```bash
$ export KOVRI_DATA_PATH=$HOME/.another-kovri-data-path && make && make install-resources
```

## Step 4. Proceed to the user guide
Read the [user guide](https://github.com/monero-project/kovri/blob/master/doc/USER_GUIDE.md) to get started

## Docker

Alternatively, if you use Docker, the following will build the image for you.

```bash
$ docker build -t geti2p/kovri .
```
