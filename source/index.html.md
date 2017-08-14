---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://getmonero.org'>GetMonero.org</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Monero API! The documentation divided into two parts - Daemon and Wallet. Majority of Daemon's RPC calls uses JSON RPC interface while some use their own interfaces, as demonstrated below. In contrast requests Wallet RPC calls are served through the JSON RPC interface entirely.

The JSON RPC endpont is `/json_rpc`

<aside class="notice">
Note: "atomic units" refer to the smallest fraction of 1 XMR according to the monerod implementation. <strong>1 XMR = 1e12 atomic units</strong>.
</aside>


# Authentication


The program monero-wallet-rpc replaced the rpc interface that was in simplewallet and then monero-wallet-cli.

> All monero-wallet-rpc methods use the same JSON RPC interface.

```shell
IP=127.0.0.1
PORT=18082
METHOD="make_integrated_address"
PARAMS="{\"payment_id\":\"1234567890123456789012345678900012345678901234567890123456789000\"}"
curl \
    -X POST http://$IP:$PORT/json_rpc \
    -d '{"jsonrpc":"2.0","id":"0","method":"'$METHOD'","params":'"$PARAMS"'}' \
    -H 'Content-Type: application/json'
```

> If the monero-wallet-rpc was executed with the `--rpc-login` argument as `username:password`, then follow this example:

```shell
IP=127.0.0.1
PORT=18082
METHOD="make_integrated_address"
PARAMS="{\"payment_id\":\"1234567890123456789012345678900012345678901234567890123456789000\"}"
curl \
    -u username:password --digest \
    -X POST http://$IP:$PORT/json_rpc \
    -d '{"jsonrpc":"2.0","id":"0","method":"'$METHOD'","params":'"$PARAMS"'}' \
    -H 'Content-Type: application/json'
```

# Daemon JSON RPC methods

## getblockcount

```shell
curl -X POST http://127.0.0.1:18081/json_rpc
  -H 'Content-Type: application/json'
  -d '{"jsonrpc": "2.0", "id": "0", "method": "getblockcount"}'
```

> The above command returns JSON structured like this:

```json
{
   "id": "0",
   "jsonrpc": "2.0",
   "result" :{
      "count": 993163,
      "status": "OK"
   }
}
```

Look up how many blocks are in the longest chain known to the node.

### Inputs

None

### Outputs

Parameter | Type | Description
--------- | ------- | -----------
count |  unsigned int | Number of blocks in longest chain seen by the node.
status | string | General RPC error code. "OK" means everything looks good.


## on_getblockhash

```shell
curl -X POST http://127.0.0.1:18081/json_rpc
  -H 'Content-Type: application/json'
  -d '{"jsonrpc": "2.0","id": "0","method": "on_getblockhash", "params": [912345]}'
```

> The above command returns JSON structured like this:

```json
{
   "id":"0",
   "jsonrpc":"2.0",
   "result":"e22cf75f39ae720e8b71b3d120a5ac03f0db50bba6379e2850975b4859190bc6"
}
```

Look up a block's hash by its height.


### Inputs

Parameter | Type|Description
--------- | ----|-----------
block height |int array| int array of length 1

### Outputs

Parameter | Type | Description
--------- | ------- | -----------
block hash |  string | Block's hash


## getblocktemplate

```shell
curl -X POST http://127.0.0.1:18081/json_rpc
  -H 'Content-Type: application/json'
  -d '{
   "jsonrpc": "2.0",
   "id": "0",
   "method": "getblocktemplate",
   "params": {
      "wallet_address": "44GBHzv6ZyQdJkjqZje6KLZ3xSyN1hBSFAnLP6EAqJtCRVzMzZmeXTC2AHKDS9aEDTRKmo6a6o9r9j86pYfhCWDkKjbtcns",
      "reserve_size": 60
   }
}'

```

> The above command returns JSON structured like this:

```json
{
   "id":"0",
   "jsonrpc":"2.0",
   "result":{
      "blocktemplate_blob":"01029af88cb70568b84a11dc9406ace9e635918ca03b008f7728b9726b327c1b482a98d81ed83000000000018bd03c01ffcfcf3c0493d7cec7020278dfc296544f139394e5e045fcda1ba2cca5b69b39c9ddc90b7e0de859fdebdc80e8eda1ba01029c5d518ce3cc4de26364059eadc8220a3f52edabdaf025a9bff4eec8b6b50e3d8080dd9da417021e642d07a8c33fbe497054cfea9c760ab4068d31532ff0fbb543a7856a9b78ee80c0f9decfae01023ef3a7182cb0c260732e7828606052a0645d3686d7a03ce3da091dbb2b75e5955f01ad2af83bce0d823bf3dbbed01ab219250eb36098c62cbb6aa2976936848bae53023c00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001f12d7c87346d6b84e17680082d9b4a1d84e36dd01bd2c7f3b3893478a8d88fb3",
      "difficulty":982540729,
      "height":993231,
      "prev_hash":"68b84a11dc9406ace9e635918ca03b008f7728b9726b327c1b482a98d81ed830",
      "reserved_offset":246,
      "status":"OK"
   }
}
```

Lookup block template

### Inputs

Parameter | Type | Description
--------- | ------- | -----------
wallet_address |  string |  Address of wallet to receive coinbase transactions if block is successfully mined.
difficulty |  unsigned int | Reserve size.


### Outputs

Parameter | Type | Description
--------- | ------- | -----------
blocktemplate_blob |  string | Blob on which to try to mine a new block.
difficulty |  unsigned int | Difficulty of next block.
height | unsigned int | Height on which to mine.
prev_hash | string | Hash of the most recent block on which to mine the next block.
reserved_offset | unsigned int | Reserved offset.
status | string |  General RPC error code. "OK" means everything looks good.


