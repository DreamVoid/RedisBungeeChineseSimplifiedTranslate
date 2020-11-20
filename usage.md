# 用法

**RedisBungee** is the leading player synchronization system for BungeeCord.

This page explains the configuration and usage of a RedisBungee setup after it has been installed.

## Configuring your proxy and servers \#\#

This step is largely dependent on how you configured your BungeeCord setup.

### I do not have any other BungeeCord plugins, or my plugins do not interact with other players. \#\#\#

In this case, RedisBungee will typically work "out of the box" and there is no additional configuration. However, see the Bukkit section below.

### I have BungeeCord plugins that interact with players. \#\#\#

In this case you will either need to convert to a BungeeCord setup without these plugins or configure/update your existing plugins to use RedisBungee.

### What about my Bukkit plugins? \#\#\#

In general, plugins that use player-targeted messages that perform actions \(like the Connect message\) will always work with RedisBungee. However, if they reference other players and servers, they may not work and require special attention \(likely a messaging facility\).

## Adding a new proxy \#\#

Adding a new proxy is simple:

* Configure the new BungeeCord to have the same servers as your existing ones.
* Follow the [install](https://github.com/minecrafter/RedisBungee/wiki/Installation) guide, but make sure your server-id is not used by another BungeeCord instance and that the redis-server connects to the same Redis server as your other instances.

Not following these steps correctly will **cause issues**!

