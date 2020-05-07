# Setup Cheatsheet

If you are new to setting up Validators, start [here](setup-cheatsheet.md).

1. Access your cloud instance.

```text
ssh -i [KEY].pem [SSH ADDRESS]
```

![](https://gblobscdn.gitbook.com/assets%2F-LlEOlYqEG_GKuO5Rehq%2F-M1lvuJz_AHOPm8BoWQR%2F-LycN_8dAOwRpW0m4dlM%2Fimage.png?alt=media)

AWS Connect Example

2. Install `tmux`, if your Linux distribution does not come with it.

3. Download the Harmony CLI.

```text
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

4. Create a BLS Key.

```text
./hmy keys generate-bls-key --passphrase
```

5. Download `node.sh`.

```text
curl -LO https://raw.githubusercontent.com/harmony-one/harmony/master/scripts/node.sh \&& chmod a+x node.sh
```

6. Start a new `tmux` session called `node`.

7. Run the node.

```text
./node.sh -S -c -z -I -N staking -k [BLS KEY FILE].key
```

8. Detach from the tmux session by pressing CTRL and B at the same time, then press D.

9. Check that your node is syncing \(block height &gt; 0\).

```text
./hmy blockchain latest-header
```

10. Create a new wallet.

```text
./hmy keys add [ACCOUNT NAME] --passphrase
```

11. Get tokens for your validator

```text
curl -X GET https://faucet.os.hmny.io/fund?address=[ONE ADDRESS]
```

12. Create your Validator

```text
./hmy --node="https://api.s0.os.hmny.io" staking create-validator \    --validator-addr [ONE ADDRESS] --amount 100000 \    --bls-pubkeys [BLS PUBLIC KEY1],[BLS PUBLIC KEY2] \    --name JohnWhitton --identity JohnIdentity --details "John The Validator" \    --security-contact John --website john@harmony.one \    --max-change-rate 0.1 --max-rate 0.1 --rate 0.1 \    --max-total-delegation 100000000 --min-self-delegation 100000 --passphrase
```

13. Check that your ONE address exists as a validator

```text
./hmy --node="https://api.s0.os.hmny.io" blockchain validator all | grep [ONE ADDRESS]
```

14. Collect rewards.

```text
./hmy --node="https://api.s0.os.hmny.io" staking collect-rewards --delegator-addr [ONE ADDRESS] --passphrase
```

15. Check validator information for active flag / availability \(block signed\) / etc ...

```text
./hmy --node="https://api.s0.os.hmny.io" blockchain validator information [VALIDATOR ONE ADDRESS]
```

​

