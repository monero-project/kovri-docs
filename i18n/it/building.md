## Step 1. Requisiti minimi

Nota: Conseguentemente a [#403](https://github.com/monero-project/kovri/issues/403), è richiesto almeno un minimo di 1 GiB di RAM per i seguenti ambienti di compilazione..

### Linux / MacOSX / FreeBSD 10
- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58
- [OpenSSL](https://openssl.org/) (sempre l'ultima versione stabile disponibile)

### Windows
- [MSYS2](https://msys2.github.io/)
- [MinGW-w64](http://mingw-w64.org/doku.php)

Opzionali:

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 su FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6 (Raccomandato se sei dietro ad un NAT senza potervi accedere)
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

### MacOSX
- [Homebrew](http://brew.sh/)

## Step 2. Installa le dipendenze

### Ubuntu Xenial (16.04)
Dipendenze richieste:
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ e libssl installate di default
```
Dipendenze opzionali:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #Per utenti dietro un NAT restrittivo
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
$ sudo apt-get install libminiupnpc-dev #Per utenti dietro un NAT restrittivo 
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
$ sudo apt-get -t testing install libminiupnpc-dev #Per utenti dietro un NAT restrittivo 
```

### Arch Linux
Dipendenze richieste:
```bash
$ sudo pacman -Syu cmake boost  # gcc/g++ e openssl installati di default
```
Dipendenze opzionali:
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc #Per utenti dietro un NAT restrittivo 
```

### Mac OSX
Dipendenze richieste:
```bash
$ brew install cmake boost openssl # clang installato di default
```
Dipendenze opzionali:
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc #Per utenti dietro un NAT restrittivo 
```

### FreeBSD 10
Dipendenze richieste:
```bash
$ sudo pkg install git cmake gmake clang36 openssl
# Build ultimo boost (minimo 1.58)
$ wget [ultimo boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd latest_boost
$ ./bootstrap.sh --with-toolset=clang  # Build with clang 3.5 OK
$ sudo ./b2 --toolset=clang install
```
Dipendenze opzionali:
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc #Per utenti dietro un NAT restrittivo 
```
**Nota: guarda le istruzioni per la build FreeBSD qui sotto**

### Windows (MSYS2/MinGW-64)
* Scarica [MSYS2 installer](http://msys2.github.io/), 64 bit o 32 bit, dipendentemente dal tuo computer ed eseguilo..
* Usa il collegamento associato con la tua architettura per lanciare l'ambiente MSYS2. Nota che se sei su Windows 64 bit, avrai tutti e due gli ambienti, 64 e 32 bit.
* Aggiorna i pacchetti con i seguenti comandi:
```
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
* Chi di voi ha già familiarità con pacman può usare normalmente ```pacman -Syu``` per aggiornare, ma potresti ricevere degli errori e dover far ripartire MSYS2 se le dipendenze di pacman sono aggiornate.
* Installa dipendenze: ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Opzionale: ```mingw-w64-x86_64-doxygen```  (you'll need [Graphviz](http://graphviz.org/doc/winbuild.html) for doxygen)
* Nota: Avrai bisogno di  ``` mingw-w64-x86_64-miniupnpc``` se sei dietro un firewall NAT restrittivo.

## Step 3. Build   

### 1. Clona la repository
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```
### 2. Build Kovri e le dipendenze dei submoduli con un comando
```bash
$ make # per diminuire il tempo di build, usa make -j [CPU cores disponibili]
```
### 3. Installa risorse (file di configurazione + risorse pacchetti)
```bash
$ make install-resources
```

- Gli utenti finali DEVONO usare ```make install-resources``` per nuove installazioni
- Gli sviluppatori DOVREBBERO usare ```make install-resources``` dopo aver eseguito un fetch

### Altre opzioni utilizzabili al posto di quelle in step 2:

- ```make upnp``` produce vanilla binary con supporto UPnP (richiede [MiniUPnP](https://github.com/miniupnp/miniupnp/releases))
- ```make optimized-hardening``` produce ottimizzati, hardened file binari
- ```make all-options``` produce ottimizzati, hardened, binari con UPnP abilitato
- ```make tests``` produce tutti i test delle unità e benchmarks
- ```make tests-optimized-hardening``` produce tutti i test delle unità e benchmarks con hardening ottimizzato
- ```make static``` produce binari statici

### Altre opzioni disponibili
- ```make doxygen``` produce documentazione Doxygen
- ```make clean``` pulisce cartelle build e gli output Doxygen
- ```make help``` mostra le opzioni di build CMake disponibili

#### Note
- L'output di Doxygen sarà nella cartella```doc```
- Tutti gli altri output di build saranno nella cartella ```build```

### Clang
Per eseguire il build con clang, **devi** esportare i seguenti:

```bash
$ export CC=clang CXX=clang++  # rimpiazza ```clang``` con una versione/percorso di clang di tua scelta
```

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36
$ gmake && gmake install-resources
```
- Rimpiazza ```make``` con ```gmake``` per tutte le altre opzioni di build

### (Opzionale) percorso data personalizzato
Puoi personalizzare il percorso dei dati di Kovri a tuo piacimento. Semplicemente esporta ```KOVRI_DATA_PATH```; esempio:

```bash
$ export KOVRI_DATA_PATH=$HOME/.another-kovri-data-path && make && make install-resources
```

## Step 4. Procedi con la guida utente
Leggi la [guida utente](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/user_guide.md) per iniziare

## Docker

Alternativamente, se usi Docker, la stringa seguente eseguirà il build dell'immagine per te.

```bash
$ docker build -t geti2p/kovri .
```
