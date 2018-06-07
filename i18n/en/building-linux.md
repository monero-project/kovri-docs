# Building Instructions for Linux

## Quickstart
1.0. Install dependencies

| Dep          | Min. version  | Vendored | Debian/Ubuntu pkg  | Arch pkg     | Fedora            | Optional | Purpose        |
| ------------ | ------------- | -------- | ------------------ | ------------ | ----------------- | -------- | -------------- |
| GCC          | 4.9.2         | NO       | `build-essential`  | `base-devel` | `gcc`             | NO       |                |
| CMake        | 2.8.12        | NO       | `cmake`            | `cmake`      | `cmake`           | NO       |                |
| Git          | 1.9.1         | NO       | `git       `       | `git`        | `git`             | NO       |                |
| Boost        | 1.58          | NO       | `libboost-all-dev` | `boost`      | `boost-devel`     | NO       | C++ libraries  |
| OpenSSL      | latest stable | NO       | `libssl-dev`       | `openssl`    | `openssl-devel`   | NO       | sha256 sum     |
| Clang        | 3.5           | NO       | `clang      `      | `clang `     | `clang       `    | NO       | Alt Compiler   |
| libminiupnpc | 1.6           | YES      | `libminiupnpc-dev` | `miniupnpc`  | `miniupnpc-devel` | YES      | NAT punching   |
| Doxygen      | 1.8.6         | NO       | `doxygen`          | `doxygen`    | `doxygen`         | YES      | Documentation  |
| Graphviz     | 2.36          | NO       | `graphviz`         | `graphviz`   | `graphviz`        | YES      | Documentation  |

2.0 Build latest boost

3.0 Clone the repo: `https://github.com/monero-project/kovri`

4.0 Build and install using `make` and `make install` respectively

## In-depth instructions

### 1.0 Install dependencies
To build correctly, Kovri has the following install dependencies:

- [Git](https://git-scm.com/download) 1.9.1
- [GCC](https://gcc.gnu.org/) 4.9.2
- [CMake](https://cmake.org/) 2.8.12
- [Boost](http://www.boost.org/) 1.58 (see platform-specific version caveats)
- [OpenSSL](https://openssl.org/) (always the latest stable version)

These are required for Kovri to build properly. There are also a few optional dependencies:

- [Clang](http://clang.llvm.org/) 3.5 ([3.6 or higher on FreeBSD](https://llvm.org/bugs/show_bug.cgi?id=28887))
- [MiniUPnP](https://github.com/miniupnp/miniupnp/releases) 1.6
- [Doxygen](http://www.doxygen.org/) 1.8.6
- [Graphviz](http://graphviz.org/) 2.36

The average person running Kovri will probably not need these, except perhaps MiniUPnP if you are behind a NAT you don't have access to, or are otherwise behind a restrictive firewall. The others will generally be for developers, so any non-contributor can skip them.

To install these, choose the correct shell code below based on the operating system you are running. Code for optional dependencies is included. If you do not want these on your machine you can look at the table provided above to see which ones are optional as well as their names and remove them from the command.

*Note: Remove the `$` before pasting in the code. It is just used to denote separate commands.*

#### Ubuntu Xenial (16.04)
*Note: gcc/g++ and libssl installed by default*

`$ sudo apt-get update && sudo apt-get install git cmake libboost-all-dev libssl-dev clang doxygen graphviz libminiupnpc-dev`

#### Ubuntu Trusty (14.04)

`$ sudo apt-get update && sudo apt-get install git g++-4.9 cmake libboost-all-dev libssl-dev libssl1.0.0 clang doxygen graphviz libminiupnpc-dev`

*Note: In Step 2 we will be building Boost. This step can be skipped in Ubuntu Trusty if you run the following code:*

```bash
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo add-apt-repository ppa:kojoley/boost
$ sudo apt-get update
$ sudo apt-get install libboost-{chrono,log,program-options,date-time,thread,system,filesystem,regex,test}1.58-dev
```

#### Debian (stable)

ADD CONTENT

#### Arch Linux

ADD CONTENT

##### Required
`$ sudo apt-get update && sudo apt-get install git cmake libboost-all-dev libssl-dev clang doxygen graphviz libminiupnpc-dev`

### 2.0 Build latest Boost
Another dependency of Kovri is [Boost](https://boost.org). We install it in a separate step to ensure we are getting the latest version

#### 2.1 Get the latest version of Boost
You can find the latest version of boost on their [website download page](https://www.boost.org/users/download/#live). Unpack this using `tar xvjf CHANGE-ME-TO-FILE-NAME.tar.bz2` or `tar xzf CHANGE-ME-TO-FILE-NAME.tar.gz` depending on the file you downloaded.

#### 2.2 Download and apply Boost patches
There are two patches that need to be applied to our Boost before we build. One for [libressl](https://svn.boost.org/trac/boost/attachment/ticket/12575/boost-1.62-asio-libressl.patch) and one for the [execution monitor file](https://gist.githubusercontent.com/laanwj/bf359281dc319b8ff2e1/raw/92250de8404b97bb99d72ab898f4a8cb35ae1ea3/patch-boost_test_impl_execution_monitor_ipp.patch). Navigate into your recently unpacked boost folder and apply them using the following steps. If either patch says `Reversed (or previously applied) patch detected!  Assume -R?`, type `y` and press enter.

```bash
$ curl -O https://svn.boost.org/trac/boost/attachment/ticket/12575/boost-1.62-asio-libressl.patch
$ patch -p0 < patch-boost_test_impl_execution_monitor_ipp.patch
$ curl -O https://gist.githubusercontent.com/laanwj/bf359281dc319b8ff2e1/raw/92250de8404b97bb99d72ab898f4a8cb35ae1ea3/patch-boost_test_impl_execution_monitor_ipp.patch
$ patch -p0 < patch-boost_test_impl_execution_monitor_ipp.patch

```

The following steps should just be ran verbatim. They define the settings under which Boost will build and install it under those conditions.
```bash
$ echo 'using gcc : : g++ : "-fvisibility=hidden -fPIC" "" "ar" "strip"  "ranlib" "" : ;' > user-config.jam
$ config_opts="runtime-link=shared threadapi=pthread threading=multi link=static variant=release --layout=tagged --build-type=complete --user-config=user-config.jam -sNO_BZIP2=1"
$ ./bootstrap.sh --without-icu --with-libraries=chrono,log,program_options,date_time,thread,system,filesystem,regex,test
$ sudo ./b2 -d2 -d1 ${config_opts} --prefix=${BOOST_PREFIX} stage
$ sudo ./b2 -d0 ${config_opts} --prefix=${BOOST_PREFIX} install
```

### 3.0 Build Kovri
Now that we're done with all the dependencies, it's time to get to building Kovri itself.

#### 3.1 Clone Kovri Nightly
Pull the latest nightly with `$ git clone --recursive https://github.com/monero-project/kovri`.

#### 3.2 Build Kovri and its dependencies
`$ make`

#### 3.3 Install
`$ make util && make install`

*Note: Developers should do this step after every fresh build.*