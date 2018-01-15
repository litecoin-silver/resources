Testnet Litecoin Silver
===

### Litecoin testnet
Litecoin testnet peers are not so stable.
If you want to sync Litecoin Silver pre-fork chain using Litecoin chain, I suggest ot use your own Litecoin node.

Example configuration of ./litecoin/litecoin.conf
```
testnet=1
reindex=1
listen=1
bind=0.0.0.0
rpcuser=<user>
rpcpassword=<password>
```

Run Litecoin peer
```shell
litecoind -daemon -testnet
```

Check downloaded blocks and wait until the last testnet block
```shell
litecoin-cli getblockchaininfo
{
  "chain": "test",
  "blocks":  327895,
  "headers": 327895,
  ...
```

### Bootstrap Ltcsilver from Litecoin node

Example configuration of ./ltcsilver/ltcsilver.conf
```
testnet=1
reindex=1
listen=1
bind=0.0.0.0
connect=<litecoin_peer_ip:19335>
rpcuser=<user>
rpcpassword=<password>
```

Run Ltcsilver peer
```shell
ltcsilverd -daemon -testnet -bootstrap
```

Check downloaded blocks and wait until the last testnet block
```shell
ltcsilver-cli getblockchaininfo
{
  "chain": "test",
  "blocks":  299999,
  "headers": 299999,
  ...
```
Check to reach the block before fork 299999

### Bootstrap Ltcsilver from Ltcsilver node


### Bootstrap Ltcsilver from Ltcsilver seeds
