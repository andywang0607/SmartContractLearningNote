# Function
- Function visibility
- Function modifier
- Fallback function

## Function visibility
- Public
    - Can be called internally and externally
- Private
    - Only for the contract
    - Not external reachable
    - Not devied contracted reachable
- External
    - Can be called from other contracts\
    - Can be called externally
- Internally
    - Only from the contract itself or derived contracts
    - Can't be invoked by transaction

## [Function Modifier](https://docs.soliditylang.org/en/v0.8.0/contracts.html?highlight=view#view-functions)
- View: 
    - Functions do not to modify the state
    - The following statements are considered modifying the state
        1. Writing to state variables.
        2. Emitting events.
        3. Creating other contracts.
        4. Using selfdestruct.
        5. Sending Ether via calls.
        6. Calling any function not marked view or pure.
        7. Using low-level calls.
        8. Using inline assembly that contains certain opcodes.
- Pure:
    - Function do not read from or modify the state
    - Following are considered reading from the state
        1. Reading from state variables.
        2. Accessing address(this).balance or <address>.balance.
        3. Accessing any of the members of block, tx, msg
        4. Calling any function not marked pure.
        5. Using inline assembly that contains certain opcodes.
- Payable
    - Enable function to receive Ether

## [Fallback function](https://docs.soliditylang.org/en/v0.8.6/contracts.html?highlight=fallback#fallback-function)
- Called When a transaction without a function-call is sent to the smart contract
- Called when the function call in the transaction isn't found
- Can only be external
- In the worst case, if a payable fallback function is also used in place of a receive function, it can only rely on 2300 gas being available
- Syntax
    - receive(): receive money
    - fallback(): interact with the Smart Contract without receiving Ether.
```
function () external {

}   
```
```
receive() external payable {

} 
```