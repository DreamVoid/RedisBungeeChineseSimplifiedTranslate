# API

**RedisBungee** is the leading player synchronization system for BungeeCord.

RedisBungee is pragmatically accessible in a few ways.

## API stability \#\#

In general, API-breaking changes are only introduced for new major releases \(e.g. 0.2.5 to 0.3\).

## Recommended: The RedisBungee Java API \(BungeeCord\) \#\#

The recommended way to access RedisBungee is via the RedisBungee Java API, which is available to BungeeCord plugins.

The Javadoc for the API is available from [md\_5's build server](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html).

### Maven \#\#\#

The following repository has all RedisBungee builds:

md\_5-snapshotshttp://repo.md-5.net/content/repositories/snapshots/

Afterwards, you can add the dependency:

com.imaginarycode.minecraftRedisBungee0.3.6-SNAPSHOTprovided

## Plugin Messaging \(Bukkit\) \#\#

From Bukkit, you can access some RedisBungee functionality via the plugin messaging API. RedisBungee listens on its own plugin messaging channel \(RedisBungee\), and expects all messages in Data{Input,Output}Stream format.

### Examples \#\#\#

**Sending messages**

```text
ByteArrayDataOutput out = ByteStreams.newDataOutput();
out.writeUTF("PlayerCount");
out.writeUTF("ALL");
player.sendPluginMessage(MyPlugin.getInstance(), "RedisBungee", out.toByteArray());
```

**Deserializing ServerPlayers results**

```text
private Multiset<String> deserializeNoMembers(ByteArrayDataInput input) {
    int collectionSize = input.readInt();
    Multiset<String> multiset = HashMultiset.create();
    for (int i = 0; i < collectionSize; i++) {
        String in = input.readUTF();
        int cnt = input.readInt();
        multiset.setCount(in, cnt);
    }
    return multiset;
}

private Multimap<String, String> deserializeWithMembers(ByteArrayDataInput input) {
    int collectionSize = input.readInt();
    Multimap<String, String> multimap = HashMultimap.create();
    for (int i = 0; i < collectionSize; i++) {
        String in = input.readUTF();
        int cnt = input.readInt();
        for (int i1 = 0; i1 < cnt; i1++) {
            String in2 = input.readUTF();
            multimap.put(in, in2);
        }
    }
    return multimap;
}
```

**Definitions**

* Player
  * Username or UUID \(Java or Mojang-style\)

**Commands**

| Subchannel | Arguments | Response | Notes |
| :--- | :--- | :--- | :--- |
| PlayerList | Server or ALL | The command returned \(but see the notes\), then a comma-separated list of players. | Due to a bug \(fixed in 0.3.2\), the first string of the response was **Players**, not **PlayerList**. |
| PlayerCount | Server or ALL | The command returned, then the number of players found. |  |
| LastOnline | See `Definitions` | The command returned, then a long specified by the output of the [getLastOnline\(\)](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html#getLastOnline%28java.util.UUID%29) API. |  |
| Proxy | _none_ | The command returned, then the proxy's name | Introduced in 0.3.6 \(June 29, 2015\) |
| ServerPlayers | COUNT or PLAYERS | The command returned, then the type specified, then a serialized multimap | Introduced in 0.3.6 \(June 29, 2015\) |

## Redis PubSub \#\#

RedisBungee supports Redis PubSub. PUBLISH a command to `redisbungee-allservers` to a BungeeCord command on all servers, or `redisbungee-<SERVERID>` to invoke the command on just one server. You can also listen on a separate PubSub channel and handle the PubSubMessageEvent event for it, starting with RedisBungee 0.3. See the \[registerPubSubChannels\(\)\]\([http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html\#registerPubSubChannels\(java.lang.String](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html#registerPubSubChannels%28java.lang.String)...\)\), \[unregisterPubSubChannels\(\)\]\([http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html\#unregisterPubSubChannels\(java.lang.String](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/RedisBungeeAPI.html#unregisterPubSubChannels%28java.lang.String)...\)\) and [PubSubMessageEvent](http://ci.md-5.net/job/RedisBungee/javadoc/com/imaginarycode/minecraft/redisbungee/events/PubSubMessageEvent.html).

If you are invoking a command, make sure that the sender is an instance of `RedisBungeeCommandSender`!

## Not recommended: Tinkering with RedisBungee's datasets \#\#

While this is possible, doing so will cause problems when RedisBungee's data schema changes \(which is sometimes quite often\). A good example of this is the 0.2.x to 0.3.x transition, when UUIDs were stored instead of usernames. RedisBungee does everything humanely possible to hide its internals from other plugins, so backend changes can be made with ease.

