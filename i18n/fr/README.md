[<img width="300" src="https://static.getmonero.org/images/kovri/logo.png" alt="ˈKoʊvriː" />](https://github.com/monero-project/kovri)

1. [Couvrir, voiler, envelopper](https://fr.wikipedia.org/wiki/Esperanto)
2. Une technologie d'anonymisation gratuire et décentralisée basée sur les spécifications ouvertes d'[I2P](https://getmonero.org/resources/moneropedia/i2p.html)

## Disclaimer
- Actuellement en **pré-alpha**; en cours de développement intensif (et pas encore intégré à monero)

## Quickstart

- Vous voulez les binaires précompilés ? [Télécharger ci-dessous](#telechargements)
- Vous voulez compiler et installer vous-même ? [Instruction de compilation](#compilation)

## Multilingual README
Ceci est une version traduite du README Kovri, la version originale (en anglais) est disponible ici : https://github.com/monero-project/kovri/blob/master/README.md

## Téléchargements

### Versions

### [Version Nocturnes (bleeding edge)](https://build.getmonero.org/waterfall)

| Téléchargement | Checksum | Etat |
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

## Couverture

| Type      | Etat |
|-----------|--------|
| Coverity  | [![Coverity Status](https://scan.coverity.com/projects/7621/badge.svg)](https://scan.coverity.com/projects/7621/)
| Coveralls | [![Coveralls Status](https://coveralls.io/repos/github/monero-project/kovri/badge.svg?branch=master)](https://coveralls.io/github/monero-project/kovri?branch=master)
| License   | [![License](https://img.shields.io/badge/license-BSD3-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

## Compilation

### Dépendances et environnements

| Dépendances         | Version minimale                    | Optionnelle | Arch Linux       | Ubuntu/Debian    | macOS (Homebrew) | FreeBSD          | OpenBSD          |
| ------------------- | ----------------------------------- |:-----------:| ---------------- | ---------------- | ---------------- | ---------------- | ---------------- |
| git                 | 1.9.1                               |             | git              | git              | git              | git              | git              |
| gcc                 | 4.9.2                               |             | gcc              | gcc              |                  |                  |                  |
| clang               | 3.5 (3.6 on FreeBSD)                |             | clang            | clang            | clang (Apple)    | clang36          | llvm             |
| CMake               | 3.5.1                               |             | cmake            | cmake            | cmake            | cmake            | cmake            |
| gmake (BSD)         | 4.2.1                               |             |                  |                  |                  | gmake            | gmake            |
| Boost               | 1.58                                |             | boost            | libboost-all-dev | boost            | boost-libs       | boost            |
| OpenSSL             | Toujours la dernière version stable |             | openssl          | libssl-dev       | openssl          | openssl          | openssl          |
| Doxygen             | 1.8.6                               |      X      | doxygen          | doxygen          | doxygen          | doxygen          | doxygen          |
| Graphviz            | 2.36                                |      X      | graphviz         | graphviz         | graphviz         | graphviz         | graphviz         |
| Docker              | Toujours la dernière version stable |      X      | voir le site web | voir le site web | voir le site web | voir le site web | voir le site web |

#### Windows (MSYS2/MinGW-64)
* Téléchargez l'[installateur MSYS2](http://msys2.github.io/), 64-bit ou 32-bit selon votre besoin
* Utilisez le raccourci associé à votre architecture pour lancer l'environnement MSYS2. Sur un système 64 bits il s'agira du raccourci `MinGW-w64 Win64 Shell`. Remarque: si vous avez un Windows 64 bits, vous disposerez des deux environnements 32 et 64 bits
* Mettez à jour les packages dans votre installation MSYS2 :

```shell
$ pacman -Sy
$ pacman -Su --ignoregroup base
$ pacman -Syu
```

#### Installer les packages

Remarque : Pour les compilations i686, remplacez `mingw-w64-x86_64` par `mingw-w64-i686`

`$ pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl`

Optionnellement :

`$ pacman -S mingw-w64-x86_64-doxygen mingw-w64-x86_64-graphviz`

### Make et install

***Ne pas* utiliser le fichier zip de github : faites uniquement un clone récursif**

```bash
$ git clone --recursive https://github.com/monero-project/kovri
$ cd kovri && make release  # Voir le Makefile pour toutes les options de compilation
$ make install
```

- Les utilisateurs DOIVENT lancer `make install` pour les nouvelles installations
- Les développeurs DEVRAIENT lancer `make install` après compilation

### Docker

Ou compilez localement avec Docker

```bash
$ docker build -t kovri:latest .
```

## Documentation et Développement
- Un [Guide Utilisateur](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/user_guide.md) est disponible pour tous les utilisateurs
- Un [Guide de développement](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/developer_guide.md) est disponible pour les développeurs (veuillez le consulter avant d'ouvrir une *pull request*)
- Vous trouverez plus de documentation dans la langue de votre choix dans le dépôt [kovri-docs](https://github.com/monero-project/kovri-docs/)
- [Moneropedia](https://getmonero.org/fr/resources/moneropedia/kovri.html) est recommandé pour tous les utilisateurs et développeurs
- Le [Forum Funding System](https://forum.getmonero.org/8/funding-required) permet d'obtenir des fonds pour financer vos travaux, [soumettez une proposition](https://forum.getmonero.org/7/open-tasks/2379/forum-funding-system-ffs-sticky)
- [build.getmonero.org](https://build.getmonero.org/) ou monero-build.i2p pour des informations de compilation détaillées
- [repo.getmonero.org](https://repo.getmonero.org/monero-project/kovri) ou monero-repo.i2p sont des alternatives à GitHub pour l'accès au dépot en lecture
- Voir également [kovri-site](https://github.com/monero-project/kovri-site) et [monero/kovri meta](https://github.com/monero-project/meta)

## Réponse aux Vulnérabilités
- Notre [Processus de Réponse aux Vulnérabilités](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) encourage les divulgations responsables
- Nous sommes également disponible à travers [HackerOne](https://hackerone.com/monero)

## Contact et Support
- IRC: [Freenode](https://webchat.freenode.net/) | Irc2P avec Kovri
  - `#kovri` | Canal de Communauté et de Support
  - `#kovri-dev` | Canal de Développement
- [Mattermost Monero](https://mattermost.getmonero.org/)
- [Slack Monero](https://monero.slack.com/) (ask for an invite on IRC)
- [StackExchange Monero](https://monero.stackexchange.com/)
- [Reddit /r/Kovri](https://www.reddit.com/r/Kovri/)
- Twitter: [@getkovri](https://twitter.com/getkovri)
- Email:
  - Besoins généraux / Contact Média
    - dev [at] getmonero.org
  - Tout autre contact
    - anonimal [at] getmonero.org
    - PGP Key fingerprint: 1218 6272 CD48 E253 9E2D  D29B 66A7 6ECF 9144 09F1

## Donations
- Consultez notre [Page de dons](https://getmonero.org/getting-started/donate/) pour aider Kovri avec vos dons
