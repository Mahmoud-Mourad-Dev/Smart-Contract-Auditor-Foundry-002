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


