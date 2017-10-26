## Schritt 0. (Optional) Erstellung überspringen und stattdessen die Binärdateien verwenden

Gehen Sie zur [README](https://github.com/monero-project/kovri/blob/master/README.md), um das bereits erstellte kovri und die Prüfsummen-Datei herunterzuladen. Einfach installieren, kovri starten und los geht's!

## Schritt 1. Die Mindestanforderungen, falls selbst erstellt wird

### Linux / MacOSX / FreeBSD 11 / OpenBSD 6
- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58 (die plattformspezifischen Versionswarnungen beachten)
- [OpenSSL](https://openssl.org/) (immer die neueste stabile Version verwenden)

### Windows
- [MSYS2](https://msys2.github.io/)
- [MinGW-w64](http://mingw-w64.org/doku.php)

Optional:

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 oder höher auf FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6 (empfohlen, wenn man hinter einer NAT ist, zu der man keinen Zugang hat)
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

### MacOSX
- [Homebrew](http://brew.sh/)

#### Hinweis: es werden mindestens 1 GiB RAM für Erstellungsumgebungen empfohlen (siehe [#403](https://github.com/monero-project/kovri/issues/403) für Details)

## Schritt 2. Abhängigkeiten installieren

#### Hinweis: für Container-Optionen (wie Docker und snapcraft), siehe den [Benutzerleitfaden](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/user_guide.md)

### Ubuntu Xenial (16.04)
Erforderliche Abhängigkeiten:
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ und libssl standardmäßig installiert
```
Optionale Abhängigkeiten:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #Für Benutzer hinter einem restriktiven NAT
```

### Ubuntu Trusty (14.04)
Man kann Boost entweder direkt aus den Quellen erstellen oder PPA verwenden.
Nachstehend findet sich die Anleitung für PPA:

Erforderliche Abhängigkeiten:
```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo add-apt-repository ppa:kojoley/boost
$ sudo apt-get update
$ sudo apt-get install libboost-{chrono,log,program-options,date-time,thread,system,filesystem,regex,test}1.58-dev
$ sudo apt-get install git g++-4.9 cmake libboost-all-dev libssl-dev libssl1.0.0
```
Optionale Abhängigkeiten:
```bash
$ sudo apt-get install clang-3.5
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #Für Benutzer hinter einem restriktiven NAT
```

### Debian (stable)
Für ```Boost 1.58+``` müssen wir von ```testing``` beziehen, auch aufgrund eines[beschädigten CMake](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=826656). Um der Dokumentation willen werden wir alle Abhängigkeiten von ```testing``` beziehen. Wenn Sie mit apt-pinning nicht vertraut sind, fahren Sie wie folgt fort, bevor Sie die Abhängigkeiten installieren:

- Erstellen und bearbeiten Sie ```/etc/apt/preferences.d/custom.pref```
- Das Folgende eingeben und speichern:

```
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650
```
- Erstellen und bearbeiten Sie ```/etc/apt/sources.list.d/custom.list```
```
# Stable
deb [Enter your mirror here] stable main non-free contrib
# Testing
deb [Enter your mirror here] testing main non-free contrib
```
- Ersetzen Sie ```[Enter your mirror here]``` mit Ihrem *mirror* (Spiegelserver) (siehe ```/etc/apt/sources.list```)
- Führen Sie ```$ sudo apt-get update``` aus
- Installieren Sie die Abhängigkeiten mit dem Flag ```-t testing```

Erforderliche Abhängigkeiten:
```bash
$ sudo apt-get -t testing install git g++ cmake libboost-all-dev libssl-dev libssl1.0.0
```
Optionale Abhängigkeiten:
```bash
$ sudo apt-get -t testing install clang
$ sudo apt-get -t testing install doxygen graphviz
$ sudo apt-get -t testing install libminiupnpc-dev #Für Benutzer hinter einem restriktiven NAT
```

### Arch Linux
Erforderliche Abhängigkeiten:
```bash
$ sudo pacman -Syu cmake boost # gcc/g++ und openssl standardmäßig installiert
```
Optionale Abhängigkeiten:
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc #Für Benutzer hinter einem restriktiven NAT
```

### Mac OSX
Erforderliche Abhängigkeiten:
```bash
$ brew install cmake boost openssl # clang standardmäßig installiert
```
Optionale Abhängigkeiten:
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc #Für Benutzer hinter einem restriktiven NAT
```

### FreeBSD 11
Erforderliche Abhängigkeiten:
```bash
$ sudo pkg install git cmake gmake clang36 boost-libs openssl
```
Optionale Abhängigkeiten:
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc #Für Benutzer hinter einem restriktiven NAT
```
**Hinweis: siehe die Erstellungsanleitung für FreeBSD weiter unten**

### OpenBSD 6
Erforderliche Abhängigkeiten:
```bash
$ sudo pkg_add bash git cmake gmake g++ llvm
```
Optionale Abhängigkeiten:
```bash
$ sudo pkg_add miniupnpc #Für Benutzer hinter einem restriktiven NAT
$ sudo pkg_add doxygen graphviz
```

# Aktuelle Boost-Version erstellen
```bash
# Aktuelle Boost-Version herunterladen
$ wget [latest boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd latest_boost/

# Patches herunterladen und anwenden
# https://svn.boost.org/trac/boost/attachment/ticket/12575/boost-1.62-asio-libressl.patch
# https://gist.githubusercontent.com/laanwj/bf359281dc319b8ff2e1/raw/92250de8404b97bb99d72ab898f4a8cb35ae1ea3/patch-boost_test_impl_execution_monitor_ipp.patch

# Boost erstellen
$ echo 'using gcc : : eg++ : "-fvisibility=hidden -fPIC" "" "ar" "strip"  "ranlib" "" : ;' > user-config.jam
$ config_opts="runtime-link=shared threadapi=pthread threading=multi link=static variant=release --layout=tagged --build-type=complete --user-config=user-config.jam -sNO_BZIP2=1"
$ ./bootstrap.sh --without-icu --with-libraries=chrono,log,program_options,date_time,thread,system,filesystem,regex,test
$ sudo ./b2 -d2 -d1 ${config_opts} --prefix=${BOOST_PREFIX} stage
$ sudo ./b2 -d0 ${config_opts} --prefix=${BOOST_PREFIX} install
```
**Hinweis: siehe die Erstellungsanleitung für OpenBSD weiter unten**

### Windows (MSYS2/MinGW-64)
* Laden Sie den [MSYS2-Installer](http://msys2.github.io/) herunter, je nach Bedarf 64-bit oder 32-bit, und starten Sie ihn.
* Nutzen Sie die Verknüpfung, die Ihrer Architektur zugeordnet ist, um die MSYS2-Umgebung zu starten. Auf 64-bit-Systemem wäre das die Verknüpfung MinGW-w64 Win64 Shell. Bitte beachten Sie, dass, falls Sie eine 64-bit-Version des Windows-Betriebssystems ausführen, Sie sowohl eine 64-bit- als auch eine 32-bit-Umgebung haben werden.
* Aktualisieren Sie die Pakete in Ihrer MSYS2-Installation:
```
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
* Wenn Sie bereits mit pacman vertraut sind, können Sie wie gewöhnlich ```pacman -Syu``` zur Aktualisierung ausführen. Sie könnten allerdings Fehler erhalten und gezwungen sein, MSYS2 neu zu starten, falls die Abhängigkeiten von pacman aktualisiert sind.
* Installationsabhängigkeiten: ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Optional: ```mingw-w64-x86_64-doxygen``` (Sie benötigen [Graphviz](http://graphviz.org/doc/winbuild.html) für doxygen)
* Hinweis: Sie benötigen ``` mingw-w64-x86_64-miniupnpc```, falls Sie hinter einer restriktiven NAT-Firewall sind.

## Schritt 3. Erstellen

### 1. Das Repository klonen
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### 2. Kovri und Submodule-Abhängigkeiten mit einem Befehl erstellen
```bash
$ make  # um die Erstellungszeit zu verringern, führen Sie `make -j <available CPU cores>` aus. Zum Beispiel: `make -j4`
```

### 3. Installieren
```bash
$ make install
```

- Endbenutzer MÜSSEN `make install` für Neuinstallationen ausführen
- Entwickler SOLLTEN `make install`nach einer neuerlichen Erstellung ausführen 

### Andere Optionen, die Sie anstelle von Schritt 2 anwenden können:

Eine akkurate und vollständige Liste von Optionen finden Sie unter *targets* im [Makefile](https://github.com/monero-project/kovri/blob/master/Makefile).

#### Hinweise
- Sämtliche während der Erstellung erzeugte Ausgaben (einschließlich Doxygen) sind im Ausgabeverzeichnis der Erstellung (*build output directory*)

### Clang
Um die Erstellung mit clang durchzuführen, **müssen** Sie Folgendes exportieren:

```bash
$ export CC=clang CXX=clang++  # Ersetzen Sie `clang` durch eine/n clang-Version/-Pfad Ihrer Wahl
```

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36  # Oder höhere clang-Version
$ gmake && gmake install
```
- Ersetzen Sie ```make``` durch ```gmake``` bei allen anderen Erstellungsoptionen


### OpenBSD
```bash
$ export CC=clang CXX=clang++  # clang empfohlen, ansonsten egcc/eg++
$ gmake && gmake install
```
- Ersetzen Sie ```make``` durch ```gmake``` bei allen anderen Erstellungsoptionen


### (Optional) Benutzerdefinierter Datenpfad
Sie können Kovris Datenpfad individuell einrichten. Exportieren Sie einfach ```KOVRI_DATA_PATH```, zum Beispiel:

```bash
$ export KOVRI_DATA_PATH=$HOME/.another-kovri-data-path && make && make install
```

## Schritt 4. Mit dem Benutzerleitfaden fortfahren
Lesen Sie zum Einstieg den [Benutzerleitfaden](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/user_guide.md)

## Docker

Falls Sie alternativ Docker nutzen, können Sie das Abbild wie folgt erstellen.

```bash
$ docker build -t geti2p/kovri .
```

## Fuzz-Testing

Von der [libFuzzer-Homepage](http://llvm.org/docs/LibFuzzer.html) : „LibFuzzer wird aktiv weiterentwickelt, Sie benötigen also die neueste (oder zumindest eine jüngere) Version des Clang-Kompilierers.“

Laden Sie eine aktuelle Version von clang herunter:

```bash
$ cd ~/ && mkdir TMP_CLANG && git clone https://chromium.googlesource.com/chromium/src/tools/clang TMP_CLANG/clang
$ ./TMP_CLANG/clang/scripts/update.py
$ cd --
```

Laden Sie libFuzzer herunter:

```bash
$ git clone https://chromium.googlesource.com/chromium/llvm-project/llvm/lib/Fuzzer contrib/Fuzzer
```

Erstellen Sie kovri mit aktiviertem Fuzz-Testing:

```bash
$ PATH="~/third_party/llvm-build/Release+Asserts/bin:$PATH" CC=clang CXX=clang++ make fuzz-tests
```

Anwendung (zum Beispiel für RouterInfo):

```bash
mkdir RI_CORPUS MIN_RI_CORPUS
find ~/.kovri/core/network_database/ -name "router_info*" -exec cp {} RI_CORPUS \;
./build/kovri-util fuzz --target=routerinfo -merge=1 MIN_RI_CORPUS RI_CORPUS
./build/kovri-util fuzz --target=routerinfo -jobs=2 -workers=2 MIN_RI_CORPUS
```
