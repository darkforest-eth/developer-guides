---
description: Dark Forest developer resources
---

# Developing for Dark Forest

With Ethereum gaming, the closed source server model has been replaced by a few open source Ethereum contracts. This means you can hack literally every other part of the experience to your liking.

Dark forest [publishes npm packages](https://www.npmjs.com/search?q=%40darkforest_eth) for its contract addresses, types, and utilities functions and releases an [official subgraph](developer-resources/subgraph.md) to ease your development workflow.

## Plugins Developers

Anyone can get started scripting with the Dark Forest Console. Just look out for the command that is printed from your mouse actions. You can copy and repaste that command to run it again any time, or modify it slightly to try something new. Mostly you'll just be replaying a command so dont worry too much about breaking anything, give it a shot. The [df object](https://github.com/darkforest-eth/client/blob/master/docs/classes/Backend_GameLogic_GameManager.default.md) and the [ui object](https://github.com/darkforest-eth/client/blob/master/docs/classes/Backend_GameLogic_GameUIManager.default.md) are the main api surfaces for plugins developers so you'll want to familiarize yourself.

Our community plugins developers have written mini maps, automation plugins, remote miners and much much more. Check the [Dark Forest Community Plugins Showcase](https://plugins.zkga.me/) for inspiration and to copy existing plugins and make them your own. Please join the community by submitting your plugins back there as well.

## Client developers

By forking the [React/WebGL client frontend](https://github.com/darkforest-eth/client) and running one yarn command you'll be running a webpack local dev client against mainnet. This allows you to edit the client to your liking customizing any part of the game and the license even allows you to fork to your own open source version and publish to IPFS or a static site host like netlify to share with your guild or friends.

## Contract Developers

If you're interested in Ethereum smart contract development and Hardhat tooling we release all [smart contract source code and scripts](https://github.com/darkforest-eth/eth) used in developing and maintaining the game

But thats not all. With that knowledge you should be able to write contracts that interact with the mainnet Dark Forest universe, no permission needed. See the [Sophon Reveal Marketplace](https://github.com/projectsophon/df-play-to-earn) example for a contract that lets users sell their daily reveal to the first bidder.

## Circuits developers

Dark Forest's innovative gameplay comes in no small part from its [ZK circuits](https://github.com/darkforest-eth/circuits) design utilizing [iden3's circomlib](https://github.com/iden3/circomlib)

## Unaudited Community Resources

**WARNING**
Nothing in the Dark Forest ecosystem has any guarantee of being audited. Smart contracts could be malicious or be found to be insecure. Further, all plugins and pasted code in the Dark Forest console have access to your private key and ability to sign transactions (without a cpnfirmation popup). This means they could now or in the future take all your funds, planets, artifacts etc from your burner wallet. You should rotate burner wallets often, not keep more funds or nfts than you're willing to lose, and be careful using any plugins that you haven't written yourself or by someone you trust completely. Further, some plugins dynamically load dependencies under the hood meaning a 'safe' plugin could become unsafe in the future! All use is at your own risk.

Theres a whole wild world of amazing community creations. They're mostly being tracked at the [awesome darkforest repo](https://github.com/snowtigersoft/awesome-darkforest)
