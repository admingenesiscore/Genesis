## Building from source Ubuntu 20.04/22.04

Building `agora` requires both a Go (version 1.19 or later) and a C compiler. You can install
them using your favorite package manager. 

### Setup
Clone the Genesis repository
```shell
git clone https://github.com/admingenesiscore/Genesis
```

### Setup Go Path
```shell
sudo nano ~/.profile
```
Paste this into the bottom of the file
```shell
export GOPATH=$HOME/work
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```
```shell
source ~/.profile
```

### Install Go
```shell
wget https://go.dev/dl/go1.20.8.linux-amd64.tar.gz
sudo tar -xvf go1.20.8.linux-amd64.tar.gz
sudo mv go /usr/local && rm go1.20.8.linux-amd64.tar.gz
```
Check that it's installed
```shell
go version
```
You should see something like this:
```shell
go version go1.20.8 linux/amd64
```

Once the dependencies are installed, run

```shell
make agora
```

## Running Genesis Node
Initialize and start the chain.
```
./build/bin/agora init genesis-main.json
```
```
./build/bin agora --bootnodes "enode://9a672272c894f35db7636ea17ec9bcb438c9b242958d63548d679084936c0d2071c9534a0af45aa4c4f5e4607c8eaaa590b46441288af2d615bce7795a15c36e@64.176.172.185:30303,enode://c0303e3ecd64bfed38aa9687374969e18f96dfb7736ec00c8cdd3a40ab383cc99c442f0360e306ba2d34c9e8af0bb3fd0a411a2eb30ddedf36d6801289edfa24@64.176.163.23:30303"
```