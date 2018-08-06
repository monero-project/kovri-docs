[<img width="300" src="https://static.getmonero.org/images/kovri/logo.png" alt="ˈKoʊvriː" />](https://github.com/monero-project/kovri)

1. [Cubrir, Tapar, Envolver](https://en.wikipedia.org/wiki/Esperanto)
2. Una tecnología  libre, descentralizada y anónima basada en especificaciones de  [I2P](https://getmonero.org/resources/moneropedia/i2p.html)

## Exclusión de garantías y limitación de responsabilidad
- Software actualmente en **pre-alfa**; bajo desarrollo extensivo (y aun no integrado con Monero)

## Guía Rápida

- Quieres binarios pre-compilados? [Descarga abajo](#Descargas)
- Quieres compilar e instalar tú mismo? [Instrucciones de compilado abajo](#Compilando)

## Léeme multi-lenguaje
Esta es una versión del archivo Léeme de Kovri, traducido al español, el original en Ingles está disponible en: https://github.com/monero-project/kovri/blob/master/README.md

## Descargas

### Lanzamientos

### [Lanzamientos Nocturnos (la más reciente)](https://build.getmonero.org/waterfall)

| Descarga | Checksum | Estado |
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

| Tipo      | Estado |
|-----------|--------|
| Coverity  | [![Estado de Coverity](https://scan.coverity.com/projects/7621/badge.svg)](https://scan.coverity.com/projects/7621/)
| Coveralls | [![Estado de Coveralls](https://coveralls.io/repos/github/monero-project/kovri/badge.svg?branch=master)](https://coveralls.io/github/monero-project/kovri?branch=master)
| Licencia   | [![Licencia](https://img.shields.io/badge/license-BSD3-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

## Compilando

### Dependencias y entorno

| Dependencia          | Versiones mínimas           | Opcional | Arch Linux  | Ubuntu/Debian    | macOS (Homebrew) | FreeBSD       | OpenBSD     |
| ------------------- | ---------------------------- |:--------:| ----------- | ---------------- | ---------------- | ------------- | ----------- |
| git                 | 1.9.1                        |          | git         | git              | git              | git           | git         |
| gcc                 | 4.9.2                        |          | gcc         | gcc              |                  |               |             |
| clang               | 3.5 (3.6 en FreeBSD)         |          | clang       | clang            | clang (Apple)    | clang36       | llvm        |
| CMake               | 3.5.1                        |          | cmake       | cmake            | cmake            | cmake         | cmake       |
| gmake (BSD)         | 4.2.1                        |          |             |                  |                  | gmake         | gmake       |
| Boost               | 1.58                         |          | boost       | libboost-all-dev | boost            | boost-libs    | boost       |
| OpenSSL             | Siempre la última versión estable |          | openssl     | libssl-dev       | openssl          | openssl       | openssl     |
| Doxygen             | 1.8.6                        |    X     | doxygen     | doxygen          | doxygen          | doxygen       | doxygen     |
| Graphviz            | 2.36                         |    X     | graphviz    | graphviz         | graphviz         | graphviz      | graphviz    |
| Docker              | Siempre la última versión estable |    X     | Ver sitio web | Ver sitio web      | Ver sitio web      | Ver sitio web   | Ver sitio web |

#### Windows (MSYS2/MinGW-64)
* Descarga el instalador de [MSYS2](http://msys2.github.io/), 64-bit o 32-bit
* Usa el acceso directo asociado con tu arquitectura, para abrir el entorno MSYS2. En sistemas 64-bit  seria `MinGW-w64 Win64 Shell`. Nota: si estas en 64-bit Windows, vas a necesitar ambos entornos 64-bit y 32-bit
* Actualiza los paquetes en tu instalación de MSYS2:

```shell
$ pacman -Sy
$ pacman -Su --ignoregroup base
$ pacman -Syu
```

#### Instala los paquetes

Nota: Para instalaciones i686, reemplaza `mingw-w64-x86_64` con `mingw-w64-i686`

`$ pacman -S make mingw-w64-x86_64-cmake mingw-w64-x86_64-gcc mingw-w64-x86_64-boost mingw-w64-x86_64-openssl`

Opcional:

`$ pacman -S mingw-w64-x86_64-doxygen mingw-w64-x86_64-graphviz`

### Make e install

***No* uses el archivo zip de github: haz un clonado recursivo**

```bash
$ git clone --recursive https://github.com/monero-project/kovri
$ cd kovri && make release # lee el archivo Makefile para más opciones
$ make install
```

- Usuarios finales DEBEN correr el comando `make install` para instalaciones nuevas
- Desarrolladores DEBERÍAN correr `make install` después de cada compilado

### Docker

O compila localmente con Docker

```bash
$ docker build -t kovri:latest .
```

## Documentación y desarrollo
- Una [Guía de usuario](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/user_guide.md) esta disponible para todos los usuarios
- Una [Guía de desarrolladores](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/developer_guide.md) esta disponible para los desarrolladores (por favor, leer antes de abrir un nuevo pull request)
- Hay más documentación en tu idioma en el repositorio de [kovri-docs](https://github.com/monero-project/kovri-docs/)
- [Moneropedia](https://getmonero.org/es/resources/moneropedia/kovri.html) es recomendado para todos los usuarios y desarrolladores
- [Forum Funding System](https://forum.getmonero.org/8/funding-required) para obtener fondos para tu trabajo, [envía una propuesta](https://forum.getmonero.org/7/open-tasks/2379/forum-funding-system-ffs-sticky)
- [build.getmonero.org](https://build.getmonero.org/) o monero-build.i2p para información detallada de los archivos compilados
- [repo.getmonero.org](https://repo.getmonero.org/monero-project/kovri) o monero-repo.i2p son alternativas a github para repositorios de acceso sin push
- Ve tambien [kovri-site](https://github.com/monero-project/kovri-site) y [monero/kovri meta](https://github.com/monero-project/meta)

## Respuesta vulnerabilidades
- Nuestro [Proceso de respuesta de Vulnerabilidades](https://github.com/monero-project/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md) alienta la divulgación responsable
- También estamos en [HackerOne](https://hackerone.com/monero)

## Contacto y Soporte
- IRC: [Freenode](https://webchat.freenode.net/) | Irc2P con Kovri
  - `#kovri` | Canal de la comunidad y soporte
  - `#kovri-dev` | Canal de desarrollo
- [Monero Mattermost](https://mattermost.getmonero.org/)
- [Monero Slack](https://monero.slack.com/) (pide una invitación en el IRC)
- [Monero StackExchange](https://monero.stackexchange.com/)
- [Reddit /r/Kovri](https://www.reddit.com/r/Kovri/)
- Twitter: [@getkovri](https://twitter.com/getkovri)
- Email:
  - Propósito general / contacto con los medios
    - dev [at] getmonero.org
  - Otros contactos
    - anonimal [at] getmonero.org
    - Huella de PGP: 1218 6272 CD48 E253 9E2D  D29B 66A7 6ECF 9144 09F1

## Donaciones
- Visita nuestra [Pagina de Donaciones](https://getmonero.org/getting-started/donate/) para ayudar a Kovri con tus donaciones
