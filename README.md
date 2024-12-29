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
        - vv Print logs for all tests
        - vvv Print execution traces for failing tests
        - vvvv Print execution traces for all tests, and setup traces for failing tests.
        - vvvvv  Print execution and setup traces for all tests, including storage changes
      
TEST IS OK
Run command ``` forge test ```
OUTPUT
```solidity
Ran 1 test for test/Jop.t.sol:ITTEST
[PASS] testMahmoudJop() (gas: 11917)
Suite result: ok. 1 passed; 0 failed; 0 skipped; finished in 1.36ms (186.83µs CPU time)

Ran 1 test suite in 19.38ms (1.36ms CPU time): 1 tests passed, 0 failed, 0 skipped (1 total tests)
```
Change jop to make test fail
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;

contract Jop {
    string public mahmoudJop ="Doctor" ;   
}

```
Run command line again to test ```fore test```
OUTPUT  
Test Fail
```solidity
Ran 1 test for test/Jop.t.sol:ITTEST
[FAIL: assertion failed: Doctor != Smart Contract Auditor] testMahmoudJop() (gas: 11914)
Suite result: FAILED. 0 passed; 1 failed; 0 skipped; finished in 451.06µs (100.45µs CPU time)

Ran 1 test suite in 19.97ms (451.06µs CPU time): 0 tests passed, 1 failed, 0 skipped (1 total tests)

Failing tests:
Encountered 1 failing test in test/Jop.t.sol:ITTEST
[FAIL: assertion failed: Doctor != Smart Contract Auditor] testMahmoudJop() (gas: 11914)
```
Run command with verposity ```forge test -vvvv``` to see What is Wrong?
```solidity
No files changed, compilation skipped

Ran 1 test for test/Jop.t.sol:ITTEST
[FAIL: assertion failed: Doctor != Smart Contract Auditor] testMahmoudJop() (gas: 11914)
Traces:
  [135672] ITTEST::setUp()
    ├─ [98061] → new Jop@0x5615dEB798BB3E4dFa0139dFa1b3D433Cc23b72f
    │   └─ ← [Return] 377 bytes of code
    └─ ← [Stop] 

  [11914] ITTEST::testMahmoudJop()
    ├─ [3054] Jop::mahmoudJop() [staticcall]
    │   └─ ← [Return] "Doctor"
    ├─ [0] VM::assertEq("Doctor", "Smart Contract Auditor") [staticcall]
    │   └─ ← [Revert] assertion failed: Doctor != Smart Contract Auditor
    └─ ← [Revert] assertion failed: Doctor != Smart Contract Auditor

Suite result: FAILED. 0 passed; 1 failed; 0 skipped; finished in 1.41ms (307.97µs CPU time)

Ran 1 test suite in 813.86ms (1.41ms CPU time): 0 tests passed, 1 failed, 0 skipped (1 total tests)

Failing tests:
Encountered 1 failing test in test/Jop.t.sol:ITTEST
[FAIL: assertion failed: Doctor != Smart Contract Auditor] testMahmoudJop() (gas: 11914)

Encountered a total of 1 failing tests, 0 tests succeeded
```
You can run command  ```forge test --gas-report ``` to see gas cost
```solidity
╭--------------------------+-----------------+------+--------+------+---------╮
| src/Jop.sol:Jop Contract |                 |      |        |      |         |
+=============================================================================+
| Deployment Cost          | Deployment Size |      |        |      |         |
|--------------------------+-----------------+------+--------+------+---------|
| 163227                   | 782             |      |        |      |         |
|--------------------------+-----------------+------+--------+------+---------|
|                          |                 |      |        |      |         |
|--------------------------+-----------------+------+--------+------+---------|
| Function Name            | Min             | Avg  | Median | Max  | # Calls |
|--------------------------+-----------------+------+--------+------+---------|
| mahmoudJop               | 3054            | 3054 | 3054   | 3054 | 1       |
╰--------------------------+-----------------+------+--------+------+---------╯


Ran 1 test suite in 10.68ms (1.78ms CPU time): 0 tests passed, 1 failed, 0 skipped (1 total tests)
```

      

