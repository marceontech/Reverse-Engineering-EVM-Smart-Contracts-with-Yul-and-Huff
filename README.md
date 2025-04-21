# Reverse-Engineering-EVM-Smart-Contracts-with-Yul-and-Huff
 This HorseStore contract is used for training purposes to practice Reverse Engineering EVM Solidity Smart Contracts with Yul and Huff to learn how compilers and opcodes work by dissecting the contract down to the low level and modify it for Gas Optimization and to get introduced to Formal Verification as part of a full security audit process.


# Getting Started

## Requirements

-   [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)  
    -   You'll know you've done it right if you can run `git --version`
-   [Foundry / Foundryup](https://github.com/gakonst/foundry)
    -   This will install `forge`, `cast`, and `anvil`
    -   You can test you've installed them right by running `forge --version` and get an output like: `forge 0.2.0 (f016135 2022-07-04T00:15:02.930499Z)`
    -   To get the latest of each, just run `foundryup`
-   [Huff Compiler](https://docs.huff.sh/get-started/installing/)
    -   You'll know you've done it right if you can run `huffc --version` and get an output like: `huffc 0.2.0`
-   [Solidity Compiler](https://docs.soliditylang.org/en/latest/installing-solidity.html)
    -   You'll know you've done it right if you can run `solc --verison` and get an output like:
    -   `solc, the solidity compiler commandline interface Version: 0.8.15+commit.e14f2714.Darwin.appleclan`
  


## Quickstart

1. Clone the repo & install dependencies

```
git clone https://github.com/Cyfrin/10-horse-store-s23
cd 10-horse-store-s23
make
```

2. Run tests

```
forge test
```

# Use

## Compile contracts 

To get the raw bytecode of each contract manually:

To get the exact same as what I get, you'll need to use solc version `Version: 0.8.20+commit.a1b79de6.Darwin.appleclang`. 

```
huffc src/huff/HorseStore.huff -b
solc --strict-assembly --optimize --optimize-runs 20000 yul/HorseStoreYul.yul --bin | grep 60 
solc --optimize --optimize-runs 20000 src/HorseStore.sol --bin | grep 60 
solc --optimize --optimize-runs 20000 src/HorseStoreYul.sol --bin | grep 60 
```
