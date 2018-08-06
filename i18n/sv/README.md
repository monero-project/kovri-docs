[<img width="300" src="https://static.getmonero.org/images/kovri/logo.png" alt="ˈKoʊvriː" />](https://github.com/monero-project/kovri)

1. [Att dölja, täcka, skyla](https://en.wikipedia.org/wiki/Esperanto)
2. En fri, decentraliserad, anonymitetsteknologi baserad på [I2P](https://getmonero.org/resources/moneropedia/i2p.html)s öppna specifikationer

## Ansvarsfriskrivning

- För närvarande **pre-alfa**-programvara; under intensiv utveckling (och ännu inte integrerad med monero)

## Snabbstart

- Vill du ha färdigbyggda binärer? [Ladda ner längre ner på sidan](#downloads)
- Vill du bygga och installera själv? [Bygginstruktioner nedan](#building)

## Flerspråkig README

Detta är en översättning av Kovris README-fil. Originalet (på engelska) finns tillgänglig på: https://github.com/monero-project/kovri/blob/master/README.md

## Nerladdningar

### Releaser

### [Nattliga byggen ("bleeding edge")](https://build.getmonero.org/waterfall)

| Nedladdning | Checksumma | Status |
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

## Kodtäckning

| Typ | Status |
| ----------- | -------- |
| Coverity | [![Coverity Status](https://scan.coverity.com/projects/7621/badge.svg)](https://scan.coverity.com/projects/7621/) |
| Coveralls | [![Coveralls Status](https://coveralls.io/repos/github/monero-project/kovri/badge.svg?branch=master)](https://coveralls.io/github/monero-project/kovri?branch=master) |
| License | [![License](https://img.shields.io/badge/license-BSD3-blue.svg)](https://opensource.org/licenses/BSD-3-Clause) |

## Att bygga projektet

### Beroenden och miljö

| Beroende | Lägsta version | Valfri | Arch Linux | Ubuntu/Debian | macOS (Homebrew) | FreeBSD | OpenBSD |
| ------------------- | ---------------------------- | :--------: | ----------- | ---------------- | ---------------- | ------------- | ----------- |
| git | 1.9.1 |  | git | git | git | git | git |
| gcc | 4.9.2 |  | gcc | gcc |  |  |  |
| clang | 3.5 (3.6 för FreeBSD) |  | clang | clang | clang (Apple) | clang36 | llvm |
| CMake | 3.5.1 |  | cmake | cmake | cmake | cmake | cmake |
| gmake (BSD) | 4.2.1 |  |  |  |  | gmake | gmake |
| Boost | 1.58 |  | boost | libboost-all-dev | boost | boost-libs | boost |
| OpenSSL | Alltid senaste stabil version |  | openssl | libssl-dev | openssl | openssl | openssl |
| Doxygen | 1.8.6 | X | doxygen | doxygen | doxygen | doxygen | doxygen |
| Graphviz | 2.36 | X | graphviz | graphviz | graphviz | graphviz | graphviz |
| Docker | Alltid senaste stabil version | X | Se webbplatsen | Se webbplatsen | Se webbplatsen | Se webbplatsen | Se webbplatsen |

#### Windows (MSYS2/MinGW-64)

* Ladda ned [MSYS2-installeraren](http://msys2.github.io/), 64-bitars eller 32-bitars efter behov
* Använd genvägen som är kopplad till din arkitektur för att starta MSYS2-miljön. För 64-bitars system innebär det genvägen `MinGW-w64 Win64 Shell`. OBS: om du kör 64-bitars Windows har du både 64-bitars och 32-bitars miljöer
* Uppdatera paketen i din MSYS2-installation:

```shell
$ pacman -Sy
$ pacman -Su --ignoregroup base
$ pacman -Syu
```

#### Installera paket

OBS: För att bygga på i686 ska du byta ut `mingw-w64-x86_64` med `mingw-w64-i686`

`$ pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl`

Valfritt:

`$ pacman -S mingw-w64-x86_64-doxygen mingw-w64-x86_64-graphviz`

### Make och install

**Använd *inte* zip-filen från github: gör endast en rekursiv kloning**

```bash
$ git clone --recursive https://github.com/monero-project/kovri
$ cd kovri && make release # se Makefile för alla byggalternativ
$ make install
```

- Slutanvändare MÅSTE köra `make install` för nya installationer
- Utvecklare BÖR köra `make install` efter ett nytt bygge

### Docker

Eller bygg lokalt med Docker

```bash
$ docker build -t kovri:latest .
```

## Dokumentation och Utveckling

- En [Användarhandledning](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/user_guide.md) finns tillgänglig för alla användare
- En [Utvecklarhandledning](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/developer_guide.md) finns tillgänglig för utveckling (läs den innan du öppnar ett 'pull request')
- Ytterligare dokumentation hittar du på ditt favoritspråk i kodförrådet [kovri-docs](https://github.com/monero-project/kovri-docs/)
- [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html) rekommenderas för alla användare och utvecklare
- [Forum Funding System](https://forum.getmonero.org/8/funding-required) för att få ersättning för ditt arbete, [skicka in ett förslag](https://forum.getmonero.org/7/open-tasks/2379/forum-funding-system-ffs-sticky)
- [build.getmonero.org](https://build.getmonero.org/) eller monero-build.i2p för detaljerad information om byggen
- [repo.getmonero.org](https://repo.getmonero.org/monero-project/kovri) eller monero-repo.i2p är alternativ till GitHub för icke-push åtkomst till kodförråd
- Se också [kovri-site](https://github.com/monero-project/kovri-site) och [monero/kovri meta](https://github.com/monero-project/meta)

## Sårbarhetshantering

- Vår [Process för sårbarhetshantering](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) uppmuntrar till ansvarsfull sårbarhetsredovisning
- Vi finns också tillgängliga via [HackerOne](https://hackerone.com/monero)

## Kontakt och support

- IRC: [Freenode](https://webchat.freenode.net/) | Irc2P med Kovri
   - `#kovri` | Community & Supportkanal
   - `#kovri-dev` | Utvecklingskanal
- [Monero Mattermost](https://mattermost.getmonero.org/)
- [Monero Slack](https://monero.slack.com/) (be om inbjudan på IRC)
- [Monero StackExchange](https://monero.stackexchange.com/)
- [Reddit /r/Kovri](https://www.reddit.com/r/Kovri/)
- Twitter: [@getkovri](https://twitter.com/getkovri)
- E-post:
   - Allmänna frågor / Mediakontakt
      - dev [at] getmonero.org
   - All annan kontakt
      - anonimal [at] getmonero.org
      - PGP-fingeravtryck: 1218 6272 CD48 E253 9E2D  D29B 66A7 6ECF 9144 09F1

## Donationer

- Besök vår [Donationssida](https://getmonero.org/getting-started/donate/) för att hjälpa Kovri med dina donationer
