## Paso 1. Requerimientos minimos

#### Note: Debido al issue [#403](https://github.com/monero-project/kovri/issues/403), se sugiere un minimo de 1GB de RAM para el entorno de desarrollo.

### Linux / MacOSX / FreeBSD 10
- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58
- [OpenSSL](https://openssl.org/) (siempre la ultima version estable)

### Windows
- [MSYS2](https://msys2.github.io/)
- [MinGW-w64](http://mingw-w64.org/doku.php)

Opcional:

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 on FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6 (Recomendado si estas detras de una NAT sin acceso a ella)
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

### MacOSX
- [Homebrew](http://brew.sh/)

## Paso 2. Instalacion de dependencias

### Ubuntu Xenial (16.04)
Dependencias requeridas:
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ y libssl instalados por defecto
```
Dependencias opcionales:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #Para usuarios bajo una NAT restrictiva
```

### Ubuntu Trusty (14.04)
Puedes compilar Boost desde las fuentes o usar PPA
Abajo estan las instrucciones para PPA:

Dependencias requeridas:
```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo add-apt-repository ppa:kojoley/boost
$ sudo apt-get update
$ sudo apt-get install libboost-{chrono,log,program-options,date-time,thread,system,filesystem,regex,test}1.58-dev
$ sudo apt-get install git g++-4.9 cmake libboost-all-dev libssl-dev libssl1.0.0
```
Dependencias opcionales:
```bash
$ sudo apt-get install clang-3.5
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #Para usuarios bajo una NAT restrictiva
```

### Debian (stable)

Necesitamos copiar ```testing``` desde ```Boost 1.58+``` por culpa de un [CMake roto](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=826656). Para fines de documentacion, vamos a copiar todas las dependencias desde ```testing```. Si no estas familiriarizado con apt-pinning, procede con lo siguiente ants de instalar las dependencias:

- Crea y edita ```/etc/apt/preferences.d/custom.pref```
- Escribe y guarda lo siguiente:

```
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650
```
- Crea y edita ```/etc/apt/sources.list.d/custom.list```
```
# Stable
deb [Aqui va tu mirrior] stable main non-free contrib
# Testing
deb [Aqui va tu mirrior] testing main non-free contrib
```
- Reemplaza ```[Aqui va tu mirrior]``` con tu mirror (ve el archivo ```/etc/apt/sources.list```)
- Corre ```$ sudo apt-get update```
- Instala las dependencias con la bandera:  ```-t testing```:

Dependencias requeridas:
```bash
$ sudo apt-get -t testing install git g++ cmake libboost-all-dev libssl-dev libssl1.0.0
```
Dependencias opcionales:
```bash
$ sudo apt-get -t testing install clang
$ sudo apt-get -t testing install doxygen graphviz
$ sudo apt-get -t testing install libminiupnpc-dev #Para usuarios bajo una NAT restrictiva
```

### Arch Linux
Dependencias requeridas:
```bash
$ sudo pacman -Syu cmake boost  # gcc/g++ y openssl instalados por defecto
```
Dependencias opcionales:
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc #Para usuarios bajo una NAT restrictiva
```

### Mac OSX
Dependencias requeridas:
```bash
$ brew install cmake boost openssl # clang instalado por defecto
```
Dependencias opcionales:
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc #Para usuarios bajo una NAT restrictiva
```

### FreeBSD 10
Dependencias opcionales:
```bash
$ sudo pkg install git cmake gmake clang36 openssl
# Compila el ultimo Boost (1.58 minimo)
$ wget [latest boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd latest_boost
$ ./bootstrap.sh --with-toolset=clang  # esta bien compilar con clang 3.5
$ sudo ./b2 --toolset=clang install
```
Dependencias opcionales:
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc #Para usuarios bajo una NAT restrictiva
```
**Note: ver instrucciones de compilado para FreeBSD abajo**

### Windows (MSYS2/MinGW-64)
* Descargar el [instalador de MSYS2](http://msys2.github.io/), 64-bit o 32-bit de ser necesario, y ejecutarlo.
* Usa el acceso directo asociado con tu arquitectura para iniciar el entorno MSYS2. En sistemas 64-bit seria MinGW-w64 Win64 Shell. Nota que si estas coriendo Windows 64-bits, necesitaras ambos entornos 64 y 32 bits.
* Actualiza el paquete en tu MSYS2:
```
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
* Para los que son familiares con pacman, pueden correr normalmente ```pacman -Syu``` para actualizar, pero pueden surgir errores y se necesitaria reiniciar MSYS2 si las dependencias de pacman son actualizadas.
* Instala las dependencias: ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Opcional: ```mingw-w64-x86_64-doxygen```  (necesitaras [Graphviz](http://graphviz.org/doc/winbuild.html) para doxygen)
* Nota: vas a necesitar ``` mingw-w64-x86_64-miniupnpc``` si estas detras de un firewall NAT restrictivo.

## Paso 3. Compilar

### 1. Clona el repositorio
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```
### 2. Compila Kovri y las dependencias submodulos con un comando
```bash
$ make # para acortar el tiempo de compilado, corre make -j [CPU cores disponibles]
```
### 3. Instala los recursos (archivos de configuracion + recursos de paquetes)
```bash
$ make install-resources
```

- Usuarios finales **DEBEN** correr ```make install-resources``` para las nuevas instalaciones
- Desarrolladores **DEBERIAN** correr ```make install-resources``` despues de cada fetch

### Otras opciones que pueden usar en el paso 2:

- ```make upnp``` produce un binario vanilla con soporte UPnP (requiere [MiniUPnP](https://github.com/miniupnp/miniupnp/releases))
- ```make optimized-hardening``` produce un binario UPnP, optimizado y fortalecido
- ```make all-options``` produce un binario UnPN activado, y optimizado y fortalecido
- ```make tests``` produce todos los benchmarks y unit-tests
- ```make tests-optimized-hardening``` produce todos los benchmarks y unit-tests con fortalecimiento optimizado
- ```make static``` produce un binario estatico

### Otras opciones disponibles
- ```make doxygen``` produce la documentacion de Doxygen
- ```make clean``` limpia el directorio de compilacion y salida de Doxygen
- ```make help``` muestra las opciones de compilado de CMake

#### Notas
- la salida de Doxygen sera en el directorio ```doc```
- todas las demas salidas seran en el directorio ```build```

### Clang
Para compilar con clang, **debes** exportar lo siguiente:

```bash
$ export CC=clang CXX=clang++ 
```
- reemplazar ```clang``` con una version de tu eleccion

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36
$ gmake && gmake install-resources
```
- reemplazar ```make``` con ```gmake``` para todas las otras opciones de compilacion

### (Opcional) directorio de datos personalizado
Puedes personalizar el directorio de datos de Kovri como gustes. Simplemente exporta ```KOVRI_DATA_PATH```;:

```bash
$ export KOVRI_DATA_PATH=$HOME/.another-kovri-data-path && make && make install-resources
```

## Paso 4. Proceder con la guia de usuario
Lee la [guia de usuario](https://github.com/monero-project/kovri-docs/blob/master/i18n/es/user_guide.md) para comenzar

## Docker

Alternativamente, si usas Docker, lo siguiente compilara la imagen por ti.

```bash
$ docker build -t geti2p/kovri .
```
