[<img width="300" src="https://static.getmonero.org/images/kovri/logo.png" alt="ˈKoʊvriː" />](https://github.com/monero-project/kovri)

1. [Verdecken, verschleiern, einhüllen](https://de.wikipedia.org/wiki/Esperanto)
2. Eine freie, dezentrale Anonymitätstechnologie, die auf [I2P](https://getmonero.org/resources/moneropedia/i2p.html)s offenen Spezifikationen beruht

## Disclaimer
- Derzeit **Alpha**-Software; unter starker Entwicklung (und noch nicht in Monero integriert)

## Schnellstart

- Du möchtest fertige Binaries? [Lade sie unten herunter](#downloads)
- Du möchtest selbst kompilieren und installieren? [Siehe die Kompilieranleitung weiter unten](#kompilierung)

## Mehrsprachige README
Dies ist eine Übersetzung der Kovri-Readme-Datei, das (englischsprachige) Original ist hier verfügbar: https://github.com/monero-project/kovri/blob/master/README.md

## Downloads

### Versionen

### [Nightly Releases (bleeding edge)](https://build.getmonero.org/waterfall)

| Installer | Prüfsumme | Status |
| --------- | --------- | ------ |
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

## Abdeckung

| Typ      | Status |
|-----------|--------|
| Coverity  | [![Coverity Status](https://scan.coverity.com/projects/7621/badge.svg)](https://scan.coverity.com/projects/7621/)
| Coveralls | [![Coveralls Status](https://coveralls.io/repos/github/monero-project/kovri/badge.svg?branch=master)](https://coveralls.io/github/monero-project/kovri?branch=master)
| License   | [![License](https://img.shields.io/badge/license-BSD3-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

## Kompilierung

### Abhängigkeiten und Umgebung

| Abhängigkeit          | Mindestversion              | Optional | Arch Linux  | Ubuntu/Debian    | macOS (Homebrew) | FreeBSD       | OpenBSD     |
| ------------------- | ---------------------------- |:--------:| ----------- | ---------------- | ---------------- | ------------- | ----------- |
| git                 | 1.9.1                        |          | git         | git              | git              | git           | git         |
| gcc                 | 4.9.2                        |          | gcc         | gcc              |                  |               |             |
| clang               | 3.5 (3.6 auf FreeBSD)         |          | clang       | clang            | clang (Apple)    | clang36       | llvm        |
| CMake               | 3.5.1                        |          | cmake       | cmake            | cmake            | cmake         | cmake       |
| gmake (BSD)         | 4.2.1                        |          |             |                  |                  | gmake         | gmake       |
| Boost               | 1.58                         |          | boost       | libboost-all-dev | boost            | boost-libs    | boost       |
| OpenSSL             | Immer die neueste stabile Version |          | openssl     | libssl-dev       | openssl          | openssl       | openssl     |
| Doxygen             | 1.8.6                        |    X     | doxygen     | doxygen          | doxygen          | doxygen       | doxygen     |
| Graphviz            | 2.36                         |    X     | graphviz    | graphviz         | graphviz         | graphviz      | graphviz    |
| Docker              | Immer die neueste stabile Version |    X     | Siehe Website | Siehe Website | Siehe Website      | Siehe Website   | Siehe Website |

#### Windows (MSYS2/MinGW-64)
* Den [MSYS2-Installer](http://msys2.github.io/) herunterladen, je nach Bedarf 64-bit oder 32-bit
* Die deiner Architektur zugeordnete Verknüpfung verwenden, um die MSYS2-Umgebung zu starten. Auf 64-Bit-Systemen wäre das die Verknüpfung `MinGW-w64 Win64 Shell`. Info: falls du 64-Bit-Windows nutzt, hast du sowohl die 64-Bit- als auch die 32-Bit-Umgebung
* Die Pakete in deiner MSYS2-Installation aktualisieren:

```shell
$ pacman -Sy
$ pacman -Su --ignoregroup base
$ pacman -Syu
```

#### Pakete installieren

Info: Bei i686-Builds `mingw-w64-x86_64` durch `mingw-w64-i686` ersetzen

`$ pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl`

Optional:

`$ pacman -S mingw-w64-x86_64-doxygen mingw-w64-x86_64-graphviz`

### Make und install

***Nicht* die Zip-Datei von GitHub verwenden: bitte nur rekursiv klonen**

```bash
$ git clone --recursive https://github.com/monero-project/kovri
$ cd kovri && make release  # siehe Makefile für alle Kompilierungsoptionen
$ make install
```

- Endnutzer MÜSSEN `make install` für neue Installationen ausführen
- Entwickler SOLLTEN `make install` nach einer neuen Kompilierung ausführen

### Docker

Oder lokal mit Docker kompilieren

```bash
$ docker build -t kovri:latest .
```

## Dokumentation und Entwicklung
- Ein [Benutzerhandbuch](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/user_guide.md) steht allen Nutzern zur Verfügung
- Ein [Entwicklerhandbuch](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/developer_guide.md) steht allen Entwicklern zur Verfügung (bitte vor dem Öffnen eines Pull-Requests lesen)
- Weitere Dokumentationen in der Sprache deiner Wahl sind im [kovri-docs](https://github.com/monero-project/kovri-docs/)-Repository zu finden
- [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html) wird allen Nutzern und Entwicklern empfohlen
- [Forum Funding System](https://forum.getmonero.org/8/funding-required) zur Finanzierung deiner Arbeit, [reiche einen Antrag ein](https://forum.getmonero.org/7/open-tasks/2379/forum-funding-system-ffs-sticky)
- [build.getmonero.org](https://build.getmonero.org/) oder monero-build.i2p für detaillierte Informationen zur Kompilierung
- [repo.getmonero.org](https://repo.getmonero.org/monero-project/kovri) oder monero-repo.i2p sind Alternativen zu GitHub für einen Zugang zum Repository ohne Push-Möglichkeit
- Siehe auch [kovri-site](https://github.com/monero-project/kovri-site) und [monero/kovri meta](https://github.com/monero-project/meta)

## Vulnerability Response
- Unser [Vulnerability Response Process](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) ermutigt zur verantwortungsvollen Offenlegung
- Wir sind auch via [HackerOne](https://hackerone.com/monero) erreichbar

## Kontakt und Support
- IRC: [Freenode](https://webchat.freenode.net/) | Irc2P mit Kovri
  - `#kovri` | Community- & Support-Channel
  - `#kovri-dev` | Development-Channel
- [Monero Mattermost](https://mattermost.getmonero.org/)
- [Monero Slack](https://monero.slack.com/) (über IRC nach einer Einladung fragen)
- [Monero StackExchange](https://monero.stackexchange.com/)
- [Reddit /r/Kovri](https://www.reddit.com/r/Kovri/)
- Twitter: [@getkovri](https://twitter.com/getkovri)
- E-Mail:
  - Allgemeines / Medienkontakt
    - dev [at] getmonero.org
  - Alle anderen Kontakte
    - anonimal [at] getmonero.org
    - Fingerabdruck des PGP-Schlüssels: 1218 6272 CD48 E253 9E2D  D29B 66A7 6ECF 9144 09F1

## Spenden
- Besuche unsere [Spendenseite](https://getmonero.org/getting-started/donate/), um Kovri mit deiner Spende zu helfen
