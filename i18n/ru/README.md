[<img width="300" src="https://static.getmonero.org/images/kovri/logo.png" alt="ˈKoʊvriː" />](https://github.com/monero-project/kovri)

1. [To cover, veil, wrap](https://en.wikipedia.org/wiki/Esperanto)
2. Свободная, децентрализованная технология для обеспечения анонимности, основанная на открытых спецификациях [I2P](https://getmonero.org/resources/moneropedia/i2p.html)

## Отказ от ответственности
- Текущая версия Alpha; проект все еще находится стадии активной разработки (на данный момент он еще не интегрирован с экосистемой Monero)

## Быстрый старт

- Хотите воспользоваться скомпилированными файлами? [Скачайте их ниже](#Загрузки)
- Хотите скомпилировать файлы самостоятельно? [Инструкции по сборке находятся ниже](#Сборка)

## Многоязычный README
Это перевод Kovri README, оригинальный документ (на английском языке) доступен по ссылке: https://github.com/monero-project/kovri/blob/master/README.md

## Загрузки

### Релизы

### [Ночные сборки (самая свежая версия)](https://build.getmonero.org/waterfall)

| Download | Checksum | Status |
| -------- | -------- | ------ |
| [Linux (x86-64)](https://build.getmonero.org/downloads/kovri-latest-linux-amd64.tar.bz2) | [Linux (x86-64)](https://build.getmonero.org/downloads/kovri-latest-linux-amd64.tar.bz2.sha256sum.txt) | [![Linux (x86-64)](https://build.getmonero.org/png?builder=kovri-static-ubuntu-amd64)](https://build.getmonero.org/builders/kovri-static-ubuntu-amd64) |
| [Linux (i686)](https://build.getmonero.org/downloads/kovri-latest-linux-i686.tar.bz2) | [Linux (i686)](https://build.getmonero.org/downloads/kovri-latest-linux-i686.tar.bz2.sha256sum.txt) | [![Linux (i686)](https://build.getmonero.org/png?builder=kovri-static-ubuntu-i686)](https://build.getmonero.org/builders/kovri-static-ubuntu-i686) |
| [Linux (ARMv8)](https://build.getmonero.org/downloads/kovri-latest-linux-armv8.tar.bz2) | [Linux (ARMv8)](https://build.getmonero.org/downloads/kovri-latest-linux-armv8.tar.bz2.sha256sum.txt) | [![Linux (ARMv8)](https://build.getmonero.org/png?builder=kovri-static-debian-arm8)](https://build.getmonero.org/builders/kovri-static-debian-arm8) |
| [Linux (ARMv7)](https://build.getmonero.org/downloads/kovri-latest-linux-armv7.tar.bz2) | [Linux (ARMv8)](https://build.getmonero.org/downloads/kovri-latest-linux-armv7.tar.bz2.sha256sum.txt) | [![Linux (ARMv8)](https://build.getmonero.org/png?builder=kovri-static-ubuntu-arm7)](https://build.getmonero.org/builders/kovri-static-ubuntu-) |
| [macOS (x86-64)](https://build.getmonero.org/downloads/kovri-latest-osx-10.13.tar.bz2) | [macOS (x86-64)](https://build.getmonero.org/downloads/kovri-latest-osx-10.13.tar.bz2.sha256sum.txt) | [![macOS (x86-64)](https://build.getmonero.org/png?builder=kovri-static-osx)](https://build.getmonero.org/builders/kovri-static-osx) |
| [FreeBSD (x86-64)](https://build.getmonero.org/downloads/kovri-latest-freebsd-amd64.tar.bz2) | [FreeBSD (x86-64)](https://build.getmonero.org/downloads/kovri-latest-freebsd-amd64.tar.bz2.sha256sum.txt) | [![FreeBSD (x86-64)](https://build.getmonero.org/png?builder=kovri-static-freebsd64)](https://build.getmonero.org/builders/kovri-static-freebsd64) |
| [OpenBSD (x86-64)](https://build.getmonero.org/downloads/kovri-latest-openbsd-amd64.tar.bz2) | [OpenBSD (x86-64)](https://build.getmonero.org/downloads/kovri-latest-openbsd-amd64.tar.bz2.sha256sum.txt) | [![OpenBSD (x86-64)](https://build.getmonero.org/png?builder=kovri-static-openbsd-amd64)](https://build.getmonero.org/builders/kovri-static-openbsd-amd64) |
| [DragonFly BSD (x86-64)](https://build.getmonero.org/downloads/kovri-latest-dragonflybsd-4.6.tar.bz2) | [DragonFly BSD (x86-64)](https://build.getmonero.org/downloads/kovri-latest-dragonflybsd-4.6.tar.bz2.sha256sum.txt) | [![DragonFly BSD (x86-64)](https://build.getmonero.org/png?builder=kovri-static-dragonflybsd-amd64)](https://build.getmonero.org/builders/kovri-static-dragonflybsd-amd64) |
| [Windows (x86-64)](https://build.getmonero.org/downloads/kovri-latest-win64.exe) | [Windows (x86-64)](https://build.getmonero.org/downloads/kovri-latest-win64.exe.sha256sum.txt) | [![Windows (x86-64)](https://build.getmonero.org/png?builder=kovri-static-win64)](https://build.getmonero.org/builders/kovri-static-win64) |
| [Windows (i686)](https://build.getmonero.org/downloads/kovri-latest-win32.exe) | [Windows (i686)](https://build.getmonero.org/downloads/kovri-latest-win32.exe.sha256sum.txt) | [![Windows (i686)](https://build.getmonero.org/png?builder=kovri-static-win32)](https://build.getmonero.org/builders/kovri-static-win32) |

## Coverage

| Type      | Status |
|-----------|--------|
| Coverity  | [![Coverity Status](https://scan.coverity.com/projects/7621/badge.svg)](https://scan.coverity.com/projects/7621/)
| Coveralls | [![Coveralls Status](https://coveralls.io/repos/github/monero-project/kovri/badge.svg?branch=master)](https://coveralls.io/github/monero-project/kovri?branch=master)
| License   | [![License](https://img.shields.io/badge/license-BSD3-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

## Сборка

### Зависимости и окружение

| Зависимость         | Минимальная версия                 | По желанию | Arch Linux  | Ubuntu/Debian    | macOS (Homebrew) | FreeBSD       | OpenBSD     |
| ------------------- | ---------------------------------- |:----------:| ----------- | ---------------- | ---------------- | ------------- | ----------- |
| git                 | 1.9.1                              |            | git         | git              | git              | git           | git         |
| gcc                 | 4.9.2                              |            | gcc         | gcc              |                  |               |             |
| clang               | 3.5 (3.6 на FreeBSD)               |            | clang       | clang            | clang (Apple)    | clang36       | llvm        |
| CMake               | 3.5.1                              |            | cmake       | cmake            | cmake            | cmake         | cmake       |
| gmake (BSD)         | 4.2.1                              |            |             |                  |                  | gmake         | gmake       |
| Boost               | 1.58                               |            | boost       | libboost-all-dev | boost            | boost-libs    | boost       |
| OpenSSL             | Любая из последних стабильных версий |            | openssl     | libssl-dev       | openssl          | openssl       | openssl     |
| Doxygen             | 1.8.6                              |      X     | doxygen     | doxygen          | doxygen          | doxygen       | doxygen     |
| Graphviz            | 2.36                               |      X     | graphviz    | graphviz         | graphviz         | graphviz      | graphviz    |
| Docker              | Любая из последних стабильных версий |      X     | See website | See website      | See website      | See website   | See website |

#### Windows (MSYS2/MinGW-64)
* Скачайте [MSYS2 installer](http://msys2.github.io/), 64-bit или 32-bit по необходимости
* Используйте ярлык соотвествующий вашей архитектуре для запуска MSYS2 окружения. Для 64-битных систем это будет ярлык `MinGW-w64 Win64 Shell`. Примечание: если у вас 64-битная версия Windows, вам будут доступны 64-битное и 32-битное окружение.
* Обновите пакеты в установленном MSYS2:

```shell
$ pacman -Sy
$ pacman -Su --ignoregroup base
$ pacman -Syu
```

#### Установите пакеты

Примечание: Для сборок i686, замените `mingw-w64-x86_64` на `mingw-w64-i686`

`$ pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl`

Выборочно:

`$ pacman -S mingw-w64-x86_64-doxygen mingw-w64-x86_64-graphviz`

### Make and install

** *Не* используйте скачанный zip файл с github: используйте только рекурсивное клонирование **

```bash
$ git clone --recursive https://github.com/monero-project/kovri
$ cd kovri && make release  # see the Makefile for all build options
$ make install
```

- Конечные пользователи ДОЛЖНЫ выполнить `make install` для новых установок
- Разрабочтики ДОЛЖНЫ выполнить `make install` после свежей сборки

### Docker

Также можно собрать локально используя Docker

```bash
$ docker build -t kovri:latest .
```

## Документация и разработка
- [Руководство пользователя](https://github.com/monero-project/kovri-docs/blob/master/i18n/ru/user_guide.md) доступно всем пользователям
- [Руководство разработчика](https://github.com/monero-project/kovri-docs/blob/master/i18n/ru/developer_guide.md) доступно для разработчиков (пожалуйста, ознакомьтесь с документацией перед созданием нового pull request)
- Любую дополнительную документацию на вашем языке, вы можете найти в репозитории [kovri-docs](https://github.com/monero-project/kovri-docs/)
- [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html) рекомендуется всем пользователям и разработчикам
- [Система общественного финансирования](https://forum.getmonero.org/8/funding-required) для получения финансирования вашей работы, [внесите свое предложение](https://forum.getmonero.org/7/open-tasks/2379/forum-funding-system-ffs-sticky)
- [build.getmonero.org](https://build.getmonero.org/) или monero-build.i2p подробная информация о сборке
- [repo.getmonero.org](https://repo.getmonero.org/monero-project/kovri) или monero-repo.i2p альтернативные репозитории GitHub с non-push доступом
- Смотри также [kovri-site](https://github.com/monero-project/kovri-site) и [monero/kovri meta](https://github.com/monero-project/meta)

## Отчет об уязвимости
- Наш [Процесс реагирования на уязвимость](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) и стимулирует оперативный поиск уязвимостей
- Мы также есть на [HackerOne](https://hackerone.com/monero)

## Контакты и поддержка
- IRC: [Freenode](https://webchat.freenode.net/) | Irc2P с Kovri
  - `#kovri` | Сообщество & Канал поддержки
  - `#kovri-dev` | Канал разработки
- [Monero Mattermost](https://mattermost.getmonero.org/)
- [Monero Slack](https://monero.slack.com/) (предварительно, попросите приглашение в IRC)
- [Monero StackExchange](https://monero.stackexchange.com/)
- [Reddit /r/Kovri](https://www.reddit.com/r/Kovri/)
- Twitter: [@getkovri](https://twitter.com/getkovri)
- Email:
  - Общего назначения / Контактная информация для СМИ
    - dev [at] getmonero.org
  - Все остальные контакты
    - anonimal [at] getmonero.org
    - PGP Key fingerprint: 1218 6272 CD48 E253 9E2D  D29B 66A7 6ECF 9144 09F1

## Пожертвования
- Посетите нашу [Страницу Пожертвований](https://getmonero.org/getting-started/donate/) чтобы помочь Kovri своим пожертвованием
