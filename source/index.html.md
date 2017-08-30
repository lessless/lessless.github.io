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

search: true
---

# Introduction

Welcome to the Monero API! The documentation divided into two parts - Daemon and Wallet. Majority of Daemon's RPC calls uses JSON RPC interface while some use their own interfaces, as demonstrated below. In contrast requests Wallet RPC calls are served through the JSON RPC interface entirely.

The JSON RPC endpont is `/json_rpc`

<aside class="notice">
Note: "atomic units" refer to the smallest fraction of 1 XMR according to the monerod implementation. <strong>1 XMR = 1e12 atomic units</strong>.
</aside>


