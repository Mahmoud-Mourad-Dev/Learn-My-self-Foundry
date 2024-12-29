# Foundry Study
## EXAMPLE 1
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;

contract Jop {

    string public mahmoudJop ="Smart Contract Auditor" ;
   
}
```
TEST
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;

import {Test, console} from "forge-std/Test.sol";
import "src/Jop.sol";

contract ITTEST is Test {
    Jop public jop;

    function setUp() public {
        jop = new Jop();
            }

    function testMahmoudJop()public view{
         assertEq(jop.mahmoudJop(),"Smart Contract Auditor");
    }   

}
```
1- To compile contract ``` forge compile ```  or ```forge build``` 

- **forge compile**

     - forge compile --help  ```Print help```
     - forge compile --thread ``` Number of threads to use. Specifying 0 defaults to the number of logical cores```
     - forge compile -vvvvv ```verbosity log messages ```
        - v 
        - vv
        - vvv
        - vvvv
        - vvvvv
