# Commands

**RedisBungee** is the leading player synchronization system for BungeeCord.

RedisBungee adds several new commands and modifies the behaviour of others.

| Command | Permission Node | Description |
| :--- | :--- | :--- |
| /glist | bungeecord.command.list | /glist by itself will only give you a player count. /glist showall will display all players. |
| /find | bungeecord.command.find | /find has not been modified in any substantial way. |
| /lastseen | redisbungee.command.lastseen | /lastseen allows you to see how long ago someone was on. |
| /ip | redisbungee.command.ip | /ip allows you to find the IP of a currently online player. |
| /sendtoall | redisbungee.command.sendtoall | /sendtoall allows you to execute a BungeeCord command on all your networks. |
| /serverid | redisbungee.command.serverid | /serverid returns the current RedisBungee instance you are on. |
| /serverids | redisbungee.command.serverids | /serverids returns all server IDs in the network. |
| /pproxy | redisbungee.command.pproxy | /pproxy will return the proxy a player is connected to. |
| /plist | redisbungee.command.plist | /plist acts like /glist, but operates on players currently online on a proxy. It accepts an additional proxy argument, i.e. /plist, /plist atl1, and /plist atl1 showall all work on atl1. |

