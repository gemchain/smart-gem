#### About
This is SmartGem core client. This will be the tool to connect to SmartGem blockchain network

#### Pre-requisite
1. VPS with min 1GB RAM and 20GB HD space
2. Fresh install Ubuntu 16.04 64bit
3. Enough swap file e.g 2GB

#### Preparing the server
1. Update and upgrade Ubuntu 16.04 64bit
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove

```
2. Install Git
```
sudo apt-get install git
```
3. Install dependencies
```
sudo apt-get install build-essential
sudo apt-get install autoconf libboost-all-dev libssl-dev libprotobuf-dev protobuf-compiler libqt4-dev libqrencode-dev libtool
sudo apt-get install libminiupnpc-dev

```
4. The client rely on old version 4.8.3 of Berkeley DB and it is not available as a standard Ubuntu 16.04 package. You need  to compile from source.
```
1. Download BerkeleyDB source package
wget http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz
```
```
2. Compile it
tar -xvf db-4.8.30.NC.tar.gz
cd db-4.8.30.NC/build_unix
mkdir -p build
BDB_PREFIX=$(pwd)/build
../dist/configure --disable-shared --enable-cxx --with-pic --prefix=$BDB_PREFIX
make install
cd ../..
#Path to your BerkerleyDB build. Change accordingly.
export CPATH="/path to your build/db-4.8.30.NC/build_unix/build/include"
export LIBRARY_PATH="/path to your build/db-4.8.30.NC/build_unix/build/lib"
```
### Build

1. Clone SmartGem repository
```
git clone https://github.com/gemchain/smartgem.git
cd smartgem/src
```

2. Build
```
make -f makefile.unix

#If you have a faster and larger memory machine run with the -j to make it faster
make -j4 -f makefile.unix
```