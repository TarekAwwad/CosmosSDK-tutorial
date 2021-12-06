## Create a validator to join the chain

Download and build Go 1.17
```bash
wget https://dl.google.com/go/go1.17.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.17.linux-amd64.tar.gz
```

Check the Go installation
```bash
go version
```

which should output
```bash
go version go1.16 linux/amd64
```

Download and build `simd`
```bash
git clone https://github.com/TarekAwwad/CosmosSDK-tutorial.git
cd cosmos-sdk/
make install
```

Create the node directories
```bash
mkdir insanode
cd insanode
simd unsafe-reset-all --home .
```

Get the genesis
```bash
curl https://github.com/TarekAwwad/CosmosSDK-tutorial/Insachain/genesis.json > config/genesis.json
```

Set the persistent peer in `./conifg/config.toml`
```bash
persistent_peers="7a33c2cf42cfe638dfae122e375ffa759c5203df@51.68.141.150:26656"
```

Enable the REST API in the correspondent section in `./conifg/app.toml`
```bash
enable = true
```

Start your node
```bash
simd start --home . &> simd.log &
```
Now that the relay is up we can declare and launch the validator. Create your validator wallet and save your mnemonic (24 words)
```bash
simd --home . keys add <YOU-WALLET-NAME>
```

Show the created wallet
```bash
simd keys show  <YOU-WALLET-NAME> --home . --keyring-backend os
```

Share your address so that we can feed it with some tokens

Broadcast the validator creation transaction:
```bash
simd tx staking create-validator \
  --commission-max-change-rate=0.1 \
  --commission-max-rate=0.1 \
  --commission-rate=0.1 \
  --min-self-delegation=1 \
  --amount=1000000utinsa \
  --pubkey `simd tendermint show-validator --home .` \
  --moniker=<YOUR-VALIDATOR-NAME> \
  --chain-id=insachain-t-1 \
  --from=<YOU-WALLET-NAME> \
  --home .
```
