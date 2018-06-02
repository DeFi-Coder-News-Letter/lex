![LEX Logo](https://github.com/216k155/LEX/blob/master/src/qt/res/images/LEX_logo_horizontal.png)

"FIRST OF ITS KIND"

LEXcore is GNU AGPLv3 licensed.

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2F216k155%2FLEX.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2F216k155%2FLEX?ref=badge_shield) [![Build Status](https://travis-ci.org/216k155/LEX.svg?branch=master)](https://travis-ci.org/216k155/LEX) [![GitHub version](https://badge.fury.io/gh/216k155%2FLEX.svg)](https://badge.fury.io/gh/216k155%2FLEX.svg)
<a href="https://discord.gg/27xFP5Y"><img src="https://discordapp.com/api/guilds/364500397999652866/embed.png" alt="Discord server" /></a>

[![Build history](https://buildstats.info/travisci/chart/216k155/LEX?branch=master)](https://travis-ci.org/216k155/LEX?branch=master)

[Website](https://LEXcore.io) — [LEXtre + LEXGate](https://github.com/216k155/LEXtre) - [PoS Web Wallet](https://LEX.poswallet.io) — [Block Explorer](https://explorer.LEXcore.io/) — [Blog](https://reddit.com/r/LEXCoin) — [Forum](https://bitcointalk.org/index.php?topic=2254046.0) — [Telegram](https://t.me/LEXcoinOfficialChat) — [Twitter](https://twitter.com/LEX_Coin)

Features
=============

* LEXgate - Parallel masternode / masternode
* Segwit
* Smart contract
* LEXgate
* New PHI1612 PoW/PoS hybrid algorithm
* Static PoS

The LEXcore Project is a decentralized peer-to-peer banking financial platform, created under an open source license, featuring a built-in cryptocurrency, end-to-end encrypted messaging and decentralized marketplace. The decentralized network aims to provide anonymity and privacy for everyone through a simple user-friendly interface by taking care of all the advanced cryptography in the background.

The LEXgate allow for communications among validated blockchain with the ability to perform tasks and advanced functions. Through the use of Pmn, LEX is able to interact with many other popular blockchains and create a unifying bond among those ecosystems.

LEX doesn't provide direct support for dapp database. Instead, a mechanism to interact with another Blockchain via LEXgate function where the other Blockchain can send and receive trigger function notices and international data through the LEX network via Parallel Masternode (Pmn) and LEXgate. Pmn & LEXgate can also be used to interact with the centralized services such as banker. Those centralism service can connect to the LEX network for specific trigger of the LEXgate via Pmn. It will allow for their developed autonomous system to act based on their behalf. The Pmn will then be developed by the connecting Blockchain developer. LEXcore will have to supply a deployment guide to assist their developer. In other to assist the Centralized services, LEX will need to provide a centralized trustworthy environments. So user have their trusted oversight to verify that the transactions are legitimate.

In addition, without LEXgate and Pmn, Bitcoin and Ethereum cannot interact with each other on the same Blockchain because the technology is incompatible. It is almost impossible before our Pmn and LEXgate functions are implemented. Therefore, we have to introduce a Smartcontract & Segwit features in the next release to verify that we succeed to combine those different technologies together to create a brand new unique features of LEX.

## Coin Specifications

| Specification | Value |
|:-----------|:-----------|
| Total Blocks | `6,000,000` |
| Block Size | `4MB` |
| Block Time | `60s` |
| PoW Reward | `10 LEX` |
| PoS Reward | `1 LEX` |
| Stake Time | `36 hours` |
| Masternode Requirement | `16,120 LEX` |
| Masternode Reward | `40% PoS Block ` |
| Port | `26868` |
| RPC Port | `9888` |
| Masternode Port | `26868` |


Build LEX wallet
----------

### Building for 64-bit Windows

The first step is to install the mingw-w64 cross-compilation tool chain. Due to different Ubuntu packages for each distribution and problems with the Xenial packages the steps for each are different.

Common steps to install mingw32 cross compiler tool chain:

    sudo apt install g++-mingw-w64-x86-64

Ubuntu Xenial 16.04 and Windows Subsystem for Linux

    sudo apt install software-properties-common
    sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu zesty universe"
    sudo apt update
    sudo apt upgrade
    sudo update-alternatives --config x86_64-w64-mingw32-g++ # Set the default mingw32 g++ compiler option to posix.

Once the tool chain is installed the build steps are common:

Note that for WSL the LEXcore source path MUST be somewhere in the default mount file system, for example /usr/src/LEX, AND not under /mnt/d/. If this is not the case the dependency autoconf scripts will fail. This means you cannot use a directory that located directly on the host Windows file system to perform the build.

The next three steps are an example of how to acquire the source in an appropriate way.

    cd /usr/src
    git clone https://github.com/216k155/LEX.git
    sudo chmod -R a+rw LEX

Once the source code is ready the build steps are below.

    PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g')
    cd LEX/depends
    ./build-wins.sh

### Build on Ubuntu

    git clone https://github.com/216k155/LEX.git

    cd LEX
    ./install-dependencies.sh
    ./autogen.sh
    ./configure --disable-tests
    make -j$(nproc)

### Build on OSX

The commands in this guide should be executed in a Terminal application.
The built-in one is located in `/Applications/Utilities/Terminal.app`.

#### Preparation

Install the OS X command line tools:

`xcode-select --install`

When the popup appears, click `Install`.

Then install [Homebrew](https://brew.sh)

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

#### Dependencies

    brew install cmake automake berkeley-db4 leveldb libtool boost@1.66 --c++11 --without-single --without-static miniupnpc openssl pkg-config protobuf qt5 libevent imagemagick --with-librsvg

Link boost 1.66

    brew link boost@1.66 --force

#### Build LEXcore

Clone the LEX source code and cd into LEX

        git clone https://github.com/216k155/LEX.git
        cd LEX
        export LDFLAGS=-L/usr/local/opt/openssl/lib;export CPPFLAGS=-I/usr/local/opt/openssl/include
        ./autogen.sh
        ./configure --disable-tests
        make -j$(nproc)
        make deploy

Setup and Build: Arch Linux
-----------------------------------
This example lists the steps necessary to setup and build a command line only, non-wallet distribution of the latest changes on Arch Linux:

    pacman -S git base-devel boost libevent python
    git clone https://github.com/216k155/LEX
    cd LEX/
    ./autogen.sh
    ./configure --without-miniupnpc --disable-tests
    make -j$(nproc)

Note:
Enabling wallet support requires either compiling against a Berkeley DB newer than 4.8 (package `db`) using `--with-incompatible-bdb`,
or building and depending on a local version of Berkeley DB 4.8. The readily available Arch Linux packages are currently built using
`--with-incompatible-bdb` according to the
As mentioned above, when maintaining portability of the wallet between the standard Bitcoin Core distributions and independently built
node software is desired, Berkeley DB 4.8 must be used.


ARM Cross-compilation
-------------------
These steps can be performed on, for example, an Ubuntu VM. The depends system
will also work on other Linux distributions, however the commands for
installing the toolchain will be different.

Make sure you install the build requirements mentioned above.
Then, install the toolchain and curl:

    sudo apt-get install g++-arm-linux-gnueabihf curl

To build executables for ARM:

    cd depends
    make HOST=arm-linux-gnueabihf NO_QT=1
    cd ..
    ./configure --prefix=$PWD/depends/arm-linux-gnueabihf --enable-glibc-back-compat --enable-reduce-exports LDFLAGS=-static-libstdc++
    make -j$(nproc)

For further documentation on the depends system see [README.md](../depends/README.md) in the depends directory.

Building on FreeBSD
--------------------

Clang is installed by default as `cc` compiler, this makes it easier to get
started than on [OpenBSD](build-openbsd.md). Installing dependencies:

    pkg install autoconf automake libtool pkgconf
    pkg install boost-libs openssl libevent
    pkg install gmake

You need to use GNU make (`gmake`) instead of `make`.
(`libressl` instead of `openssl` will also work)

For the wallet (optional):

    ./contrib/install_db4.sh `pwd`
    setenv BDB_PREFIX $PWD/db4

Then build using:

    ./autogen.sh
    ./configure BDB_CFLAGS="-I${BDB_PREFIX}/include" BDB_LIBS="-L${BDB_PREFIX}/lib -ldb_cxx"
    gmake

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/216k155/LEX/tags) are created
regularly to indicate new official, stable release versions of LEX.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).


Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/qa) of the RPC interface, written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/qa) are installed) with: `qa/pull-tester/rpc-tests.py`

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2F216k155%2FLEX.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2F216k155%2FLEX?ref=badge_large)
