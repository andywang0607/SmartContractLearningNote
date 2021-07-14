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

## Start Coding
- [Hello world](01_helloworld/helloworld.md)