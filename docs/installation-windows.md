## Building from source Windows

Building `agora` requires Chocolatey. You can follow [this guide](https://chocolatey.org/install#individual) to install it.

### Intall Build Tools
to install the build tool the following commands can be run in an Administrator command prompt
```shell
C:\Windows\system32> choco install git
C:\Windows\system32> choco install golang
C:\Windows\system32> choco install mingw
```

Installing these packages sets up the path environment variables. To get the new path a new command prompt must be opened. To install Genesis, a Go workspace directory must first be created, then the Genesis source code can be created and built.
```shell
C:\Users\xxx> mkdir src\github.com\admingenesiscore
C:\Users\xxx> git clone https://github.com/admingenesiscore/Genesis src\github.com\admingenesiscore\Genesis
C:\Users\xxx> cd src\github.com\admingenesiscore\Genesis
C:\Users\xxx\src\github.com\admingenesiscore\Genesis> go get -u -v golang.org/x/net/context
C:\Users\xxx\src\github.com\admingenesiscore\Genesis> go install -v ./cmd/...
```

## Running Genesis Node
Initialize and start the chain.
```
.\build\bin\agora init genesis-main.json
```
```
.\build\bin agora --bootnodes "enode://9a672272c894f35db7636ea17ec9bcb438c9b242958d63548d679084936c0d2071c9534a0af45aa4c4f5e4607c8eaaa590b46441288af2d615bce7795a15c36e@64.176.172.185:30303,enode://c0303e3ecd64bfed38aa9687374969e18f96dfb7736ec00c8cdd3a40ab383cc99c442f0360e306ba2d34c9e8af0bb3fd0a411a2eb30ddedf36d6801289edfa24@64.176.163.23:30303"
```
