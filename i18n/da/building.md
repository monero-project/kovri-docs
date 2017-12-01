## Trin 0. (valgfri) Drop at bygge programmet og brug de udgivet binære filer i stedet

Kig i [README](https://github.com/monero-project/kovri/blob/master/README.md) for at downloade den allerede bygget Kovri og checksum fil. Bare installer og start Kovri, også er du klar!

## Trin 1. Hvis du bygger er der nogle minimums krav der skal overholdes


### Linux / MacOSX / FreeBSD 11 / OpenBSD 6
- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58 (se platforms-specifikke versions advarsler)
- [OpenSSL](https://openssl.org/) (altid den seneste stabile version)

### Windows
- [MSYS2](https://msys2.github.io/)
- [MinGW-w64](http://mingw-w64.org/doku.php)

Valgfri:

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 eller senere på FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6 (Anbefalet hvis du er bag en NAT uden adgang til den)
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

### MacOSX
- [Homebrew](http://brew.sh/)

#### Note: et minimum af 1 GiB RAM er foreslået til bygge miljøet (se [#403](https://github.com/monero-project/kovri/issues/403) for detaljer)

## Trin 2. Installer afhængigheder 

#### Note: for container muligheder (som Docker og snapcraft), kig i [Bruger Guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/da/bruger_guide.md)

### Ubuntu Xenial (16.04)
Påkrævede afhængigheder:
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ and libssl installed by default
```
Valgfrie afhængigheder:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For brugere bag en begrænsende NAT
```

### Ubuntu Trusty (14.04)
Du kan enten bygge Boost fra kildekode eller bruge PPA 
Nedenunder er instruktioner til PPA:

Påkrævede afhængigheder:
```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo add-apt-repository ppa:kojoley/boost
$ sudo apt-get update
$ sudo apt-get install libboost-{chrono,log,program-options,date-time,thread,system,filesystem,regex,test}1.58-dev
$ sudo apt-get install git g++-4.9 cmake libboost-all-dev libssl-dev libssl1.0.0
```
Valgfrie afhængigheder:
```bash
$ sudo apt-get install clang-3.5
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For brugere bag en begrænsende NAT
```

### Debian (stable)
Vi bliver nødt til at hente fra ```testing``` for ```Boost 1.58+``` og på grund af [broken CMake](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=826656). Af hensyn til dokumentation ville vi hente alle afhængigheder fra ```testing```. Hvis du ikke er bekendt med apt-pinning, fortsæt med følgende før du installere afhængigheder:

- Opret og rediger ```/etc/apt/preferences.d/custom.pref```
- Indsæt and gem følgende:

```
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650
```
- Opret og rediger ```/etc/apt/sources.list.d/custom.list```
```
# Stabil
deb [Skriv dit spejlbillede her] stable main non-free contrib
# Testing
deb [Skriv dit spejlbillede her] testing main non-free contrib
```
- Erstat ```[Skriv dit spejlbillede her]``` med dit spejlbillede (kig i ```/etc/apt/sources.list```)
- Kør ```$ sudo apt-get update```
- Installer afhængigheder med  ```-t testing``` skift:

Påkrævede afhængigheder:
```bash
$ sudo apt-get -t testing install git g++ cmake libboost-all-dev libssl-dev libssl1.0.0
```
Valgfrie afhængigheder:
```bash
$ sudo apt-get -t testing install clang
$ sudo apt-get -t testing install doxygen graphviz
$ sudo apt-get -t testing install libminiupnpc-dev #For brugere bag en begrænsende NAT
```

### Arch Linux
Påkrævede afhængigheder:
```bash
$ sudo pacman -Syu cmake boost  # gcc/g++ and openssl installed by default
```
Valgfrie afhængigheder:
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc #For brugere bag en begrænsende NAT
```

### Mac OSX
Påkrævede afhængigheder:
```bash
$ brew install cmake boost openssl # clang installed by default
```
Valgfrie afhængigheder:
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc #For brugere bag en begrænsende NAT
```

### FreeBSD 11
Påkrævede afhængigheder:
```bash
$ sudo pkg install git cmake gmake clang36 boost-libs openssl
```
Valgfrie afhængigheder:
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc #For brugere bag en begrænsende NAT
```
**Note: kig i FreeBSD bygge instruktioner nedenunder**

### OpenBSD 6
Påkrævede afhængigheder:
```bash
$ sudo pkg_add bash git cmake gmake g++ llvm
```
Valgfrie afhængigheder:
```bash
$ sudo pkg_add miniupnpc #For brugere bag en begrænsende NAT
$ sudo pkg_add doxygen graphviz
```

# Byg seneste boost
```bash
# Hent seneste boost
$ wget [seneste boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd seneste_boost/

# Download og anvend opdateringer
# https://svn.boost.org/trac/boost/attachment/ticket/12575/boost-1.62-asio-libressl.patch
# https://gist.githubusercontent.com/laanwj/bf359281dc319b8ff2e1/raw/92250de8404b97bb99d72ab898f4a8cb35ae1ea3/patch-boost_test_impl_execution_monitor_ipp.patch

# Byg boost
$ echo 'using gcc : : eg++ : "-fvisibility=hidden -fPIC" "" "ar" "strip"  "ranlib" "" : ;' > user-config.jam
$ config_opts="runtime-link=shared threadapi=pthread threading=multi link=static variant=release --layout=tagged --build-type=complete --user-config=user-config.jam -sNO_BZIP2=1"
$ ./bootstrap.sh --without-icu --with-libraries=chrono,log,program_options,date_time,thread,system,filesystem,regex,test
$ sudo ./b2 -d2 -d1 ${config_opts} --prefix=${BOOST_PREFIX} stage
$ sudo ./b2 -d0 ${config_opts} --prefix=${BOOST_PREFIX} install
```
**Note: se OpenBSD bygge instruktioner nedenunder**

### Windows (MSYS2/MinGW-64)
* Download [MSYS2 installer](http://msys2.github.io/), 64-bit eller 32 efter dit behov, og kør den.
* Brug den associerede genvej med din arkitektur for at starte MSYS2 miljøet. På et 64-bit system ville det være MinGW-w64 Win64 Shell shortcut. Bemærk at hvis du kører 64-bit Windows, ville du have både 64-bit og 32-bit miljøer
* Opdater pakkerne i din MSYS2 installation:
```
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
* For dem af jer der allerede har kendskab til pacman, kan i køre den normale ```pacman -Syu``` for at opdatere, men du kan få fejl og være nødt til at genstarte MSYS2 hvis pacman's afhængigheder er opdateret.
* Installer afhængigheder: ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Valgfri: ```mingw-w64-x86_64-doxygen```  (Du får brug for [Graphviz](http://graphviz.org/doc/winbuild.html) til doxygen)
* Note: Du får brug for  ``` mingw-w64-x86_64-miniupnpc``` hvis du er bag en begrænsende NAT firewall.

## Trin 3. Byg

### 1. Klon depotet
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### 2. Byg Kovri og undermodul afhængigheder med en kommando
```bash
$ make  # for at formindske bygge-tiden, kør `make -j <tilgængelige CPU kerner>`. Eksempel: `make -j4`
```

### 3. Installer
```bash
$ make install
```

- Slut-brugerne SKAL køre `make install` til nye installationer
- Udviklere BURDE køre `make install` efter et frisk build

### Andre muligheder du kan bruge i stedet for trin 2:

For en akkurat og komplet liste af muligheder, se targets i [Makefile](https://github.com/monero-project/kovri/blob/master/Makefile).

#### Noter
- Alle bygge resultater (inkluderet Doxygen) ville være i bygge resultatets mappe

### Clang
For at bygge med clang, **skal* du eksportere følgende:

```bash
$ export CC=clang CXX=clang++  # erstat ```clang``` med en clang version/sti efter eget valg
```

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36  # Or higher clang version
$ gmake && gmake install
```
- Erstat ```make``` med ```gmake``` for alle andre bygge muligheder


### OpenBSD
```bash
$ export CC=clang CXX=clang++  # clang er anbefalet, ellers egcc/eg++
$ gmake && gmake install
```
- Erstat ```make``` med ```gmake``` for alle andre bygge muligheder


### (Valgfri) brugdefineret data sti
Du kan brugerdefinere Kovri's datasti efter dine behov. Bare eksporter
```KOVRI_DATA_PATH```; eksempel:

```bash
$ export KOVRI_DATASTI=$HOME/.another-
kovri-data-sti && make && make install
```

## Trin 4. Fortsæt til bruger guiden Læs [bruge guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/da/bruger_guide.md) for at starte

## Docker

Alternativt, hvis du bruger Docker, ville følgende bygge billedet for dig.


```bash
$ docker build -t geti2p/kovri .
```

## Fuzz test

Fra [reference](http://llvm.org/docs/LibFuzzer.html) : "LibFuzzer er under aktiv udvikling så du ville få brug for den nuværende (eller i det mindste en af de meget seneste) version af Clang compiler"

Hent en nylig version af clang:

```bash
$ cd ~/ && mkdir TMP_CLANG && git clone https://chromium.googlesource.com/chromium/src/tools/clang TMP_CLANG/clang
$ ./TMP_CLANG/clang/scripts/update.py
$ cd --
```

Hent libFuzzer:

```bash
$ git clone https://chromium.googlesource.com/chromium/llvm-project/llvm/lib/Fuzzer contrib/Fuzzer
```

Byg Kovri med fuzz test slået til:

```bash
$ PATH="~/third_party/llvm-build/Release+Asserts/bin:$PATH" CC=clang CXX=clang++ make fuzz-tests
```

Brug (Eksempel til RouterInfo):

```bash
mkdir RI_CORPUS MIN_RI_CORPUS
find ~/.kovri/core/network_database/ -name "router_info*" -exec cp {} RI_CORPUS \;
./build/kovri-util fuzz --target=routerinfo -merge=1 MIN_RI_CORPUS RI_CORPUS
./build/kovri-util fuzz --target=routerinfo -jobs=2 -workers=2 MIN_RI_CORPUS
```
