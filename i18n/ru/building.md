## Шаг 1. Минимальные требования

#### Примечание: Из-за [#403](https://github.com/monero-project/kovri/issues/403), требуется как минимум 1 Gb ОЗУ.    

### Linux / MacOSX / FreeBSD 10
- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58
- [OpenSSL](https://openssl.org/) (всегда последняя стабильная версия)

### Windows
- [MSYS2](https://msys2.github.io/)
- [MinGW-w64](http://mingw-w64.org/doku.php)

Выборочно:

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 on FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6 (Рекомендуется, если вы находитесь за NAT и не имеете доступа к нему)
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

### MacOSX
- [Homebrew](http://brew.sh/)

## Шаг 2. Установить зависимости

### Ubuntu Xenial (16.04)
Требуемые зависимости:
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ and libssl installed by default
```
Опциональные зависимости:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For users behind a restrictive NAT
```

### Ubuntu Trusty (14.04)
You can either build Boost from source or use PPA
Below are instructions for PPA:

Требуемые зависимости:
```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo add-apt-repository ppa:kojoley/boost
$ sudo apt-get update
$ sudo apt-get install libboost-{chrono,log,program-options,date-time,thread,system,filesystem,regex,test}1.58-dev
$ sudo apt-get install git g++-4.9 cmake libboost-all-dev libssl-dev libssl1.0.0
```
Опциональные зависимости:
```bash
$ sudo apt-get install clang-3.5
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For users behind a restrictive NAT 
```

### Debian (stable)
Нам нужно отвязать ```testing``` для ```Boost 1.58+``` из-за [сломанного CMake](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=826656). Согласно документации мы удаляем зависимости от ```testing```. Если вы не знакомы с apt-pinning, выполните следующие действия перед установкой зависимостей:

- Создайте и отредактируйте ```/etc/apt/preferences.d/custom.pref```
- Введите и сохраните следующее:

```
Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650
```
- Создайте и отредактируйте ```/etc/apt/sources.list.d/custom.list```
```
# Стабильная
deb [Enter your mirror here] stable main non-free contrib
# Тестируемая
deb [Enter your mirror here] testing main non-free contrib
```
- Замените ```[Enter your mirror here]``` with your mirror (see ```/etc/apt/sources.list```)
- Запустите ```$ sudo apt-get update```
- Установите зависимости для ```-t testing``` переключения:

Требуемые зависимости:
```bash
$ sudo apt-get -t testing install git g++ cmake libboost-all-dev libssl-dev libssl1.0.0
```
Опциональные зависимости:
```bash
$ sudo apt-get -t testing install clang
$ sudo apt-get -t testing install doxygen graphviz
$ sudo apt-get -t testing install libminiupnpc-dev #For users behind a restrictive NAT 
```

### Arch Linux
Required dependencies:
```bash
$ sudo pacman -Syu cmake boost  # gcc/g++ and openssl installed by default
```
Требуемые зависимости:
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc #For users behind a restrictive NAT 
```

### Mac OSX
Требуемые зависимости:
```bash
$ brew install cmake boost openssl # clang installed by default
```
Опциональные зависимости:
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc #For users behind a restrictive NAT 
```

### FreeBSD 10
Требуемые зависимости:
```bash
$ sudo pkg install git cmake gmake clang36 openssl
# Build latest boost (1.58 minimum)
$ wget [latest boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd latest_boost
$ ./bootstrap.sh --with-toolset=clang  # OK to build with clang 3.5
$ sudo ./b2 --toolset=clang install
```
Опциональные зависимости:
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc #For users behind a restrictive NAT 
```
**Примечание: см. инструкции по сборке FreeBSD ниже**

### Windows (MSYS2/MinGW-64)
* загрузите [MSYS2 инсталлятор](http://msys2.github.io/), 64-bit или 32-bit в зависимости от вашей операционной системы, и запустите его.
* Используйте ярлык, связанный с вашей архитектурой, для запуска среды MSYS2. В 64-битных системах ярлык MinGW-w64 Win64. Примечание: если вы используете 64-битную Windows, у вас будут 64-разрядная и 32-разрядная среды.
* Обновите пакеты в вашем инсталляторе MSYS2:
```
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
*  Для тех, кто уже знаком с pacman, вы можете запустить обычный ```pacman -Syu``` для обновления, но могут возникнуть ошибки и потребуется перезапуск MSYS2 если зависимости обновятся.
* Установите зависимости: ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Optional: ```mingw-w64-x86_64-doxygen```  (you'll need [Graphviz](http://graphviz.org/doc/winbuild.html) for doxygen)
* Note: You'll need  ``` mingw-w64-x86_64-miniupnpc``` if you are behind a restrictive NAT firewall.

## Шаг 3. Сборка   

### 1. Скопируйте репозиторий
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```
### 2. Соберите Kovri и подмодули зависимостей одной командой
```bash
$ make # to decrease build-time, run make -j [available CPU cores]
```
### 3. Установите ресурсы (файлы конфигурации + ресурсы пакета)
```bash
$ make install
```

- Пользователи ДОЛЖНЫ ЗАПУСКАТЬ ```make install``` для новой установки
- Разработчики ДОЛЖНЫ ЗАПУСКАТЬ ```make install``` после fresh fetch

### Другие варианты, которые вы можете использовать вместо шага 2:

- ```make upnp``` создает классическую двоичную систему с поддержкой UPnP (требует [MiniUPnP](https://github.com/miniupnp/miniupnp/releases))
- ```make optimized-hardening``` создает жестко-оптимизированный бинарник
- ```make all-options``` создает жестко-оптимизированный бинарник, с поддержкой UPnP
- ```make tests``` производит все unit тесты и бэнчмарки
- ```make tests-optimized-hardening``` производит все unit тесты и бэнчмарки с жесткой оптимизацией
- ```make static``` создает статичный бинарник

### Другие доступные параметры
- ```make doxygen``` создает Doxygen документацию
- ```make clean``` очищает директорию сборки и вывод Doxygen
- ```make help``` показывает доступные варианты сборки CMake

#### Примечание
- Сборки Doxygen будут находиться в каталоге ```doc```
- Все остальные сборки будут находиться в каталоге `` build```

### Clang
Чтобы осуществить сборку с помощью clang, вы** должны** экспортировать следующее:

```bash
$ export CC=clang CXX=clang++  # replace ```clang``` with a clang version/path of your choosing
```

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36
$ gmake && gmake install
```
- Заменить ```make``` with ```gmake``` для всех других вариантов сборки

###(Необязательно) Пользовательская директория
Вы можете настроить пользовательскую директорию Kovri по своему вкусу. Просто экспортируйте `` `KOVRI_DATA_PATH```; пример:

```bash
$ export KOVRI_DATA_PATH=$HOME/.another-kovri-data-path && make && make install
```

## Шаг 4. Перейдите к руководству пользователя
Прочитайте [Руководство пользователя](https://github.com/monero-project/kovri-docs/blob/master/i18n/ru/user_guide.md) для начала работы
## Docker

Кроме того, если вы используете Docker, следующее будет актуально для вас.

```bash
$ docker build -t geti2p/kovri .
```
