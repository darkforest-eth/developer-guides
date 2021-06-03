# What is a plugin?

Dark Forest allows players to customize the default webclient via the _plugins_ system. Plugins are snippets of code that players can write to generate alternate views of game data, automate common gameplay flows, or even reskin the game. Essentially, Dark Forest allows players can interact programmatically with the webclient in any way they'd like.

We encourage players to share plugins with the larger community. A community-maintained plugins showcase can be found [here](https://plugins.zkga.me/), with the underlying source code available in [this repository](https://github.com/darkforest-eth/plugins). Follow the instructions in the plugins showcase [README](https://github.com/darkforest-eth/plugins#adding-your-plugin) to submit your plugin to the repository.

It's worth noting that plugins are evaluated in the context of your game and can access all of your private information (including your burner wallet private key!). Additionally, plugins can dynamically load data, which can be switched out from under you. **Use these plugins at your own risk.**

Therefore, it can be dangerous to use any plugins that you haven't written/reviewed yourself or by someone you trust completely. You or someone you trust should control the entire pipeline (such as imported dependencies) and should review plugins before you use them.
