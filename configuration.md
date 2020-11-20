# Configuration

**RedisBungee** is the leading player synchronization system for BungeeCord.

RedisBungee exposes several configuration options to specify a Redis server and modify some core behavior.

### Example \#\#\#

```text
# RedisBungee configuration file.
# PLEASE READ THE WIKI: http://minecraft.imaginarycode.com/

# The Redis server you use.
# Get Redis from http://redis.io/
redis-server: 127.0.0.1
redis-port: 6379
# OPTIONAL: If your Redis server uses AUTH, set the password required.
redis-password: ""
# Maximum connections that will be maintained to the Redis server.
# The default is 8. This setting should be left as-is unless you have some wildly
# inefficient plugins or a lot of players.
max-redis-connections: 8

# An identifier for this BungeeCord instance.
server-id: test1

# Whether or not RedisBungee should install its version of regular BungeeCord commands.
# Often, the RedisBungee commands are desired, but in some cases someone may wish to
# override the commands using another plugin.
#
# If you are just denying access to the commands, RedisBungee uses the default BungeeCord
# permissions - just deny them and access will be denied.
#
# Please note that with build 787+, most commands overridden by RedisBungee were moved to
# modules, and these must be disabled or overridden yourself.
register-bungee-commands: true

# A list of IP addresses for which RedisBungee will not modify the response for, useful for automatic
# restart scripts.
exempt-ip-addresses: []
```

## Options \#\#

### redis-server, redis-port, and redis-password \#\#\#

These specify the connection details to your Redis server. redis-server is the IP address to the server, redis-port is the port where your Redis server is bound, and redis-password is your AUTH/requirepass password \(if you have one\).

### max-redis-connections \#\#\#

**Leave this setting alone**. The default setting usually works fine. Only modify this setting if we recommend doing so.

### server-id \#\#\#

This is the ID that this BungeeCord may be identified by RedisBungee as being. This is an important setting to change - you can not have more than one instance of RedisBungee using the same server ID, as this will lead to data inconsistency issues, and RedisBungee will not be enabled unless the server had been offline for more than 20 seconds.

### register-bungee-commands \#\#\#

This option allows you to not let RedisBungee register its main commands. Other commands \(like /serverid, /serverids, and /sendtoall\) and essential RedisBungee functionality continues working.

### exempt-ip-addresses \#\#\#

If an IP address pinging the server is found in the list specified by this option, RedisBungee will not modify the response given.

