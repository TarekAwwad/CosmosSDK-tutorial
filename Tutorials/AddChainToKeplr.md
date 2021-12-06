## Add a new chain to Keplr

Keplr is a third part wallet extension for Cosmos SDK based chains. Install Keplr extension in you browser and import your wallet by the 24 word mnemonic.
```bash
https://chrome.google.com/webstore/detail/keplr/dmkamcknogkgcdfhhbddcghachkejeap?hl=en
```

Keplr does not natively implement insachain. Add the insachain to keplr by navigating to [wallet.keplr.app](https://wallet.keplr.app/#/dashboard), opening the console and injecting the following code:

```javascipt
await window.keplr.experimentalSuggestChain({
    chainId: "insachain-t-1",
    chainName: "insachain-t-1",
    rpc: "http://51.68.141.150:3317",
    rest: "http://51.68.141.150:36657",
    bip44: {
        coinType: 118,
    },
    bech32Config: {
        bech32PrefixAccAddr: "insa",
        bech32PrefixAccPub: "insa" + "pub",
        bech32PrefixValAddr: "insa" + "valoper",
        bech32PrefixValPub: "insa" + "valoperpub",
        bech32PrefixConsAddr: "insa" + "valcons",
        bech32PrefixConsPub: "insa" + "valconspub",
    },
    currencies: [
        {
            coinDenom: "tinsa",
            coinMinimalDenom: "utinsa",
            coinDecimals: 6,
            coinGeckoId: "tinsa",
        },
    ],
    feeCurrencies: [
        {
            coinDenom: "tinsa",
            coinMinimalDenom: "utinsa",
            coinDecimals: 6,
            coinGeckoId: "tinsa",
        },
    ],
    stakeCurrency: {
        coinDenom: "tinsa",
        coinMinimalDenom: "utinsa",
        coinDecimals: 6,
        coinGeckoId: "tinsa",
    },
    coinType: 118,
    gasPriceStep: {
        low: 0.025,
        average: 0.025,
        high: 0.03,
    },
});

```
