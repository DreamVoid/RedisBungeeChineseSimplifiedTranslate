# FAQ

**RedisBungee** is the leading player synchronization system for BungeeCord.

## What is RedisBungee? \#\#

RedisBungee is a player synchronization system that is intended for large, at least semi-dedicated, server deployments where the setup requires two or more BungeeCord instances.

### But what exactly? \#\#\#

RedisBungee:

* **does** expose players on all your BungeeCord instances via a simple API
* **does** link your servers together
* **does not** perform fairy dust to reimplement the BungeeCord API, since doing so is frivolous
* **does not** perform the actual balancing of players on proxies
* **does not** synchronize your BungeeCord configuration
* **does not** serve as a replacement for BungeeCord forced hosts

## What is Redis? \#\#

Quoting the [website](http://redis.io/topics/introduction):

```text
Redis is an open source, BSD licensed, advanced key-value store. It is often referred to as a data structure server since keys can contain strings, hashes, lists, sets and sorted sets.
```

## Can I use RedisBungee on Windows? \#\#

Yes. While to my knowledge that there are some RedisBungee users using Windows, and it works, this is an unsupported configuration for RedisBungee. You must use the Microsoft Open Technology port of Redis to Windows available here. You could also use a Linux VPS to host the Redis server and connect to it from your Windows BungeeCord instances.

## What is the minimum version of Redis required to use RedisBungee? \#\#

RedisBungee \(as of 0.3.8\) requires at least Redis 2.6 or later, as it requires [Lua scripting support](http://redis.io/commands/eval). For best performance, use Redis 2.8.10 or later.

## When I shut down my proxy, RedisBungee gives out lots of errors! \#\#

Please update to BungeeCord [build \#1025](http://ci.md-5.net/job/BungeeCord/1025/) or later, which resolves this issue.

## RedisBungee isn't connecting to my Redis server! \#\#

* Please make sure your Redis server is running.
* Please make sure you're running at least Redis 2.6.
* Please make sure you can connect to your Redis server from the host.
* If you set requirepass in your Redis configuration, you also need to set RedisBungee's redis-password to its value.
* Try using the latest version of RedisBungee.

## Can I use Redis Sentinel with RedisBungee? \#\#

RedisBungee does not currently support Redis Sentinel as there is currently not enough demand for it. It may be added at a future date.

## I installed RedisBungee, but can't interact with a player on another Bungee! \#\#

First, see this page to see some common plugins that support RedisBungee. If you have the plugin's RedisBungee support enabled and it doesn't work, please contact the plugin's author.

If your plugin was not on the list, then it most likely doesn't support RedisBungee. Keep in mind that **RedisBungee is not magic**. It will not instantaneously expose all players on a network. Doing so would involve a non-trivial amount of work for little gain. Contact the author \(or another developer\) to add support for the RedisBungee API to the plugin. In the event you can't do so, contact me \(you must pay for the support to be added\).

## I installed RedisBungee, but am getting method and class-related errors! \#\#

Do not expect support for old versions of BungeeCord or Spigot unless you are willing to edit the plugin or pay for that support. we have little inclination to support old versions of Minecraft as my main compensation avenue for our \(mostly free\) plugins involves the use of the latest version of Minecraft possible.

## I updated BungeeCord and now I get AccessControlExceptions \#\#

Update RedisBungee in order to fix this issue.

## I installed RedisBungee but my tablist isn't synchronized! \#\#

Synchronizing the tablist is not possible with RedisBungee, as it is outside the scope of the plugin. Consider instead using a plugin like [BungeeTabListPlus](http://www.spigotmc.org/resources/bungeetablistplus.313/) instead.

## One of my Bungees doesn't display the proper server count, or the player list is wrong. \#\#

* Please make sure that your server configuration is correct.
* Please make sure you can connect to the Redis server.
* Please make sure all BungeeCord proxies are started.
* **Please make sure that the time is synchronized on all your BungeeCord machines!**RedisBungee will automatically kick a Bungee from the network if it does not update a specific timestamp after 30 seconds. I have collected instructions for some Linux distributions.
* Make sure you are running the same version of RedisBungee on all your BungeeCords. CI builds are especially prone to this, as experimental changes are made in master often.
* Make sure you are using the latest version of RedisBungee.

If these troubleshooting steps failed, you may seek support.

## RedisBungee is acting up! \#\#

* Your plugins could be sending RedisBungee too many requests. Remove all plugins that request data from RedisBungee **first**.
* You may want to set the maxclients in your redis.conf to 0. This requires a restart of Redis.

## I need to make Redis accessible to my external Bungees! \#\#

### Please read [http://redis.io/topics/security](http://redis.io/topics/security) before proceeding. \#\#\#

Set the bind value in your Redis configuration to 0.0.0.0, or comment it out. You can also change the port if desired, for extra security.

Now you have two choices:

* Restrict access to your Redis server
  * IPTables.
    * `iptables -A INPUT -s 127.0.0.1 -p tcp --dport 6379 -j ACCEPT`
    * `iptables -A INPUT -s <BUNGEE-IP> -p tcp --dport 6379 -j ACCEPT`
    * `iptables -A INPUT -p tcp --dport 6379 -j DROP`
  * Other ways
    * You can also use an encrypted and authenticated connection. [spiped](https://www.tarsnap.com/spiped.html) is recommended.
    * Set a password
      * Set the requirepass in your Redis configuration. Please note however that this is at best a backup layer of security as the password is sent in the clear \(you can use SSL tunnelling, but this has a large performance impact and is only recommended for small networks\). You will also need to set the redis-password in your RedisBungee configuration.

You can now reboot your Redis server and your BungeeCord instances.

## I want feature X added to RedisBungee! \#\#

RedisBungee has an intentionally limited scope. In general, if it involves a feature that is not currently available in BungeeCord, it is unlikely to be added unless there is a valid use case for it.

## Where is the source code? \#\#

The source code is available on [GitHub](https://github.com/thechunknetwork/RedisBungee) and is licensed under the [Unlicense](http://unlicense.org/) \(previous to June 9, 2015, I used the WTFPL\). However, I would like it if you submitted me pull requests.

## Do you have a Maven repository? \#\#

md\_5-snapshotshttp://repo.md-5.net/content/repositories/snapshots/

