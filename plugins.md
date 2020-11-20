# Plugins

**RedisBungee** is the leading player synchronization system for BungeeCord.

The following \(exhaustive\) list of plugins below are RedisBungee-aware. If your plugin supports RedisBungee, let me know and I will add it to this page.

## Automatic integration \#\#

With these plugins, adding RedisBungee should "just work" with no changes.

* [SimpleCommands](http://www.spigotmc.org/resources/simplecommands.289/): Automatic integration of RedisBungee data.
* [BungeeTabListPlus](http://www.spigotmc.org/resources/bungeetablistplus.313/): Automatic integration of RedisBungee data.
* [RedisMessage](http://www.spigotmc.org/resources/redismessage.9260/): Plugin is built on RedisBungee APIs.
* [UntamedChat](http://www.spigotmc.org/resources/untamedchat.2520/): Plugin is built on RedisBungee APIs.
* [Party and Friends Extended Edition for Bungeecord](https://www.spigotmc.org/resources/party-and-friends-extended-edition-for-bungeecord-example-server-hexagonmc-eu.10123/): Uses RedisBungee APIs as soon as RedisBungee is installed.

## Manual integration \#\#

* [BungeeAdminTools](http://www.spigotmc.org/resources/bungee-admin-tools.444/): You must set `redisSupport: true` in the configuration.
* [BungeePlayerCounter](http://www.spigotmc.org/resources/bungeeplayercounter.269/): You must set `datasource: redis` in the configuration.
* [HolographicDisplays](http://dev.bukkit.org/bukkit-plugins/holographic-displays/): You must set `using-RedisBungee: true` in the configuration.
* [UltimateVotes](http://www.spigotmc.org/resources/ultimatevotes-1-8-spigot-bungeecord.516/): You must set `broadcastRedis: true` in the configuration.
* Plugins using [MVdW placeholders](http://www.spigotmc.org/wiki/mvdw-placeholders/): Use `{redisbungeecount}` for global count, `{redisbungeecount@server}` for a specific server.
* [UltimateFriends](http://www.spigotmc.org/resources/ultimate-friends.3964/): You must set `module: "redis"` under `communication`.
* [UltimateVotes \(Bungee\)](http://www.spigotmc.org/resources/ultimatevotes-1-8-spigot-bungeecord-uuid.516/): Can run a command across the network using RedisBungee.
* [BungeeTabComplete](http://www.spigotmc.org/resources/bungeetabcomplete.7328/): Requires toggling a setting in the config.yml file.
* [GlobalTabList](http://www.spigotmc.org/resources/globaltablist.1117/): You must use a `{redis_count}` variable.
* [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/): You must use `%redisbungee_total%`, `%redisbungee_<server>`, and set `hooks.redisbungee: true`.
* [~~Global Perms~~](https://www.spigotmc.org/resources/global-perms.9932/) - _\[Plugin no longer being updated\]_
* [BungeeUtilsals](https://www.spigotmc.org/resources/bungeeutilisals.7865/): Need to set `Use-RedisBungee: true` in the configuration.
* [ReporterGUI](https://www.spigotmc.org/resources/reportergui.8596/)
* [PlayerBalancer](https://www.spigotmc.org/resources/10788/): You have to set the entry 'redisbungee' under 'settings' to 'true'

