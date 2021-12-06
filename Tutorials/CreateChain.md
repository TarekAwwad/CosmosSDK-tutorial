## Create a test chain from scratch 

Create the node directories
```bash
simd unsafe-reset-all --home .
```

Initiate the chain genesis
```bash
simd init genesis --chain-id insachain-t-1  --home .
```

Change the denom "stake" -> "utinsa"
```bash
vim config/genesis.json
```

Create the genesis valdiator wallet
```bash
simd --home . keys add genesisw
```

Show the created wallet
```bash
simd keys show genesisw --home . --keyring-backend os
```

Feed the genesis validator wallet
```bash
simd add-genesis-account genesisw 100000000utinsa --home . --keyring-backend os
```

Create the genesis supply wallet
```bash
simd --home . keys add supplyw
```

Feed the genesis supply wallet
```bash
simd add-genesis-account supplyw 1000000000000utinsa --home . --keyring-backend os
```

Check the balances in genesis
```bash
grep -A 20 balances config/genesis.json
```

Create the validator genesis tx
```bash
simd gentx genesisw --moniker genesis --home .  50000000utinsa --chain-id insachain-t-1
```

Collect the transactions
```bash
simd collect-gentxs --home .
```

Start the valdiator
```bash
simd start --home . --mode validator
```
