send tokens
```bash
simd tx bank send <from> <to> <amount>utinsa --home . --chain-id insachain-t-1
```

Delegate tokens
```bash
simd tx staking delegate <to-validator> <amount>utinsa --from <WALLET-NAME> --home . --chain-id insachain-t-1
```

Withdraw rewards
```bash
simd tx distribution withdraw-all-rewards --from <WALLET-NAME> --home . --chain-id insachain-t-1
```

All transactions help
```bash
simd tx --help
```
