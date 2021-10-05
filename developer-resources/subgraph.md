# Darkforest Subgraph

[The Graph](https://thegraph.com/docs/about/introduction) is a decentralized protocol for indexing and querying data from blockchains. It makes it possible to query data that is difficult to query directly from the smart contract itself.

For Dark Forest the subgraph acts almost as a read only excel spreadsheet client to the game where you can query for any information that is public in the smart contract.

## Forking the subgraph

The [graph schema and mappings](https://github.com/darkforest-eth/eth/tree/master/subgraph) are open sourced and offered as a starting point. Feel free to PR bug fixes and or new features but remember you dont have to rely on our existing graph implementation or hosted url. You can and should publish your instance of thegraph on the hosted site or better yet on your own infrastructure which will be FAR faster to sync. The legacy hosted solution can take days to sync weeks of chain data making patching within the round a difficult task. Syncing a subgraph requires an archive node. xDai offers a free endpoint which thegraph uses which, again, is very slow for being free and open. It would be far better to sync your own xdai archive node.

## Previous Dark Forest subgraphs

* [v5](https://thegraph.com/legacy-explorer/subgraph/jacobrosenthal/dark-forest-v05)
* [v6 R1](https://thegraph.com/legacy-explorer/subgraph/darkforest-eth/dark-forest-v06-round-1)
* [V6 R2](https://thegraph.com/legacy-explorer/subgraph/darkforest-eth/dark-forest-v06-round-2)
* [V6 R3](https://thegraph.com/legacy-explorer/subgraph/darkforest-eth/dark-forest-v06-round-3)
* [V6 R4](https://thegraph.com/legacy-explorer/subgraph/darkforest-eth/dark-forest-v06-round-4)
