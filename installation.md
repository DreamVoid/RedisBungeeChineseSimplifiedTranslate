# Installation

**RedisBungee** is the leading player synchronization system for BungeeCord.

Installing RedisBungee and connecting it to your other Bungees is easy.

## Requirements \#\#

* A [Redis](http://redis.io/) server.
  * If you are running Debian 8 or Ubuntu 14.04 and above, a suitable server can be installed by running apt-get install redis-server as root.
  * If you are running CentOS 6, you'll need to compile Redis from source. The version in EPEL is not supported by RedisBungee as of 0.3.8.
  * If you are running CentOS 7, a suitable server can be installed by running yum install redis.
  * If you do not have Redis available in your system repositories, or it doesn't contain Redis 2.6 or above, you can download and install it from the [official website](http://redis.io/download).
* Properly synchronized time between all your Bungees. RedisBungee will have problems when your system time is around 27 seconds earlier than another Bungee's. Configuring NTP will usually take care of this for you.

## RedisBungee 0.3 and above \#\#

* Download RedisBungee and place it in your proxy's plugins folder.
* Start then stop the proxy.
* Modify plugins/RedisBungee/config.yml, especially the server-id and redis-server. See the configuration page for more details.
* Start and enjoy!

## RedisBungee 0.2.5 and below \#\#

* Download RedisBungee and place it in your proxy's plugins folder.
* Start then stop the proxy.
* Modify plugins/RedisBungee/config.yml, especially the server-id, redis-server, and linked-servers. It is imperative you include all your proxies in the linked-servers definition!
* Start and enjoy!

### Note about modules \#\#\#

As of build `#787` and above, BungeeCord now includes a modules system. RedisBungee 0.3 will automatically load after these load, but this is only supported by new builds of BungeeCord. If you must use 0.2.x, you will need to disable cmd\_list and cmd\_find so RedisBungee can replace them. To do this:

* Stop your proxy.
* Delete modules/cmd\_list.jar and modules/cmd\_find.jar.
* Edit modules.yml and remove the lines - jenkins://cmd\_list and - jenkins://cmd\_find.
* Restart your proxy.

