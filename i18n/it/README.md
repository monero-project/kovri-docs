[<img width="300" src="https://static.getmonero.org/images/kovri/logo.png" alt="ˈKoʊvriː" />](https://github.com/monero-project/kovri)

## Kovri
1. [Coprire, velare, avvolgere](https://it.wikipedia.org/wiki/Esperanto)
2. Una libera, decentralizzata, tecnologia di anonimizzazione basata sulle specifiche aperte di [I2P](https://getmonero.org/it/resources/moneropedia/i2p.html)

## Disclaimer
- Correntemente in **Alpha**; in intensivo sviluppo (e non ancora integrato con monero)

## Quickstart

- Vuoi i file binari pre-compilati? [Download sotto](#downloads)
- Vuoi compilare e installare da solo/a? [Istruzioni per la compilazione](#compilazione)

## Multilingual README
Questa è la versione tradotta del README di Kovri, l'originale (in inglese) è disponibile al seguente link: https://github.com/monero-project/kovri/blob/master/README.md

## Downloads

### Pubblicazioni

### [Pubblicazioni 'notturne' (bleeding edge)](https://build.getmonero.org/waterfall)

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

## Copertura

| Type      | Status |
|-----------|--------|
| Coverity  | [![Coverity Status](https://scan.coverity.com/projects/7621/badge.svg)](https://scan.coverity.com/projects/7621/)
| Coveralls | [![Coveralls Status](https://coveralls.io/repos/github/monero-project/kovri/badge.svg?branch=master)](https://coveralls.io/github/monero-project/kovri?branch=master)
| License   | [![License](https://img.shields.io/badge/license-BSD3-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

## Compilazione

### Dipendenze e ambiente di compilazione

| Dependency          | Minimum version              | Optional | Arch Linux  | Ubuntu/Debian    | macOS (Homebrew) | FreeBSD       | OpenBSD     |
| ------------------- | ---------------------------- |:--------:| ----------- | ---------------- | ---------------- | ------------- | ----------- |
| git                 | 1.9.1                        |          | git         | git              | git              | git           | git         |
| gcc                 | 4.9.2                        |          | gcc         | gcc              |                  |               |             |
| clang               | 3.5 (3.6 su FreeBSD)         |          | clang       | clang            | clang (Apple)    | clang36       | llvm        |
| CMake               | 3.5.1                        |          | cmake       | cmake            | cmake            | cmake         | cmake       |
| gmake (BSD)         | 4.2.1                        |          |             |                  |                  | gmake         | gmake       |
| Boost               | 1.58                         |          | boost       | libboost-all-dev | boost            | boost-libs    | boost       |
| OpenSSL             | Sempre ultima versione stabile |          | openssl     | libssl-dev       | openssl          | openssl       | openssl     |
| Doxygen             | 1.8.6                        |    X     | doxygen     | doxygen          | doxygen          | doxygen       | doxygen     |
| Graphviz            | 2.36                         |    X     | graphviz    | graphviz         | graphviz         | graphviz      | graphviz    |
| Docker              | Sempre ultima versione stabile |    X     | Vedi sito | Vedi sito      | Vedi sito      | Vedi sito   | Vedi sito |

#### Windows (MSYS2/MinGW-64)
* Scarica l'[installer MSYS2](http://msys2.github.io/),64-bit o 32-bit all'occorrenza
* Usa gli shortcut associati alla tua architettura per avviare l'ambiente di compilazione di MSYS2. Su sistemi 64-bit sarebbe `MinGW-w64 Win64 Shell`. Nota: se stai usando Windows 64-bit, avrai entrambi gli ambienti, 64-bit e 32-bit
* Aggiorna i pacchetti della versione di MSYS2 installata:

```shell
$ pacman -Sy
$ pacman -Su --ignoregroup base
$ pacman -Syu
```

#### Installa pacchetti

Nota: Per compilazioni i686, rimpiazza `mingw-w64-x86_64` con `mingw-w64-i686`

`$ pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl`

Opzionale:

`$ pacman -S mingw-w64-x86_64-doxygen mingw-w64-x86_64-graphviz`

### Make e installa

***Non* utilizzare il file zip su github: clona esclusivamente recursivamente**

```bash
$ git clone --recursive https://github.com/monero-project/kovri
$ cd kovri && make release  # leggi il Makefile per tutte le opzioni di compilazione
$ make install
```

- Gli utenti finali DEVONO usare `make install` per nuove installazioni
- Gli sviluppatori DOVREBBERO usare `make install` dopo una nuova compilazione

### Docker

O compila localmente con Docker

```bash
$ docker build -t kovri:latest .
```

## Documentazione e sviluppo
- [Guida per utenti](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/user_guide.md) è disponibile per gli utenti
- [Guida per sviluppatori](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/developer_guide.md) è disponibile per gli sviluppatori (per favore leggi prima di aprire una pull request)
- Ulteriore documentazione nella tua lingua (italiano) può essere trovata nella sezione apposita della repository [kovri-docs](https://github.com/monero-project/kovri-docs/tree/master/i18n/it)
- [Moneropedia](https://getmonero.org/it/resources/moneropedia/kovri.html) è raccomandata per tutti gli utenti e sviluppatori
- [Forum Funding System](https://forum.getmonero.org/8/funding-required) per essere finanziato/a per il tuo lavoro, [invia una proposta](https://forum.getmonero.org/7/open-tasks/2379/forum-funding-system-ffs-sticky)
- [build.getmonero.org](https://build.getmonero.org/) o monero-build.i2p per istruzioni dettagliate sulla compilazione
- [repo.getmonero.org](https://repo.getmonero.org/monero-project/kovri) o monero-repo.i2p sono alternative a GitHub per repository senza accesso 'push'
- Vedi anche [kovri-site](https://github.com/monero-project/kovri-site) e [monero/kovri meta](https://github.com/monero-project/meta)

## Gestione vulnerabilità
- Il nostro [sistema di gestione delle vulnerabilità](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) incoraggia una pubblicazione responsabile
- Siamo anche disponibili su [HackerOne](https://hackerone.com/monero)

## Contatti e supporto
- IRC: [Freenode](https://webchat.freenode.net/) | Irc2P con Kovri
  - `#kovri` | Community & canale di supporto
  - `#kovri-dev` | canale per sviluppatori
- [Monero Mattermost](https://mattermost.getmonero.org/)
- [Monero Slack](https://monero.slack.com/) (ask for an invite on IRC)
- [Monero StackExchange](https://monero.stackexchange.com/)
- [Reddit /r/Kovri](https://www.reddit.com/r/Kovri/)
- Twitter: [@getkovri](https://twitter.com/getkovri)
- Email:
  - Scopi generali / Contatti per media
    - dev [at] getmonero.org
  - Tutti gli altri contatti
    - anonimal [at] getmonero.org
    - PGP Key fingerprint: 1218 6272 CD48 E253 9E2D  D29B 66A7 6ECF 9144 09F1

## Donazioni
- Visita la nostra [pagina per le donazioni](https://getmonero.org/getting-started/donate/) per aiutare Kovri effettuando delle donazioni
