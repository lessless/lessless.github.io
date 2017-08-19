
# Monero API docs

Notes
------------

This docs are build with Slate which doesn't support nesting objects. To overcome this limitation all nested structures
are described in hierarchical order, one after another.


Let's take `getbans` call for example. The nested version of its response would be a 2-level deep list:

- `bans` - List of banned nodes:
- `ip` - unsigned int; Banned IP address, in Int format.
  - `seconds` - unsigned int; Local Unix time that IP is banned until.
  - `status` - string; General RPC error code. "OK" means everything looks good.


Instead, a `bans` list item description will be given right after after the root object description

Parameter | Type | Description
--------- | ------- | -----------
bans | array |  List of banned nodes(see below)
status | string |  General RPC error code. "OK" means everything looks good.

_**`bans[]`** field structure_

Parameter | Type | Description
--------- | ------- | -----------
ip | unsigned int | Banned IP address, in Int format.
seconds | unsigned int |   Local Unix time that IP is banned until.


If objects are more than 2 levels deep, than `.`(dot) is used to denote parent - children relationships. For example: ``miner_tx.vout[].target` (See `getblock` call)

A JavaScript terminology is used to describe data types, hence `array` and `object`.

### Building

You're going to need:

 - **Linux or OS X** — Windows may work, but is unsupported.
 - **Ruby, version 2.3.1 or newer**
 - **Bundler** — If Ruby is already installed, but the `bundle` command doesn't work, just run `gem install bundler` in a terminal.

Building:
```shell
bundle exec middleman build --clean
```

Running develpment server:
```shell
# either run this to run locally
bundle install
bundle exec middleman server
```

You can now see the docs at http://localhost:4567

Use `deploy.sh` for [deploying](https://github.com/lord/slate/wiki/Deploying-Slate)

Checkout [Slate](https://github.com/lord/slate) README and Wiki for more detailed instructions

