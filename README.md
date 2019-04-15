# ssb-gossip

ssb-server gossip plugin

Schedule connections randomly with a **peerlist** constructed from config, multicast [UDP](https://ssbc.github.io/scuttlebutt-protocol-guide/#discovery) announcements, [feed](https://ssbc.github.io/scuttlebutt-protocol-guide/#feeds) announcements, and API-calls.

## peers: sync

Get the current peerlist.

```bash
peers
```

```js
peers(cb)
```

## add: sync

Add an address to the peer table.

```bash
add {addr}
add --host {string} --port {number} --key {feedid}
```

```js
add(addr, cb)
add({ host:, port:, key: }, cb)
```

 - `addr` (address string): An address string, of the following format: `hostname:port:feedid`.
 - `host` (host string): IP address or hostname.
 - `port` (port number)
 - `key` (feedid)

## remove: sync

Remove an address from the peer table.

```bash
remove {addr}
remove --host {string} --port {number} --key {feedid}
```

```js
remove(addr)
remove({ host:, port:, key: })
```

## ping: duplex

used internally by the gossip plugin to measure latency and clock skew

## connect: async

Add an address to the peer table, and connect immediately.

```bash
connect {addr}
connect --host {string} --port {number} --key {feedid}
```

```js
connect(addr, cb)
connect({ host:, port:, key: }, cb)
```

 - `addr` (address string): An address string, of the following format: `hostname:port:feedid`.
 - `host` (host string): IP address or hostname.
 - `port` (port number)
 - `key` (feedid)


## changes: source

Listen for gossip events.

```bash
changes
```

```js
changes()
```

Events come in the following forms:

```
{ type: 'discover', peer:, source: }
{ type: 'connect', peer: }
{ type: 'connect-failure', peer: }
{ type: 'disconnect', peer: }
```

## reconnect: sync

Tell ssb-server to reinitiate gossip connections now.


## enable: sync

Update the config to enable a gossip type.

```bash
enable {type}
```
```js
enable(type, cb)
```

 - type (string): The type of gossip to enable: local, global, or seed. Default
     global.


## disable: sync

Update the config to disable a gossip type.

```bash
disable {type}
```
```js
disable(type, cb)
```

 - type (string): The type of gossip to enable: local, global, or seed. Default
     global.

## License

MIT

