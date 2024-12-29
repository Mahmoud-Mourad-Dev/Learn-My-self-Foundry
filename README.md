## Foundry study
- **Forge** 
  - forge init  create project
  - forge build  to compile contract
  - forge test to test contract
  You’ll notice that two new directories have popped up: out and cache.
The out directory contains your contract artifact, such as the ABI, while the cache is used by forge to only recompile what is necessary.

## Working on an Existing Project
```solidity
$ git clone https://github.com/PaulRBerg/foundry-template
$ cd foundry-template 
$ forge install
```

## Clone a Verified Contract on Chain
```solidity
$ forge clone 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2 WETH9
This creates a new directory WETH9, configures it as a foundry project and clones all
the source code of the contract into it. This also initializes a new git repository
```



