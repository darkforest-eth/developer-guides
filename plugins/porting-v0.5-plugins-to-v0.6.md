# Porting v0.5 plugins to v0.6

For most v0.5 plugins, upgrading is as simple as following these two steps:
 - First, replace `plugin.register(new Plugin());` (usually the last line of the v0.5 plugin) with `export default Plugin;`.
 - If the plugin is tracked in the [plugins repository](https://github.com/darkforest-eth/plugins), replace `0.5.0` in the `version` field with `0.6.0`, and the `date` to the current date.

Here's an [example](https://github.com/darkforest-eth/plugins/pull/63/files) port (doesn't update the `date` field).

In a few cases, you might have to alter a few more lines. Here is a (possibly incomplete) list of additional modifications you may have to make:
 - If the plugin is importing utils dynamically with `import('https://plugins.zkga.me/utils/utils.js')`, you should replace any instances of `canUpgrade` with `canPlanetUpgrade`. [example](https://github.com/darkforest-eth/plugins/pull/70/files)
 - `entityStore.planetCanUpgrade` is now a static method; any instance of `df.entityStore.planetCanUpgrade(planet)` should be replaced with `df.entityStore.constructor.planetCanUpgrade(planet)`.

If you want to inspect the differences between the v0.5 and v0.6 clients, you can find the last v0.5 client source code [here](https://github.com/darkforest-eth/client/tree/e13caedd3497fbd3822056694d445ddcb25dca88). Documentation on the v0.6 `df` and `ui` objects can be found [here](https://github.com/darkforest-eth/client/blob/master/docs/classes/backend_gamelogic_gamemanager.default.md) and [here](https://github.com/darkforest-eth/client/blob/master/docs/classes/backend_gamelogic_gameuimanager.default.md), and the source code can be found in the [Dark Forest open-source client](https://github.com/darkforest-eth/client).
