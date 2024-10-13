# Smart-Contract-Auditor-Foundry-002 [![Telegram](https://img.shields.io/badge/chat-gray?logo=telegram)](https://t.me/web3Eg_aiuditor)
```diff
-All private key in this course for educational purposes please dont share your private key in plaintext
```
New Example Counter.sol
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;

contract Counter {
    uint256 public count;

    function incerement() public{
        count+=1;
    }

    function decerement() public {
       // count-=1;

    }
    function getCount() public view returns(uint256){
        return count;
    }
    
}
```
To compile this contract
```solidity
forge compile Counter.sol:Counter
```
You can use --names to compile only one contract from src folder
```solidity
forge compile --names contractName
```
 Print compiled contract sizes
 ```solidity
forge compile --sizes
```
Skip building files whose names contain the given filter.
```solidity
forge compile --skip  contractName
```
## Deploy
Script to deploy contract
```solidity
//SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;
import "../src/Counter.sol";
import "forge-std/Script.sol";

contract DeployCounter is Script{
    function run() external {
        vm.startBroadcast();
        Counter counter= new Counter();

        vm.stopBroadcast();
    }
}
```
## Test
write test 
```solidity
//SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;
import "forge-std/Test.sol";
import "../src/Counter.sol";

contract CounterTest is Test{
    Counter counter;
    function setUp() public {
      counter = new Counter();
    }
    function testIntialValue()public {

       assertEq(counter.getCount(),0);
    }
     function testIncrement() public{
        counter.increment();
        assertEq(counter.getCount(), 1);
    }

    function testDecrement() public{
        counter.decrement();
        assertEq(counter.getCount(),0);
    }
}

```
You can also run specific tests by passing a filter ,Inverse versions of these flags also exist (--no-match-contract and --no-match-test).
You can run tests in filenames that match a glob pattern with --match-path.

```silidity
forge test --match-contract <contractName> --match-test <contractFunction>
forge test --match-contract CounterTest --match-test testIncrement
```
You can run tests in filenames that match a glob pattern with --match-path.
The inverse of the --match-path flag is --no-match-path.
```solidity
forge test --match-path test/Counter.t.sol
```
Logs and traces use this command v from verbosity
```solidity
forge test -vv
forge test -vvv
forge test -vvvv
forge test -vvvv
```
Watch mode
```solidity
forge test --watch
```







