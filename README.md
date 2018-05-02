#### About
This is SmartGem core client. This will be the tool to connect to SmartGem blockchain network. Currently the available on Linux. Windows version will be availble in newar future.

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
sudo apt-get install software-properties-common
```
4. The client rely on old version 4.8.3 of Berkeley DB and it is not available as a standard Ubuntu 16.04 package. You need  to Bitcoin PPA.
```
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install libdb4.8-dev libdb4.8++-dev
```
### Build

1. Clone SmartGem repository
```
git clone https://github.com/gemchain/smartgem.git
cd smartgem/src
```

2. Build Core
```
make -f makefile.unix

#If you have a faster and larger memory machine run with the -j to make it faster
make -j4 -f makefile.unix

#run client
./smartgemd
```

3. Build GUI
```
cd ..
qmake
make -j4
#run gui client
./smartgem-qt
```

4. Add RPC username and password. The SmartGem client might ask you to add a rpc username and password. 
```
cd
cd .smartgem
nano smartgem.conf

#Add the line below
rpcuser=user
rpcpassword=pasword

Exit and save. Run ./smartgemd again.
```
