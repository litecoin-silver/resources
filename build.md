Build Litecoin Silver
===
A more technical documentation is available for :
* linux https://github.com/litecoinsilver/litecoin/blob/master/doc/build-unix.md
* osx https://github.com/litecoinsilver/litecoin/blob/master/doc/build-osx.md
* windows https://github.com/litecoinsilver/litecoin/blob/master/doc/build-windows.md

### Get Ltcsilver
```bash
git clone https://github.com/litecoinsilver/ltcsilver.git
cd ./ltcsilver
```

### Build Linux
```bash
./autogen.sh
./configure
make
make install # optional
```

### Build requirements
This will build litecoin-qt as well if the dependencies are met.
```bash
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils
```
### Lib Sodium
* install from Ubuntu repository. Note Ubuntu 16.04 has an unsupported libsodium version, install manually.
```bash
sudo apt-get install libsodium18 libsodium-dev
```
* install from sources. Download a [tarball](https://download.libsodium.org/libsodium/releases/) of libsodium, preferably the latest stable version, then follow the ritual:
```bash
./configure
make && make check
sudo make install
```

### Lib BOOST
On at least Ubuntu 14.04+ and Debian 7+ there are generic names for the
individual boost development packages, so the following can be used to only
install necessary parts of boost:
```bash
    sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev
```

### Lib QT
To build with Qt 5 (recommended) you need the following:
```bash
sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler
```

### Berkeley DB
It is recommended to use Berkeley DB 4.8.
```bash
* install from Ubuntu repository. 
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install libdb4.8-dev libdb4.8++-dev
```
* install from sources.
```bash
LITECOIN_ROOT=$(pwd)

# Pick some path to install BDB to, here we create a directory within the litecoin directory
BDB_PREFIX="${LITECOIN_ROOT}/db4"
mkdir -p $BDB_PREFIX

# Fetch the source and verify that it is not tampered with
wget 'http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz'
echo '12edc0df75bf9abd7f82f821795bcee50f42cb2e5f76a6a281b85732798364ef  db-4.8.30.NC.tar.gz' | sha256sum -c
# -> db-4.8.30.NC.tar.gz: OK
tar -xzvf db-4.8.30.NC.tar.gz

# Build the library and install to our prefix
cd db-4.8.30.NC/build_unix/
#  Note: Do a static build so that it can be embedded into the executable, instead of having to find a .so at runtime
../dist/configure --enable-cxx --disable-shared --with-pic --prefix=$BDB_PREFIX
make install

# Configure Litecoin Core to use our own-built instance of BDB
cd $LITECOIN_ROOT
./autogen.sh
./configure LDFLAGS="-L${BDB_PREFIX}/lib/" CPPFLAGS="-I${BDB_PREFIX}/include/" # (other args...)
```
**Note**: You only need Berkeley DB if the wallet is enabled (see the section *Disable-Wallet mode* below).

### Summary
List of commands to install Ltcsilver on an empty vm (tested on Ubuntu artful).
```bash
sudo apt-get update
sudo apt-get install git
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils
sudo apt-get install libsodium18 libsodium-dev
sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install libdb4.8-dev libdb4.8++-dev
git clone https://github.com/litecoinsilver/ltcsilver
cd ltcsilver
./autogen.sh
./configure --enable-debug --without-gui
make
sudo make install
```
