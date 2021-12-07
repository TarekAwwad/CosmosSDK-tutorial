## API endpoints:
With your local API REST (http://localhost:1317) fetch the following URL.

Fetch your node data:
```
/cosmos/base/tendermint/v1beta1/node_info
```

Fetch a given block:
```
/cosmos/base/tendermint/v1beta1/blocks/{height}
```

Fetch the latest block:
```
/cosmos/base/tendermint/v1beta1/blocks/latest
```

Fetch a transaction:
```
/cosmos/tx/v1beta1/txs/{hash}
```

Fetch a wallet:
```
/cosmos/auth/v1beta1/accounts/{address}
```

Fetch a wallet balance:
```
/cosmos/bank/v1beta1/balances/{address}
```

Fetch a validator:
```
/cosmos/staking/v1beta1/validators/{address}
```

Fetch the validator list:
```
/cosmos/staking/v1beta1/validators
```

A full swagger doc can be found [here](https://v1.cosmos.network/rpc/v0.42.6)
