# Lending 101

## Introduction

Welcome! This is an automated workshop that will guide you into using AAVE and doing a simple integration in a smart contract.
It is aimed at developpers that are familiar with Solidity and ERC20

## How to work on this TD

### Introduction

The TD has two components, deployed on the goerli testnet:

- An ERC20 token, ticker TD-AAVE-101, that is used to keep track of points
- An evaluator contract, that is able to mint and distribute TD-AAVE-101 points

Your objective is to gather as many TD-AAVE-101 points as possible. Please note :

- The 'transfer' function of TD-AAVE-101 has been disabled to encourage you to finish the TD with only one address
- You can answer the various questions of this workshop with different contracts. However, an evaluated address has only one evaluated contract at a time. To change the evaluated contract associated with your address, call `submitExercice()` with that specific address.
- In order to receive points, you will have to do execute code in `Evaluator.sol` such that the function `TDERC20.distributeTokens(msg.sender, n);` is triggered, and distributes n points.
- This repo contains an interface `IExerciceSolution.sol`. Your ERC20 contract will have to conform to this interface in order to validate the exercice; that is, your contract needs to implement all the functions described in `IExerciceSolution.sol`.
- A high level description of what is expected for each exercice is in this readme. A low level description of what is expected can be inferred by reading the code in `Evaluator.sol`.
- The Evaluator contract sometimes needs to make payments to buy your tokens. Make sure he has enough ETH to do so! If not, you can send ETH directly to the contract.

### Getting to work

- Claim fake tokens from AAVE's faucet. Go to their [website](https://app.aave.com/), activate testnet mode, find V2 markets and find the faucet
- Clone the repo on your machine
- Install the dependencies. Deps in Foudry are git submodules, you have to run `git submodule init` and `git submodule update`.
- Register for an infura API key (optional)
- Create a `.env` file that contains private key for deployment, an infura API key.
- To deploy a contract, configure a script in the [scripts folder](script). Look at the way the TD is deployed and try to iterate
- Test your deployment locallly with `anvil` and `forge script script/your-script.s.sol --fork-url http://localhost:8545 --broadcast -vvvv`
- Deploy on Goerli `forge script script/deployTD.s.sol --rpc-url $goerli_url --broadcast -vvvv `

## Points list

### Setting up

- Fork this repo
- implement IExerciceSolution

### AAVE basics

Using [Aave's website](https://app.aave.com/)

- Activate the testnet option by clicking on the wheel in the top right part of the screen
- Deposit assets in AAVE and call `ex1_showIDepositedTokens()` to get points (2 pts)
- Borrow assets from AAVE and call `ex2_showIBorrowedTokens()` to get points (2 pts)
- Repay assets to AAVE and call `ex3_showIRepaidTokens()` to get points (2 pts)
- Withdraw assets from AAVE and call `ex4_showIWithdrewTokens()` to get points (2 pts)

### AAVE integration

- Write a smart contract that deposits assets in AAVE and call `ex5_showContractCanDepositTokens()` to get points (2 pts)
- Write a smart contract that borrow assets from AAVE and call `ex6_showContractCanBorrowTokens()` to get points (2 pts)
- Write a smart contract that repays assets to AAVE and call `ex7_showContractCanRepayTokens()` to get points (2 pts)
- Write a smart contract that withdraw assets from AAVE and call `ex8_showContractCanWithdrawTokens()` to get points (2 pts)

### Flashloan

- Write a smart contract that uses a FlashLoan (4 pts)

### Extra points

Extra points if you find bugs / corrections this TD can benefit from, and submit a PR to make it better. Ideas:

- Adding a way to check the code of a specific contract was only used once (no copying)
- Publish the code of the Evaluator on Etherscan using the "Verify and publish" functionnality

## TD addresses

- Points contracts [`0x482749F0578D0c8b067865a4eA49B5ef220c456B`](https://goerli.etherscan.io/address/0x482749F0578D0c8b067865a4eA49B5ef220c456B)
- Evaluator [`0xc6895dFD6A256438a83D868DCaE2AdaebeC54616`](https://goerli.etherscan.io/address/0xc6895dFD6A256438a83D868DCaE2AdaebeC54616)
- AAVE address  [`0x4bd5643ac6f66a5237E18bfA7d47cF22f1c9F210`](https://goerli.etherscan.io/address/0x4bd5643ac6f66a5237E18bfA7d47cF22f1c9F210)
