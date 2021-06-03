# What is an RPC endpoint?

As a decentralized game, Dark Forest stores all public game data on a _blockchain_. Currently, Dark Forest v0.6 is run on the [xDAI blockchain](https://www.xdaichain.com/)--an EVM compatible sidechain.

To connect to and retrieve data from a blockchain, you'll need to connect to a _node_ on the blockchain network. A _node_ is a participant in the network that stores and serves the latest blockchain state. Users who wish to download blockchain data can either run a node themselves, or connect to a publicly-provided node via the node's _RPC endpoint_. An RPC \(remote procedure call\) endpoint is like a node's address: it's a URL which requests for blockchain data can be sent to.

The Ethereum [JSON-RPC spec](https://eth.wiki/json-rpc/API) defines the methods which you can use to retrieve data from a node. As a player or 3rd-party developer, you likely won't need to make RPC calls directly with this API--these calls are typically abstracted by web3 libraries like [ethers.js](https://docs.ethers.io/v5/).

By default, the Dark Forest webclient will connect to https://rpc-df.xdaichain.com/, a public endpoint provided by the xDAI team. xDAI maintains a fleet of nodes which respond to requests made to this endpoint. There are other public endpoints you can connect to as well; if you'd like a dedicated node to serve your requests, you can also run your own xDAI node and connect to the endpoint it exposes.

