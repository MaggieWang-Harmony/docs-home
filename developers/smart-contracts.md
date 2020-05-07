# Smart Contracts

This section is designed to get the casual smart contract developer up and running deploying ERC20 tokens on a harmony network. **This can be done in under one Minute.**

## One Minute Deploy <a id="one-minute-deploy"></a>

Here is a short video running through the deployment.

## One Minute Instructions <a id="one-minute-instructions"></a>

```text
npm install -g truffle@5.0.38git clone https://github.com/harmony-one/HRC.gitcd HRCcp .envSample .envnpm installtruffle compiletruffle migrate --network testnet --resettruffle networks
```

## Interacting with contracts <a id="interacting-with-contracts"></a>

```text
truffle console --network testnettruffle(testnet)> HarmonyERC20.deployed().then(function(instance){myHRC20=instance})undefinedtruffle(testnet)> myHRC20.symbol()'H20'truffle(testnet)> myHRC20.name()'HarmonyERC20'truffle(testnet)> myHRC20.decimals()BN { negative: 0, words: [ 18, <1 empty item> ], length: 1, red: null }truffle(testnet)> myHRC20.totalSupply()BN {  negative: 0,  words: [ 16777216, 62077800, 20718012, 3, <1 empty item> ],  length: 4,  red: null}
```

## Detailed Overview <a id="detailed-overview"></a>

For detailed instructions, sample files and github repository please see below

* * * 
