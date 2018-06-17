# Building Instructions for Windows

## Quickstart
1.0 Download [MSYS2](http://msys2.github.io/)

2.0 Update pacman packages with `pacman -Syu` (may need to restart MSYS2 after warnings part way through, run the command again after restart)

3.0 Install dependencies

| Dep          | Pacakage Name                                                        | Optional                | Purpose       |
| ------------ | -------------------------------------------------------------------- | ----------------------- | ------------- |
| GCC          | `mingw-w64-x86_64-gcc`                                               | NO                      |               |
| Git          | `git`                                                                | NO                      |               |
| Make         | `make`                                                               | NO                      |               |
| CMake        | `mingw-w64-x86_64-cmake`                                             | NO                      |               |
| Boost        | `mingw-w64-x86_64-boost`                                             | NO                      | C++ libraries |
| OpenSSL      | `mingw-w64-x86_64-openssl`                                           | NO                      | sha256 sum    |
| libminiupnpc | `mingw-w64-x86_64-miniupnpc`                                         | YES                     | NAT punching  |
| Doxygen      | `mingw-w64-x86_64-doxygen`                                           | YES                     | Documentation |
| Graphviz     | [Link](http://graphviz.org/doc/winbuild.html) (required for Doxygen) | YES (req'd for Doxygen) | Documentation |

*Note: You may have to run `pacman -S mingw-w64-x86_64-ca-certificates ca-certificates` depending on the outputs git is giving you.*

3.0 Clone the repo: `https://github.com/monero-project/kovri`

4.0 Build and install using `make` and `make install` respectively