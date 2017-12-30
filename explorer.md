Explorer
===
Repository https://github.com/litecoinsilver/explorer

Forked from iquidus https://github.com/iquidus/explorer


## Settings
Main config
```
  // name your instance!
  "title": "IQUIDUS",
  "address": "127.0.0.1:3001",
  // coin name
  "coin": "LitecoinSilver",
  // coin symbol
  "symbol": "LTS",
```
Edit custom local ltcsilver.conf
```
  "wallet": {
    "host": "localhost",
    "port": 19449,
    "user": "",
    "pass": ""
  },
```
Edit mongodb config
```
  // database settings (MongoDB)
  "dbsettings": {
    "user": "iquidus",
    "password": "3xp!0reR",
    "database": "explorerdb",
    "address": "localhost",
    "port": 27017
  },
```
Edit genesis block
```
  // litecoin genesis mainnet
  // "genesis_tx": "97ddfbbae6be97fd6cdf3e7ca13232a3afff2353e29badfab7f73011edd4ced9",
  // "genesis_block": "12a765e31ffd4059bada1e25190f6e98c99d9714d334efa41a195a7e7e04bfe2",
  // litecoin genesis testnet
  // https://chain.so/api/v2/block/LTCTEST/4966625a4b2851d9fdee139e56211a0d88575f59ed816ff5e6a63deb4e3e29a0
  "genesis_tx": "97ddfbbae6be97fd6cdf3e7ca13232a3afff2353e29badfab7f73011edd4ced9",
  "genesis_block": "4966625a4b2851d9fdee139e56211a0d88575f59ed816ff5e6a63deb4e3e29a0",
```
## Install
```bash
npm install
```
## Start
Start frontend
```bash
npm start
open http://localhost:3001
```
Start update process
```bash
node scripts/sync.js index check
```
