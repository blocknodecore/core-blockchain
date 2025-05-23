# BNC Blockchain Node

This project aims to provide installation, running, and maintenance capabilities of **BNC Chain validator node** for potential and existing BNC Chain Blockchain backers. The consensus structure of this chain is Delegated proof of stake "DPos" and is governed by the symbiosis of BNC's implementation of go-ethereum and our system contracts [https://github.com/blocknodecore/System-Contracts]. This repository has multiple release candidates inline so we recommend checking for updates for better functions and stability.

## System Requirements

**Operating System:** Ubuntu >= 20.04 LTS

**RAM:** 8GB minimum, 32GB recommended

**Persistent Storage:** 25GB minimum, 100GB high-speed SSD recommended

**Note regarding use of GPUs -** GPUs are primarily used in POW consensus chains. Being a DPos BNC chain has not only more TPS and fast block production but also doesn't need a GPU altogether for its purpose.



## How to become a validator
To back the BNC blockchain you can become a validator. Full flow to become a validator, you must:

* Install this package **([See Installation](#installation))**

* Download your newly created validator wallet from your server and import it into your metamask or preferred wallet. Fund this account with the appropriate BNC Coins needed to become a validator. Example command to download the wallet on your local PC. Only works for UNIX-based OSes or on any environment that can run the OpenSSH package:
```bash
  scp -r root@<server_ip>:/root/core-blockchain/chaindata/node1/keystore ./
  scp root@<server_ip>:/root/core-blockchain/chaindata/node1/pass.txt ./
```

* On your server, start the node that you just installed **([See Usage/Example](#usageexamples))**

* Once the node is started and confirmation is seen on your terminal, open the interactive console by attaching tmux session **([See Usage/Example](#usageexamples))**

* Once inside the interactive console, you'll see "IMPORTED TRANSACTION OBJECTS" and "age=<some period like 6d5hr or 5mon 3weeks>". You need to wait until the "unauthorized validator" warning starts to pop up on the console. 

* Once "unauthorized validators" warning shows up, go to https://staking.blocknodecore.com/ and click "Become a validator". Fill in all the details in the form, in the "Fee address" field enter the validator wallet address that you imported into your metamask. Proceed further

* Once the last step is done, you'll see a "🔨 mined potential block" message on the interactive console. You'll also see your validator wallet as a validator on the staking page and on explorer. You should also detach from the console after the whole process is done **([See Usage/Example](#usageexamples))**

## Installation

**You must ensure that:** 
* system requirements are met with careful supervision
* the concerned server/local setup must be running 24/7 
* there is sufficient power and cooling arrangement for your machine if running a local setup 
If failed you may end up losing your stake in the blockchain and your staked coins, if any. You'll be jailed at once with no return point by the blockchain if found down/dead. You'll be responsible for chain data corruption on your node, frying up your motherboard, or damaging yourself and your surroundings. 


To install the BNC validator node in ubuntu linux
```bash
  sudo -i
  apt update && apt upgrade
  apt install git tar curl wget
  reboot
```
Skip the above commands if you have already updated the system and installed the necessary tools.

Connect again to your server after reboot
```bash
  sudo -i
  git clone https://github.com/blocknodecore/core-blockchain.git
  cd core-blockchain
  ./node-setup.sh --validator 1
```
After you run node-setup, follow the on-screen instructions carefully and you'll get confirmation that the node was successfully installed on your system.

**Note regarding your validator account -** While in the setup process, you'll be asked to create a new account that must be used for block mining and receiving gas rewards. You must import this account to your metamask or any preferred wallet. 
 
    
## Usage/Examples

Display help
```bash
./node-setup.sh --help
```
To create/install a validator node. Fresh first-time install
```bash
./node-setup.sh --validator 1
source ~/.bashrc
```
To run the validator node
```bash
./node-start.sh --validator
```
To create/install a RPC node. Fresh first-time install
```bash
./node-setup.sh --rpc
source ~/.bashrc
```
To run the RPC node
```bash
./node-start.sh --rpc
```
To stop the RPC node
```bash
./node-stop.sh --rpc
```
To stop the Validator node
```bash
./node-stop.sh --validator
```
To get into a running node's interactive console/tmux session 
```bash
tmux attach -t node1
```
To stop a running node or the running blockchain node 
```bash
tmux attach -t node1
```

To exit/detach from an interactive console
```text
Press CTRL & b , release both keys, and press d
```



