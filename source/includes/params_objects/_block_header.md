_**`block_header`** field structure_

Parameter | Type | Description
--------- | ------- | -----------
depth |  string | Blob on which to try to mine a new block.
depth | unsigned int | The number of blocks succeeding this block on the blockchain. A larger number means an older block.
difficulty | unsigned int | The strength of the Monero network based on mining power.
hash | string | The hash of this block.
height | unsigned int | The number of blocks preceding this block on the blockchain.
major_version | unsigned int | The major version of the monero protocol at this block height.
minor_version | unsigned int | The minor version of the monero protocol at this block height.
nonce | unsigned int | a cryptographic random one-time number used in mining a Monero block.
orphan_status | boolean | Usually false. If true, this block is not part of the longest chain.
prev_hash | string | The hash of the block immediately preceding this block in the chain.
reward | unsigned int | The amount of new atomic units generated in this block and rewarded to the miner. **Note: 1 XMR = 1e12 atomic units.**
timestamp| unsigned int | The time the block was recorded into the blockchain.
status | string |  General RPC error code. "OK" means everything looks good.
