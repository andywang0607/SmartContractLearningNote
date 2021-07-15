# Life Cycle and Secure
- Security issue
- Pause smart contract
- Destroy smart contract

## Security Issue
- Risk in previous code
    - Someone funded the Smart Contract
    - But everyone can withdraw to any address according to their choice?
- Solution
    - Ownership-Model
    - Only the owner of contract can transfer money

```
// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.1;

contract OwnershipModelExample {

    address public owner;

    constructor() {
        owner = msg.sender;
    }

    function sendMoney() public payable {

    }

    function withdrawAllMoney(address payable _to) public {
        require(owner == msg.sender, "You are not owner");
        _to.transfer(address(this).balance);
    }
}
```

## Pause Smart Contract
- A Smart Contract cannot be "paused" on a protocol-level on the Ethereum Blockchain
- But we can add some logic "in code" to pause it.

```
// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.1;

contract PauseContractExample {

    address public owner;
    bool public paused;

    constructor() {
        owner = msg.sender;
    }

    function sendMoney() public payable {

    }

    function setPaused(bool _paused) public {
        require(msg.sender == owner, "You are not the owner");
        paused = _paused;
    }

    function withdrawAllMoney(address payable _to) public {
        require(owner == msg.sender, "You are not the owner");
        require(paused == false, "Contract Paused");
        _to.transfer(address(this).balance);
    }
}
```

## Destroy Smart Contract
- We can not erase information from the Blockchain
- But we can update the current state
- Once selfdestruct is called, smart contract can not be interacted
- After destroy contract the money in this contract will sent back to owner

```
// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.1;

contract DestroyContractExample {

    address public owner;
    bool public paused;

    constructor() {
        owner = msg.sender;
    }

    function sendMoney() public payable {

    }

    function setPaused(bool _paused) public {
        require(msg.sender == owner, "You are not the owner");
        paused = _paused;
    }

    function withdrawAllMoney(address payable _to) public {
        require(owner == msg.sender, "You are not the owner");
        require(paused == false, "Contract Paused");
        _to.transfer(address(this).balance);
    }
    
    function destroySmartContract(address payable _to) public {
        require(msg.sender == owner, "You are not the owner");
        selfdestruct(_to);
    }
}
```