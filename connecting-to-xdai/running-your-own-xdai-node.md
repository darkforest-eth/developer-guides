# Running your own xDAI node

This guide will walk you through how to setup your own non-validator xdai node. Please be aware that you will need at least **50GB** of free storage space and a broadband internet connection in order to run the node.  

## Getting Started

This guide will be using the openethereum node software, as it is easy to use and non-developer friendly. If you want more control over your node you can use the [Nethermind](https://www.xdaichain.com/for-developers/install-xdai-client/nethermind) client written in .NET or you could use the Rust implementation of [Openethereum](https://www.xdaichain.com/for-developers/install-xdai-client/parity).

### Download

- [Openethereum Linux v3.2.6](https://github.com/openethereum/openethereum/releases/download/v3.2.6/openethereum-linux-v3.2.6.zip)

- [Openethereum MacOS v3.2.5](https://github.com/openethereum/openethereum/releases/download/v3.2.5/openethereum-macos-v3.2.5.zip)

- [Openethereum Windows v3.2.5](https://github.com/openethereum/openethereum/releases/download/v3.2.5/openethereum-windows-v3.2.5.zip)

- [Source](https://github.com/openethereum/openethereum/archive/refs/tags/v3.2.5.zip)


## Running Your Node

Firstly, unzip the archive you downloaded. Next, locate the binary file called ***openethereum*** and run it with the following command

```
./openethereum --chain xdai --jsonrpc-port=8545 --jsonrpc-cors=all --jsonrpc-interface=all --jsonrpc-hosts=all --jsonrpc-apis=web3,eth,net,parity --ws-interface=all --ws-apis=web3,eth,net,parity,pubsub --ws-origins=all --ws-hosts=all --ws-max-connections=10 --max-peers=100
```

Or for those running Windows

```
./openethereum.exe --chain xdai --jsonrpc-port=8545 --jsonrpc-cors=all --jsonrpc-interface=all --jsonrpc-hosts=all --jsonrpc-apis=web3,eth,net,parity --ws-interface=all --ws-apis=web3,eth,net,parity,pubsub --ws-origins=all --ws-hosts=all --ws-max-connections=10 --max-peers=100
```

## Syncing The Chain

If you succesfully started the node it should look something like this 

![darkforest](https://user-images.githubusercontent.com/42391793/122550961-59cc3800-d002-11eb-9aec-ce2a32eb5749.png)

Now all that's left to do is wait for your local node to synchronize with the current xdai chain. 
