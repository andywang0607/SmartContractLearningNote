# Event
- Study event in solidity

## Introduction
- [Document](https://docs.soliditylang.org/en/v0.8.6/abi-spec.html?highlight=event#events)
- Used for return values from transactions
- Used externally to trigger functionality
- Used as a cheap data storage
- Can not be retrieved from within smart contracts
- Event arguments marked as indexed can be searched for 

### Event as Data storage
- Problem: Storing data is extremely expensive on the Ethereum blockchain
- Solution
    1. Store data off-chain and store only a proof(hash)->Notary
    2. Store data in another blockchain such as IPFS
    3. Store data in event logs if not necessary

### Event in dApps
- Application can subscribe and listen to these events through the RPC interface of an Ethereum client
- Event are inheritable members of contracts
- The log and its event data is not accessible from within contracts

## Practice
```
pragma solidity ^0.5.11;
contract EventExample {

    mapping(address => uint) public tokenBalance;

    event tokenTranser(address _from, address _to, uint _amount);

    constructor() public {
        tokenBalance[msg.sender] = 100;
    }

    function sendToken(address _to, uint _amount) public returns(bool) {
        require(tokenBalance[msg.sender] >= _amount, "Not enough tokens");
        assert(tokenBalance[_to] + _amount >= tokenBalance[_to]);   
        assert(tokenBalance[msg.sender] - _amount <= tokenBalance[msg.sender]);
        tokenBalance[msg.sender] -= _amount;
        tokenBalance[_to] += _amount;

        emit tokenTranser(msg.sender, _to, _amount);
        
        return true;
    }
}
```