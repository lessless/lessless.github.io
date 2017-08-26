---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://getmonero.org'>GetMonero.org</a>

includes:
  - daemon_json_rpc
  - daemon_custom_calls
  - wallet_json_rpc
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

All monero-wallet-rpc methods use the same JSON RPC interface.

<pre class="center-column" >
  <code>
  curl -X POST http://127.0.0.1:18082/json_rpc
    -H 'Content-Type: application/json'
    -d '{
      "jsonrpc":"2.0",
      "id":"0",
      "method":"make_integrated_address",
      "params":{
        "payment_id":"1234567890123456789012345678900012345678901234567890123456789000"
      }
    }'
  </code>
</pre>

If the monero-wallet-rpc was executed with the `--rpc-login` argument as `username:password`, then follow this example:

<pre class="center-column" >
  <code>
    curl -X POST http://127.0.0.1:18082/json_rpc
      -u username:password --digest
      -H 'Content-Type: application/json'
      -d '{
        "jsonrpc":"2.0",
        "id":"0",
        "method":"make_integrated_address",
        "params":{
          "payment_id":"1234567890123456789012345678900012345678901234567890123456789000"
        }
      }'
  </code>
</pre>


