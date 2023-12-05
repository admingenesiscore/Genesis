## How to install and run a Genesis node
Below are guides on how to install and run a Genesis node. 
* [Linux](docs/installation-linux.md)
* [MacOS](docs/installation-macos.md)
* [Windows](docs/installation-windows.md)

## How to run run a signer
**REQUIREMENTS**
* Capability of 99% uptime (VPS or Home Server)
* Fast internet
* Pass our vetting process

If you meet those requirements and you have followed the guides above to setup a node, you can continue below if you would like to run a signer. 

### Create Signer Wallet
You will need a wallet address to act as the signer.
```shell
cd ~/Genesis/build/bin
./agora account new
```

After setting that up, create a `.txt` file to store the wallet's password in that directory. 
```shell
nano pass.txt
``` 

To exit: `control x + y + enter`

### Setting up signer

1. Open up another terminal window

2. Attach to your running node
```shell
cd ~/Genesis/build/bin
./agora attach
```

3. Send a proposal
You can now send a proposal to add your wallet to the list of signers
```shell
clique.propose("YOUR_WALLET_ADDRESS", true)
```

4. Voting period
During the voting epoch, other signers will vote wether or not to add you as a signer. If it was successful you will be added to the list. 

5. Signer list
You can see the list of signers with this command
```shell
clique.getSigners()
```

6. Once you are added, you can start your node like so:
```shell
./agora --unlock YOUR_WALLET_ADDRESS --mine --miner.etherbase YOUR_WALLET_ADDRESS --miner.extradata "Validator Name" --password pass.txt --allow-insecure-unlock --bootnodes "enode://9a672272c894f35db7636ea17ec9bcb438c9b242958d63548d679084936c0d2071c9534a0af45aa4c4f5e4607c8eaaa590b46441288af2d615bce7795a15c36e@64.176.172.185:30303,enode://c0303e3ecd64bfed38aa9687374969e18f96dfb7736ec00c8cdd3a40ab383cc99c442f0360e306ba2d34c9e8af0bb3fd0a411a2eb30ddedf36d6801289edfa24@64.176.163.23:30303"
```

If you want to be able to connect to your node via RPC:
```shell
./agora --http --http.addr 127.0.0.1 --http.port 8545 --http.api "admin,debug,web3,eth,txpool,personal,miner,clique,net" --http.rpcprefix "/" --http.corsdomain "*" --http.vhosts "*" --ws --ws.addr 127.0.0.1 --ws.port 8546 --ws.api "admin,debug,web3,eth,txpool,personal,miner,clique,net" --ws.origins "*" --unlock YOUR_WALLET_ADDRESS --mine --miner.etherbase YOUR_WALLET_ADDRESS --miner.extradata "Validator Name" --password pass.txt --allow-insecure-unlock --bootnodes "enode://9a672272c894f35db7636ea17ec9bcb438c9b242958d63548d679084936c0d2071c9534a0af45aa4c4f5e4607c8eaaa590b46441288af2d615bce7795a15c36e@64.176.172.185:30303,enode://c0303e3ecd64bfed38aa9687374969e18f96dfb7736ec00c8cdd3a40ab383cc99c442f0360e306ba2d34c9e8af0bb3fd0a411a2eb30ddedf36d6801289edfa24@64.176.163.23:30303"
```