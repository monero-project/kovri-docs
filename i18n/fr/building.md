## Étape 0. (Facultatif) Vous pouvez passer la compilation et utiliser directement les binaires

Rendez-vous sur le [README](https://github.com/monero-project/kovri/blob/master/README.md) pour télécharger une version pré-compilée de kovri et les fichiers *checksum*. Vous n'aurez plus qu'à installer et démarrer kovri, et vous êtes partis !

## Étape 1. (Si vous compilez) La configuration système minimale

### Linux / MacOSX / FreeBSD 11 / OpenBSD 6
- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58 (voir les mises en garde spécifiques à chaque plateforme)
- [OpenSSL](https://openssl.org/) (utiliser toujours la version stable la plus récente)

### Windows
- [MSYS2](https://msys2.github.io/)
- [MinGW-w64](http://mingw-w64.org/doku.php)

Facultatif :

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 ou plus si sur FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6 (Recommandé si vous êtes derrière un NAT sans accès à celui-ci)
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

### MacOSX
- [Homebrew](http://brew.sh/)

**Note : un minimum de 1 GiB de RAM est recommandé pour compiler (voir [#403](https://github.com/monero-project/kovri/issues/403) pour plus de détails)**

## Étape 2. Installations des dépendances

**Note : pour utiliser des *containers* (comme Docker et snapcraft), voir le [Guide d'Utilisation](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/user_guide.md)**

### Ubuntu Xenial (16.04)
Dépendances requises :
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ et libssl installés par défaut
```
Dépendances facultatives :
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev # pour les utilisateurs derrière un NAT restrictif
```

### Ubuntu Trusty (14.04)
Vous pouvez ou bien compiler Boost depuis les sources ou bien utiliser PPA
Voici les instructions pour PPA :

Dépendances requises :
```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo add-apt-repository ppa:kojoley/boost
$ sudo apt-get update
$ sudo apt-get install libboost-{chrono,log,program-options,date-time,thread,system,filesystem,regex,test}1.58-dev
$ sudo apt-get install git g++-4.9 cmake libboost-all-dev libssl-dev libssl1.0.0
```
Dépendances facultatives :
```bash
$ sudo apt-get install clang-3.5
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev # pour les utilisateurs derrière un NAT restrictif
```

### Debian (stable)
We'll need to pull from ```testing``` for ```Boost 1.58+``` and because of a [broken CMake](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=826656). For documentation's sake, we will pull all dependencies from ```testing```. If you're unfamiliar with apt-pinning, proceed with the following before installing dependencies:

- Create and edit ```/etc/apt/preferences.d/custom.pref```
- Enter and save the following:

```
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650
```
- Create and edit ```/etc/apt/sources.list.d/custom.list```
```
# Stable
deb [Enter your mirror here] stable main non-free contrib
# Testing
deb [Enter your mirror here] testing main non-free contrib
```
- Replace ```[Enter your mirror here]``` with your mirror (see ```/etc/apt/sources.list```)
- Run ```$ sudo apt-get update```
- Install dependencies with the ```-t testing``` switch:

Dépendances requises :
```bash
$ sudo apt-get -t testing install git g++ cmake libboost-all-dev libssl-dev libssl1.0.0
```
Dépendances facultatives :
```bash
$ sudo apt-get -t testing install clang
$ sudo apt-get -t testing install doxygen graphviz
$ sudo apt-get -t testing install libminiupnpc-dev # pour les utilisateurs derrière un NAT restrictif
```

### Arch Linux
Dépendances requises :
```bash
$ sudo pacman -Syu cmake boost  # gcc/g++ and openssl installed by default
```
Dépendances facultatives :
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc # pour les utilisateurs derrière un NAT restrictif
```

### Mac OSX
Dépendances requises :
```bash
$ brew install cmake boost openssl # clang installed by default
```
Dépendances facultatives :
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc # pour les utilisateurs derrière un NAT restrictif
```

### FreeBSD 11
Dépendances requises :
```bash
$ sudo pkg install git cmake gmake clang36 boost-libs openssl
```
Dépendances facultatives :
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc # pour les utilisateurs derrière un NAT restrictif
```
**Note: see FreeBSD build instructions below**

### OpenBSD 6
Dépendances requises :
```bash
$ sudo pkg_add bash git cmake gmake g++ llvm
```
Dépendances facultatives :
```bash
$ sudo pkg_add miniupnpc # pour les utilisateurs derrière un NAT restrictif
$ sudo pkg_add doxygen graphviz
```

# Compiler la version de boost la plus récente
```bash
# Obtenez la dernière version de boost
$ wget [latest boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd latest_boost/

# Téléchargez et appliquez les correctifs
# https://svn.boost.org/trac/boost/attachment/ticket/12575/boost-1.62-asio-libressl.patch
# https://gist.githubusercontent.com/laanwj/bf359281dc319b8ff2e1/raw/92250de8404b97bb99d72ab898f4a8cb35ae1ea3/patch-boost_test_impl_execution_monitor_ipp.patch

# Compilez boost
$ echo 'using gcc : : eg++ : "-fvisibility=hidden -fPIC" "" "ar" "strip"  "ranlib" "" : ;' > user-config.jam
$ config_opts="runtime-link=shared threadapi=pthread threading=multi link=static variant=release --layout=tagged --build-type=complete --user-config=user-config.jam -sNO_BZIP2=1"
$ ./bootstrap.sh --without-icu --with-libraries=chrono,log,program_options,date_time,thread,system,filesystem,regex,test
$ sudo ./b2 -d2 -d1 ${config_opts} --prefix=${BOOST_PREFIX} stage
$ sudo ./b2 -d0 ${config_opts} --prefix=${BOOST_PREFIX} install
```
**Note : voir plus bas les instructions de compilation de OpenBSD**

### Windows (MSYS2/MinGW-64)
* Téléchargez l'[installateur MSYS2](http://msys2.github.io/), 64-bit ou 32-bit en fonction de votre système, et lancez-le.
* Utilisez le raccourci associé à votre architecture pour lancer l'environnement MSYS2. Sur les systèmes 64-bit, ce devrait être le raccourci Shell MinGW-w64 Win64. Notez que si vous êtes sur Windows 64-bit, vous aurez les 2 environnements 64-bit et 32-bit.
* Mettez à jour les paquets de votre installation MSYS2 :
```bash
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
* Pour ceux d'entre vous qui connaissent déjà pacman, vous pouvez lancer ```pacman -Syu``` pour mettre à jour, mais vous pourriez avoir des erreurs et avoir besoin de relancer MSYS2 si les dépendances de pacman sont mises à jour.
* Installez les dépendances : ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Facultatif : ```mingw-w64-x86_64-doxygen```  (vous aurez besoin de [Graphviz](http://graphviz.org/doc/winbuild.html) pour doxygen)
* Note : Vous aurez besoin de ``` mingw-w64-x86_64-miniupnpc``` si vous êtes derrière un pare-feu NAT restrictif.

## Étape 3. Compilation

### 1. Clonez le dépôt
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### 2. Compilez kovri et les dépendances *submodule* en une commande
```bash
$ make  # pour réduire le temps de compilation : `make -j <available CPU cores>`. Par exemple : `make -j4`
```

### 3. Installation
```bash
$ make install
```

- Les utilisateurs DOIVENT lancer `make install` pour les nouvelles installations
- Les développeurs DEVRAIENT lancer `make install` après compilation

### Les autres options que vous pouvez utiliser à la place de l'étape 2 :

Pour une liste complète des options, voir les *targets* dans le fichier [Makefile](https://github.com/monero-project/kovri/blob/master/Makefile).

#### Notes
- Tous les résultats de compilation (y compris Doxygen) se trouveront dans le dossier de résultats de compilation.

### Clang
Pour compiler avec clang, vous **devez** exporter ce qui suit :

```bash
$ export CC=clang CXX=clang++  # remplacez `clang` avec la version de clang ou le chemin de votre choix
```

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36  # ou une version de clang plus récente
$ gmake && gmake install
```
- Remplacez ```make``` avec ```gmake``` pour toutes les autres options de compilation.


### OpenBSD
```bash
$ export CC=clang CXX=clang++  # clang recommendé, ou bien egcc/eg++
$ gmake && gmake install
```
- Remplacez ```make``` avec ```gmake``` pour toutes les autres options de compilation.


### (Facultatif) Chemin custom
Vous pouvez changer le chemin d'accès des données de Kovri. Exportez simplement le ```KOVRI_DATA_PATH```. Par exemple en faisant :

```bash
$ export KOVRI_DATA_PATH=$HOME/.un-autre-chemin-d-accès-kovri && make && make install
```

## Étape 4. Lisez le guide utilisateur
Aidez-vous du [guide utilisateur](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/user_guide.md) pour commencer.

## Docker

Sinon, si vous utilisez Docker, la commande suivante compilera l'image à votre place.

```bash
$ docker build -t geti2p/kovri .
```

## Tests Fuzz

Du [site de LibFuzzer](http://llvm.org/docs/LibFuzzer.html) : "LibFuzzer est en développement actif donc vous aurez besoin de la dernière version (ou au moins une version très récente) du compilateur Clang"

Obtenez une version récente de clang :

```bash
$ cd ~/ && mkdir TMP_CLANG && git clone https://chromium.googlesource.com/chromium/src/tools/clang TMP_CLANG/clang
$ ./TMP_CLANG/clang/scripts/update.py
$ cd --
```

Obtenez libFuzzer :

```bash
$ git clone https://chromium.googlesource.com/chromium/llvm-project/llvm/lib/Fuzzer contrib/Fuzzer
```

Compilez kovri avec les tests fuzz activés :

```bash
$ PATH="~/third_party/llvm-build/Release+Asserts/bin:$PATH" CC=clang CXX=clang++ make fuzz-tests
```

Utilisation (Exemple de RouterInfo) :

```bash
mkdir RI_CORPUS MIN_RI_CORPUS
find ~/.kovri/core/network_database/ -name "router_info*" -exec cp {} RI_CORPUS \;
./build/kovri-util fuzz --target=routerinfo -merge=1 MIN_RI_CORPUS RI_CORPUS
./build/kovri-util fuzz --target=routerinfo -jobs=2 -workers=2 MIN_RI_CORPUS
```
