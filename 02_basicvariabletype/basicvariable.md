# Basic Variable
Study the following basic variable type of solidity
- Integer
- Boolean
- String
- Address
- Mapping
- Struct
- Array
- Enum

## Note
- All variable are initialized by default
    - uint and int: 0
    - bool: false
    - string: ""
- A public variable automatically creates a getter function in solidity
- Reference types need a memory location
- Remix is automatically generating buttons for every function

## Integer
- The definition is same as other language
- There uint256 in solidity
- Solidity will catch overflow

```
// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.1;

contract IntegerExample {
    uint8 public myUint8;

     function setMyUint(uint8 _myUint8) public {
        myUint8 = _myUint8;
    }

    function decrement() public {
        myUint8--;
    }

    function increment() public {
        myUint8++;
    }
}
```

## Boolean
- The definition is same as other language
- Nothing important just write a setter function

```
// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.1;

contract BooleanExample {
    bool public myBool;

    function setMyBool(bool _myBool) public {
        myBool = _myBool;
    }
}
```

## String
- No native string manipulation functions
- Strings are expensive to store and work with in Solidity
- Avoid string!! use events instead

```
// SPDX-License-Identifier: GPL-3.0
pragma solidity 0.8.1;

contract StringExample {
    string public myString = 'hello world!';

    function setMyString(string memory _myString) public {
        myString = _myString;
    }
}
```

## Address
- A 20 bytes address
- All information is public
- Member
    - balance: balance in wei
    - .transfer(amount)


### Important concept
- The Smart Contract is stored under its own address
- The Smart Contract can store an address in the variable "myAddress", which can be its own address, but can be any other address as well.
- All information on the blochain is public, so we can retrieve the balance of the address stored in the variable "myAddress"
- The Smart Contract can transfer funds from his own address to another address. But it cannot transfer the funds from another address.
- Transferring Ether is fundamentally different than transferring ERC20 Tokens.

## Mapping
- Syntax: mapping(_KeyType => _ValueType)
- Like hash map
- Public state variables of mappings become a getter

## Struct
- Member of the struct can not be the type of the struct
- It is better to define struct than object
    - For saving gas consumption

## Array
- Fixed or Dynamic size
    - T[k]: fixed size of type T with k elements
    - T[]: Dynamic size of type T
    - T[][5]: 5 dynamic sized arrays
- Member
    - Length
    - Push()

- Avoid use it because of gas cost!
    - It's mostly better to use mappings

## Enum
- Create user-defined type in solidity
- Will be integers internally 