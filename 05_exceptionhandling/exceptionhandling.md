# Exception Handling
Study Require and Assert a in Solidity

## Require and Assert
- Syntax
    - assert(bool condition)
    - require(bool condition, string message)
- Comparison
    - Assert comsume all gas
    - Require return remaining gas
- Enable to let user know what error happened

## When to use
- Require
    - Validate user input
- Assert
    - Validate invariant

## Practice
- Without exception handling
    - User will not know what happened
```
//SPDX-License-Identifier: MIT

pragma solidity 0.6.12;

contract ExceptionExample {

    mapping(address => uint) public balanceReceived;

    function receiveMoney() public payable {
        balanceReceived[msg.sender] += msg.value;
    }

    function withdrawMoney(address payable _to, uint _amount) public {
        if(_amount > balanceReceived[msg.sender])
            return;
        balanceReceived[msg.sender] -= _amount;
        _to.transfer(_amount);
    }
}
```

- With exception handling 
```
//SPDX-License-Identifier: MIT

pragma solidity 0.6.12;

contract ExceptionExample {

    mapping(address => uint) public balanceReceived;

    function receiveMoney() public payable {
        balanceReceived[msg.sender] += msg.value;
    }

    function withdrawMoney(address payable _to, uint _amount) public {
        require(_amount <= balanceReceived[msg.sender], "Not Enough Funds, aborting");

        balanceReceived[msg.sender] -= _amount;
        _to.transfer(_amount);
    }
}
```