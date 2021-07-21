# SmartContractLearningNote
My note for learning smart contract


## Test Environment Setup
1. Install [MetaMask](https://metamask.io)
    - A browser plugin which can securely store private keys and connect to different blockchains
    - For testing "Injected Web3" environment
2. Install [Ganache](https://www.trufflesuite.com/ganache)
    - A personal blockchain for rapid Ethereum and Corda distributed application development
    - For testing "Web3 Provider" environment

## Environment
- Javascript VM
    - Data stored in memory
    - Isolated ethereum node in the browser
    - Very useful when you want to test a contract
- Injected Web3
    - It will try to use the "Web3 provider" embedded in the browser
    - Allow to connect with real network service
    - Example: MetaMask
- Web3 Provider
    - Allow to connect with specific RPC address node
    - Example: Ganache

## Note and Practice
### Fundamentals of Solidity
- [Hello world](01_helloworld/helloworld.md)
    - My first smart contract
- [Basic variable type](02_basicvariabletype/basicvariable.md)
    - Study some basic type of solidity
    - Interact with the Smart Contract
    - Verify solidity will catch overflow automaitcally
- [Send and withdraw Ether](03_sendandwithdraw/sendandwithdraw.md)
    - Study Units and Globally Available Variables
    - A coding practice for Send/Withdraw Ether to/from smart contract
- [Life-Cycle and Secure](04_lifecycleandsecure/lifecycleandsecure.md)
    - Security issue
    - Pause smart contract
    - Destroy smart contract
- [Exception Handling](05_exceptionhandling/exceptionhandling.md)
    - Study Require and Assert a in Solidity
- [Function visibility/Function modifier/Fallback Function](06_function/function.md)
    - Function visiblility
    - Function modifier
    - Fallback function
- [Event and ABI](07_Event/eventandABI.md)
    - Study event in solidity
    - Study debugger in Remix and ABI
- Simple Project
    - [Shared Wallet](https://github.com/andywang0607/SharedWallet)

### Web3.js
- [Fundamentals of Web3.js](08_web3/fundamentalsofweb3.md)
    - Study Web3.js
    - Environment Setup
    - Interaction between Smart Contract and Web3.js

### Truffle
- [Supply Chain] (https://github.com/andywang0607/SupplyChain)
    - Learn the low-level function address.call.value
    - Learn the Workflow with Truffle
    - Learn Unit Testing with Truffle

### Go-Ethereum
- [Create Private Chain and Mine Ether](09_geth/geth.md)
