# Fundamentals of Web3.js
- Study Web3.js
- Environment Setup
- Interaction between Contract and Web3.js

## Web3.js
- A javascript library
- Abstract the json-rpc from the blockchain node
- Modules
    - Eth: For interacting with the Ethereum network
    - Net: For interacting with network properties
    - Personal: For interacting with the Ethereum accounts
    - Shh: For interacting wtih the whisper protocol
    - Bzz: For interacting with swarm network
    - Utils: Some convinient utilities

## Environment Setup
- Install nodejs and npm(Node Package Manager)
```
# Install nodejs
sudo apt update
sudo apt install nodejs -y

# Install npm
sudo apt install npm -y
```

- Install web3.js in current working directory
```
npm init -y
npm install -save web3
```

## Try web3.js API with Terminal
- Query balance of account in Ganache
- Transfer money between account in Ganache
```
# Start NodeJS
node

# Query balance
let Web3 = require('web3'); //attention CAPITAL Web3
let web3 = new Web3(new Web3.providers.HttpProvider('http://localhost:7545'));
web3.eth.getBalance("$MYACCOUNT").then(console.log);

# Transfer money
web3.eth.sendTransaction({from: "$ACCOUNT1", to: "ACCOUNT2", value: web3.utils.toWei("$AMOUNT","ether")});
```

### Interaction Between Contract and Web3.js
- Low Level Method
```
web3.eth.call({from: '$ACCOUNT_IN_GANACHE', to:'$SMART_CONTRACT_ADDRESS', data:'$INPUT'}).then(console.log);
```

- ABI Array Method
```
// Enable to call function with the contract instance
var myContract = new web3.eth.Contract(PASTE_ABI_ARRAY_HERE, 'CONTRACT_ADDRESS');
```