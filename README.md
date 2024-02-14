# Foundry-test
### 1- Forge can run your tests with the forge test command
### 2- All tests are written in Solidity.
### 3- Forge will look for the tests anywhere in your source directory
### 4- Any contract with a function that starts with test is considered to be a test
### 5- Perfect! Let's start with a beginner-friendly example using a simple Counter Contract in Solidity
### 6- This will help you learn the fundamentals of writing tests with Foundry.

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract Counter {
    uint256 public count;

    function increment() public {
        count++;
    }
}

```

## Test-Script
Contract: We'll define a simple contract named Counter that has a single function increment to increase a counter by 1
Test: We'll write a test script named Counter.test.sol to test the functionality of the increment function.

1- We import necessary utilities like Test from Foundry.

2- We define a test contract CounterTest that inherits from Test.

3- Use assertEq to check if the new value is equal to 1.



```solidity

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "forge-std/Test.sol";
import {Counter} from "../src/Counter.sol";

contract CounterTest is Test {
    Counter  counter;

    function setUp() public {
        counter = new Counter();
    }

    function testIncrement() public {
        counter.increment();
        assertEq(counter.count(), 1);
    }
}

```
### you have to get outbut like this after run command forge test

![Screenshot from 2024-02-13 20-51-58](https://github.com/Mahmoud-Mourad-Dev/Foundry-Test/assets/35864731/6e75cffb-2b4f-48ed-af42-0c06d77c385c)
## Forge test
![Forge-test](https://github.com/Mahmoud-Mourad-Dev/Foundry-Test/assets/35864731/ab1affac-3e9d-46e3-a28a-c085d727e599)


#### You can also run specific tests by passing a filter to test one function from contract by this command line
`forge test  --match-test testIncrement`

![Screenshot from 2024-02-14 20-39-33](https://github.com/Mahmoud-Mourad-Dev/Foundry-Test/assets/35864731/7cb755c6-ff84-4224-a9e1-e37c28fc8b65)

#### You can also run specific tests by passing a filter to test only contract by passing contract name by command
`forge test --match-contract Counter`
![Screenshot from 2024-02-14 20-44-14](https://github.com/Mahmoud-Mourad-Dev/Foundry-Test/assets/35864731/c137af67-1dff-4f21-af3b-08862bbc0e0f)
#### run test by path command line
`forge test --match-path test/Counter.t.sol`
![Screenshot from 2024-02-14 20-49-33](https://github.com/Mahmoud-Mourad-Dev/Foundry-Test/assets/35864731/dafcc1a0-ba1d-4edc-979e-f83928d93b96)












