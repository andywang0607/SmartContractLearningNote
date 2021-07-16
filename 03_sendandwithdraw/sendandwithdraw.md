# Deposit and withdraw
- Units and Globally Available Variables
- Send/Withdraw Ether to/from smart contract

## [Units and Globally Available Variables](https://docs.soliditylang.org/en/v0.8.0/units-and-global-variables.html)
- Time Unit
    - seconds
    - minutes
    - hours
    - days
    - weeks
- Special Variables and Functions
    - Exist in the global namespace and are mainly used to provide information about the blockchain or are general-use utility functions.
    1. Block and Transaction Properties
    2. ABI Encoding and Decoding Functions
    3. Error Handling
    4. Mathematical and Cryptographic Functions
    5. Members of Address Types
    6. Contract Related
    7. Type Information

## Send/Withdraw Ether to/from smart contract
- Send Ether to the smart contract
    - receiveMoney: Send Ether to this contract
    - getBalance: Get current balance of this contract
```
// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.1;

contract SendEtherExample {

    uint public balanceReceived;


    function receiveEther() public payable {
        balanceReceived += msg.value;
    }

    function getBalance() public view returns(uint) {
        return address(this).balance;
    }
}
```

- Withdraw money from smart contract
    - withDrawEther: withdraw ether from this contract to whoever call this function
    - withDrawEtherTo: withdraw ether to specific account
```
// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.1;

contract SendEtherExample {

    uint public balanceReceived;


    function receiveEther() public payable {
        balanceReceived += msg.value;
    }

    function getBalance() public view returns(uint) {
        return address(this).balance;
    }
    
    function withDrawEther() public {
        address payable to = payable(msg.sender);
        to.transfer(getBalance());
    }

    function withdrawEtherTo(address payable _to) public {
        _to.transfer(getBalance());
    }
}
```
- Time-Locked Withdraw
```
// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.1;

contract SendEtherExample {

    uint public balanceReceived;
    uint public lockedUntil;

    function receiveEther() public payable {
        balanceReceived += msg.value;
        lockedUntil = block.timestamp + 30 seconds;
    }

    function getBalance() public view returns(uint) {
        return address(this).balance;
    }
    
    function withDrawEther() public {
        if(lockedUntil >= block.timestamp)
            return;
        address payable to = payable(msg.sender);
        to.transfer(getBalance());
    }

    function withdrawEtherTo(address payable _to) public {
        if(lockedUntil >= block.timestamp)
            return;
        _to.transfer(getBalance());
    }
}
```