# Go-Ethereum
Create own private chain and mine ether

## Evironment Setup
- Install Geth
```
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install geth
```

## Create Private Chain
1. Prepare genesis.json in working directory
```
{
  "difficulty" : "0x20000",
  "gasLimit"   : "0x8000000",
  "alloc": {},
  "config": {
        "chainId": 15,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    }
}
```
2. Create private chain
```
mkdir chaindata
./geth --datadir=./chaindata init ./genesis.json 
```

3. Start chain
```
# --nodiscover: Disabling running node-discovering algorithm to find peers to connect
./geth --datadir=./chaindata --nodiscover
```