[<img width="300" src="https://static.getmonero.org/images/kovri/logo.png" alt="ˈKoʊvriː" />](https://github.com/monero-project/kovri)

1. [To cover, veil, wrap](https://en.wikipedia.org/wiki/Esperanto)
2. En gratis, decentral, anonymitetsteknologi baseret på [I2P](https://getmonero.org/resources/moneropedia/i2p.html)'s åbne specifikationer

## Dementi
- På nuværende tidspunkt **Alfa** software; under heftig udvikling (og endnu ikke integreret med Monero)

## Hurtig start

- Vil du have prebuilded binære filer? [Download nedenfor](#downloads)
- Vil du selv builde og installere? [byggeinstruktioner nedenfor](#building)

## Multilingual README
Dette er en oversat version af Kovri README, den originale version (på engelsk) er tilgængelig på: https://github.com/monero-project/kovri/blob/master/README.md

## Downloads

### Udgivelser

### [Nightly Udgivelser (bleeding edge)](https://build.getmonero.org/waterfall)

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

## Dækning

| Type      | Status |
|-----------|--------|
| Coverity  | [![Coverity Status](https://scan.coverity.com/projects/7621/badge.svg)](https://scan.coverity.com/projects/7621/)
| Coveralls | [![Coveralls Status](https://coveralls.io/repos/github/monero-project/kovri/badge.svg?branch=master)](https://coveralls.io/github/monero-project/kovri?branch=master)
| License   | [![License](https://img.shields.io/badge/license-BSD3-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

## Building

### Dependencies and environment

| Dependency          | Minimum version              | Optional | Arch Linux  | Ubuntu/Debian    | macOS (Homebrew) | FreeBSD       | OpenBSD     |
| ------------------- | ---------------------------- |:--------:| ----------- | ---------------- | ---------------- | ------------- | ----------- |
| git                 | 1.9.1                        |          | git         | git              | git              | git           | git         |
| gcc                 | 4.9.2                        |          | gcc         | gcc              |                  |               |             |
| clang               | 3.5 (3.6 on FreeBSD)         |          | clang       | clang            | clang (Apple)    | clang36       | llvm        |
| CMake               | 3.5.1                        |          | cmake       | cmake            | cmake            | cmake         | cmake       |
| gmake (BSD)         | 4.2.1                        |          |             |                  |                  | gmake         | gmake       |
| Boost               | 1.58                         |          | boost       | libboost-all-dev | boost            | boost-libs    | boost       |
| OpenSSL             | Always latest stable version |          | openssl     | libssl-dev       | openssl          | openssl       | openssl     |
| Doxygen             | 1.8.6                        |    X     | doxygen     | doxygen          | doxygen          | doxygen       | doxygen     |
| Graphviz            | 2.36                         |    X     | graphviz    | graphviz         | graphviz         | graphviz      | graphviz    |
| Docker              | Always latest stable version |    X     | See website | See website      | See website      | See website   | See website |

#### Windows (MSYS2/MinGW-64)
* Download [MSYS2 installer](http://msys2.github.io/), 64-bit or 32-bit efter behov
* Brug genvejen forbundet med din arkitektur til at igangsætte MSYS2 environment. På 64-bit systemer er det `MinGW-w64 Win64 Shell` genvejen. Bemærk: hvis du kører Windows 64-bit, Vil du både have 64-bit og 32-bit environments. 
* Opdater packages i MSYS2 installationen:

```shell
$ pacman -Sy
$ pacman -Su --ignoregroup base
$ pacman -Syu
```

#### Installér packages

Bemærk: For i686 builds, erstat `mingw-w64-x86_64` med `mingw-w64-i686`

`$ pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl`

Valgfri:

`$ pacman -S mingw-w64-x86_64-doxygen mingw-w64-x86_64-graphviz`

### Lav og installér

**Brug ikke zip-filen fra github: lav kun en rekursiv klon**

```bash
$ git clone --recursive https://github.com/monero-project/kovri
$ cd kovri && make release  # see the Makefile for all build options
$ make install
```

- End-users SKAL køre `make install` for nye installationer
- Udviklere BØR køre `make install` efter en frisk build

### Docker

Eller build lokalt med Docker

```bash
$ docker build -t kovri:latest .
```

## Dokumentation og Udvikling
- En [Brugerguide](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/user_guide.md) er tilgængelig for alle brugere
- En [Udviklerguide](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/developer_guide.md) er tilgængelig for alle udviklere (læse venligst før du åbner en pull request)
- Yderligere dokumentation kan findes på dit valgte sprog i [kovri-docs](https://github.com/monero-project/kovri-docs/) repositoriet
- [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html) anbefales for alle brugere og udviklere
- [Forum Funding System](https://forum.getmonero.org/8/funding-required) for at få økonomisk kompensation for dit arbejde [indsend et forslag](https://forum.getmonero.org/7/open-tasks/2379/forum-funding-system-ffs-sticky)
- [build.getmonero.org](https://build.getmonero.org/) or monero-build.i2p for detaljeret build information
- [repo.getmonero.org](https://repo.getmonero.org/monero-project/kovri) eller monero-repo.i2p er alternativer til  GitHub for non-push repository adgang
- Se også [kovri-site](https://github.com/monero-project/kovri-site) og [monero/kovri meta](https://github.com/monero-project/meta)

## Sårbarhedsrespons
- Vores [Sårbarhedsrespons Process](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) opfordrer til ansvarlig offentliggørelse
- Vi er også tilgængelige via [HackerOne](https://hackerone.com/monero)

## Kontakt og Support
- IRC: [Freenode](https://webchat.freenode.net/) | Irc2P with Kovri
  - `#kovri` | Community & Support Channel
  - `#kovri-dev` | Development Channel
- [Monero Mattermost](https://mattermost.getmonero.org/)
- [Monero Slack](https://monero.slack.com/) (spørg for invitation på IRC)
- [Monero StackExchange](https://monero.stackexchange.com/)
- [Reddit /r/Kovri](https://www.reddit.com/r/Kovri/)
- Twitter: [@getkovri](https://twitter.com/getkovri)
- Email:
  - Generelle Øjemed / Mediekontact
    - dev [at] getmonero.org
  - Al anden kontakt
    - anonimal [at] getmonero.org
    - PGP Key fingerprint: 1218 6272 CD48 E253 9E2D  D29B 66A7 6ECF 9144 09F1

## Donationer
- Besøg vores [Donationsside](https://getmonero.org/getting-started/donate/) for at hjælpe Kovri med donationer
