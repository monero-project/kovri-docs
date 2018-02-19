## Шаг 0. (Необязательный) Пропустить сборку и использовать готовые выпуски

Смотри в [README](https://github.com/monero-project/kovri/blob/master/README.md) как скачать предварительно собранный kovri и checksum файла. Просто установи, запусти kovri и прочь отсюда!

## Шаг 1. Если собирать, то минимальные требования

### Linux / MacOSX / FreeBSD 11 / OpenBSD 6

- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58 (смотри платформозависимые предупреждения)
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

#### Примечание: минимум 1 GiB RAM рекомендуется для сборки окружения (смотри [#403](https://github.com/monero-project/kovri/issues/403) для получения более подробной информации)

## Шаг 2. Установить зависимости

#### Примечание: в случае использования контейнеров (таких как Docker и Snapcraft), смотри [Руководство пользователя](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/user_guide.md)

### Ubuntu Xenial (16.04)
Требуемые зависимости:
```bash
$ sudo apt-get install git cmake libboost-all-dev libssl-dev  # gcc/g++ и libssl установлены по умолчанию
```
Опциональные зависимости:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #For users behind a restrictive NAT
```

### Ubuntu Trusty (14.04)
Можете собрать Boost из исходников или использовать PPA
Ниже инструкции для PPA:

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
$ sudo apt-get install libminiupnpc-dev #для пользователей за ограничительным NAT
```

### Debian-9 (stretch/stable)
Требуемые зависимости:
```bash
$ sudo apt-get install git g++ cmake libboost-all-dev libssl-dev libssl1.0.0
```
Опциональные зависимости:
```bash
$ sudo apt-get install clang
$ sudo apt-get install doxygen graphviz
$ sudo apt-get install libminiupnpc-dev #для пользователей за ограничительным NAT
```

### Arch Linux
Требуемые зависимости:
```bash
$ sudo pacman -Syu cmake boost  # gcc/g++ и openssl установлены по умолчанию
```
Опциональные зависимости:
```bash
$ sudo pacman -S clang
$ sudo pacman -S doxygen graphviz
$ sudo pacman -S miniupnpc #для пользователей за ограничительным NAT
```

### Mac OSX
Требуемые зависимости:
```bash
$ brew install cmake boost openssl # clang установлен по умолчанию
```
Опциональные зависимости:
```bash
$ brew install doxygen graphviz
$ brew install miniupnpc #для пользователей за ограничительным NAT
```

### FreeBSD 11
Требуемые зависимости:
```bash
$ sudo pkg install git cmake gmake clang36 boost-libs openssl
```
Опциональные зависимости:
```bash
$ sudo pkg install doxygen graphviz
$ sudo pkg install miniupnpc #для пользователей за ограничительным NAT
```
**Примечание: см. инструкции по сборке для FreeBSD ниже**

### OpenBSD 6
Требуемые зависимости:
```bash
$ sudo pkg_add bash git cmake gmake g++ llvm
```
Опциональные зависимости:
```bash
$ sudo pkg_add miniupnpc #для пользователей за ограничительным NAT
$ sudo pkg_add doxygen graphviz
```

# Сборка последнего boost
```bash
# Получить boost
$ wget [latest boost] -O latest_boost.tar.bz2
$ tar xvjf latest_boost.tar.bz2 && cd latest_boost/

# Скачать и применить патчи
# https://svn.boost.org/trac/boost/attachment/ticket/12575/boost-1.62-asio-libressl.patch
# https://gist.githubusercontent.com/laanwj/bf359281dc319b8ff2e1/raw/92250de8404b97bb99d72ab898f4a8cb35ae1ea3/patch-boost_test_impl_execution_monitor_ipp.patch

# Собрать boost
$ echo 'using gcc : : eg++ : "-fvisibility=hidden -fPIC" "" "ar" "strip"  "ranlib" "" : ;' > user-config.jam
$ config_opts="runtime-link=shared threadapi=pthread threading=multi link=static variant=release --layout=tagged --build-type=complete --user-config=user-config.jam -sNO_BZIP2=1"
$ ./bootstrap.sh --without-icu --with-libraries=chrono,log,program_options,date_time,thread,system,filesystem,regex,test
$ sudo ./b2 -d2 -d1 ${config_opts} --prefix=${BOOST_PREFIX} stage
$ sudo ./b2 -d0 ${config_opts} --prefix=${BOOST_PREFIX} install
```
**Примечание: см. инструкции по сборке для OpenBSD ниже**

### Windows (MSYS2/MinGW-64)
* загрузите [MSYS2 инсталлятор](http://msys2.github.io/), 64-bit или 32-bit в зависимости от вашей операционной системы, и запустите его.
* Используйте ярлык, соответствующий вашей архитектуре, для запуска среды MSYS2. В 64-битных системах ярлык MinGW-w64 Win64 Shell. Примечание: если вы используете 64-битную Windows, у вас будут 64-разрядное и 32-разрядное окружение.
* Обновите пакеты в вашем установленном MSYS2:
```
pacman -Sy
pacman -Su --ignoregroup base
pacman -Su
```
*  Для тех, кто уже знаком с pacman, вы можете запустить обычный ```pacman -Syu``` для обновления, но могут возникнуть ошибки и потребуется перезапуск MSYS2 если зависимости pacman'a обновятся.
* Установите зависимости: ```pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl```
* Опционально: ```mingw-w64-x86_64-doxygen```  (вам понадобится [Graphviz](http://graphviz.org/doc/winbuild.html) для doxygen)
* Примечание: Вам понадобится  ``` mingw-w64-x86_64-miniupnpc``` если вы находитесь за NAT.

## Шаг 3. Сборка   

### 1. Скопируйте репозиторий
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### 2. Соберите Kovri и модули зависимостей одной командой
```bash
$ make  # to decrease build-time, run `make -j <available CPU cores>`. Example: `make -j4`
```

### 3. Установите
```bash
$ make install
```

- Пользователи ДОЛЖНЫ ЗАПУСКАТЬ ```make install``` для каждой новой установки
- Разработчикам СЛЕДУЕТ ЗАПУСКАТЬ ```make install``` после каждой свежей сборки

### Другие параметры, которые вы можете использовать на этапе 2:

Точный и полный список параметров, ищи в целях(targets) [Makefile](https://github.com/monero-project/kovri/blob/master/Makefile).

#### Примечание
- Все результаты\выводы (outputs) сборки (включая Doxygen) будут находиться папке сборки

### Clang
Чтобы осуществить сборку с помощью clang, вам **необходимо** выполнить следующее:

```bash
$ export CC=clang CXX=clang++  # замените ```clang``` на версию\путь к clang, который вам нужен
```

### FreeBSD
```bash
$ export CC=clang36 CXX=clang++36  # Или более свежая версия clang
$ gmake && gmake install
```
- Замените ```make``` на ```gmake``` для всех других параметров сборки

### OpenBSD
```bash
$ export CC=clang CXX=clang++  # clang рекомендуется, иначе egcc/eg++
$ gmake && gmake install
```
- Замените ```make``` на ```gmake``` для всех других параметров сборки


### (Не обязательно) Изменение пути
Вы можете изменить путь для Kovri как вам угодно. Просто добавьте переменную ```KOVRI_DATA_PATH```; например:

```bash
$ export KOVRI_DATA_PATH=$HOME/.another-kovri-data-path && make && make install
```


## Шаг 4. Перейдите к руководству пользователя
Прочитайте [Руководство пользователя](https://github.com/monero-project/kovri-docs/blob/master/i18n/ru/user_guide.md) для начала работы

## Docker

Кроме того, если вы используете Docker, следующая команда соберет вам образ.

```bash
$ docker build -t geti2p/kovri .
```

## Fuzz тестирование

Из [справки](http://llvm.org/docs/LibFuzzer.html) : "LibFuzzer активно разрабатывается поэтому вам требуется текущая (или достаточно свежая) версия Clang компилятора"

Получить свежую версию clang:

```bash
$ cd ~/ && mkdir TMP_CLANG && git clone https://chromium.googlesource.com/chromium/src/tools/clang TMP_CLANG/clang
$ ./TMP_CLANG/clang/scripts/update.py
$ cd --
```

Получить libFuzzer:

```bash
$ git clone https://chromium.googlesource.com/chromium/llvm-project/llvm/lib/Fuzzer contrib/Fuzzer
```

Собрать kovri с поддержкой fuzz тестирования:

```bash
$ PATH="~/third_party/llvm-build/Release+Asserts/bin:$PATH" CC=clang CXX=clang++ make fuzz-tests
```

Использование (Пример для RouterInfo):

```bash
mkdir RI_CORPUS MIN_RI_CORPUS
find ~/.kovri/core/network_database/ -name "router_info*" -exec cp {} RI_CORPUS \;
./build/kovri-util fuzz --target=routerinfo -merge=1 MIN_RI_CORPUS RI_CORPUS
./build/kovri-util fuzz --target=routerinfo -jobs=2 -workers=2 MIN_RI_CORPUS
```

