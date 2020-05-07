# AutoNode

Our team is currently working on optimizing AutoNode. If you face any issues, please ask our 24/7 support group for assistance at: [https://harmony.one/volunteers](https://harmony.one/volunteers).

## **Installing AutoNode** <a id="installing-autonode"></a>

### **Step 1:** Spin up your instance on [AWS](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws) or [other providers](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides). <a id="step-1-spin-up-your-instance-on-aws-or-other-providers"></a>

> It is recommended to go with Ubuntu or Amazon Linux as your operating system.

### **Step 2:** [SSH](https://docs.harmony.one/home/validators/first-time-setup/cloud-guides/aws#step-2-connecting-to-your-aws-instance) into the machine. <a id="step-2-ssh-into-the-machine"></a>

AutoNode **DOES NOT** run with root, thus you need to login with a user that is not root.

**Most cloud providers \(like AWS\) give you such an account as the default login.** However, if you don't have a user that is not root, follow the procedures below to create one, otherwise you can just skip this part and go to Step 3.

You can choose any username you want. It will ask for a password and a password confirmation. We will also add this user to the sudo group. Please keep track of this password for future use!

```text
sudo useradd -m 
sudo passwd sudo adduser  sudo
```

Now login with the new username you just created.

If you wish to automatically reset your node during hard resets \(the `--auto-reset` option in step 7\) your user \(\) must have sudo access without a passphrase. Follow instructions [here](https://www.cyberciti.biz/faq/linux-unix-running-sudo-command-without-a-password/) to set that up.

If you don't want to do that, you can still run AutoNode! Only thing is that on hard resets, you have to do is step 6 and 7 to restart your node.

### **Step 3:** Install AutoNode. <a id="step-3-install-autonode"></a>

```text
curl -O https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/install.sh && chmod +x ./install.sh && ./install.sh && rm ./install.sh
```

If you are upgrading your AutoNode from a previous version the installer might ask you some questions. Answer with Y for the upgrading process to go on.

### **Step 4:** Add or import a validator key. <a id="step-4-add-or-import-a-validator-key"></a>

Import Private Key \(not recommended\)

```text
./hmy keys import-private-key 
```

### **Step 5:** Edit the configuration file and change the `validator-addr`to the ONE address created on Step 4.  <a id="step-5-edit-the-configuration-file-and-change-the-validator-addrto-the-one-address-created-on-step-4"></a>

```text
./auto_node.sh edit-config
```

> Note that `identity` must be unique or else your validator won't get created.

> Save and exit the configuration by pressing **Ctrl + X** then **Y**, then by hitting **enter**.

Note that the ONE address has to be in quotes

### **Step 6:** Fund your ONE account. For OSTN, the faucet is [here](https://faucet.os.hmny.io/). \*\*_**\(for OSTN P3 phase the faucet is not active\)**_ <a id="step-6-fund-your-one-account-for-ostn-the-faucet-is-here-for-ostn-p3-phase-the-faucet-is-not-active"></a>

### **Step 7:** Run your validator. <a id="step-7-run-your-validator"></a>

```text
./auto_node.sh run --auto-active --auto-reset --clean
```

> Answer the prompts with `Y` or `N` \(this process may take a minute\). Feel free to exit with **Ctrl+Z** after your node syncs!

You can view all the commands for AutoNode with `~/auto_node.sh -h`

## **Monitoring** <a id="monitoring"></a>

If any of the commands activates a monitoring screen, you can always exit using **Ctrl**+**Z**.

### **1\) View the log of your Harmony Monitor:** <a id="1-view-the-log-of-your-harmony-monitor"></a>

```text
./auto_node.sh monitor log
```

### 2\) Using TUI <a id="2-using-tui"></a>

![](https://gblobscdn.gitbook.com/assets%2F-LlEOlYqEG_GKuO5Rehq%2F-M699yw-ve-aaK3-tJ4k%2F-M69AulVkJZw7M9OTsYA%2Fimage.png?alt=media&token=ee4191d7-476f-4adc-84cc-de55f57bfe42)

### 3\) View the status of your Harmony Monitor daemon: <a id="3-view-the-status-of-your-harmony-monitor-daemon"></a>

```text
./auto_node.sh monitor status
```

### 4\) Restart your Harmony Monitor daemon: <a id="4-restart-your-harmony-monitor-daemon"></a>

```text
./auto_node.sh monitor restart
```

## Upgrade AutoNode <a id="upgrade-autonode"></a>

### 1\) Deactivate your validator during the upgrade process <a id="1-deactivate-your-validator-during-the-upgrade-process"></a>

```text
./auto_node.sh deactivate
```

### 2\) Safely kill AutoNode & its monitor \(if alive\) <a id="2-safely-kill-autonode-and-its-monitor-if-alive"></a>

### 3\) Update AutoNode by running the install step again: <a id="3-update-autonode-by-running-the-install-step-again"></a>

```text
curl -O https://raw.githubusercontent.com/harmony-one/auto-node/master/scripts/install.sh && chmod +x ./install.sh && ./install.sh && rm ./install.sh
```

### 4\) Start up your node again but this time _without_ the `--clean` option. <a id="4-start-up-your-node-again-but-this-time-without-the-clean-option"></a>

```text
 ./auto_node.sh run --auto-active --auto-reset
```

> Once your node is done syncing, AutoNode will automatically activate your validator to be elected in the next epoch!

### 5\) \(Optional\) If needed, you might have to activate your validator manually, do so with: <a id="5-optional-if-needed-you-might-have-to-activate-your-validator-manually-do-so-with"></a>

## Cleaning Keys <a id="cleaning-keys"></a>

### 1\) You can cleanse your BLS \(based on performance of a key\) with: <a id="1-you-can-cleanse-your-bls-based-on-performance-of-a-key-with"></a>

```text
 ./auto_node.sh cleanse-bls
```

### 2\) Remove all keys except for keys running on your current autonode with: <a id="2-remove-all-keys-except-for-keys-running-on-your-current-autonode-with"></a>

```text
./auto_node.sh cleanse-bls --hard
```

## More detailed documentation can be found [here](https://github.com/harmony-one/auto-node). <a id="more-detailed-documentation-can-be-found-here"></a>

> Feel free to contribute or open issues!

