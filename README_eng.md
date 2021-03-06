# Neth - Android Wallet Manager
Neth is an Android app for managing Ethereum wallets.

_For italians readers, go here:_ [README ENG](README.md)

## Introduction
Neth is built on java and relies on [*web3j*](https://docs.web3j.io/getting_started.html) API for the operations on the Ethereum blockchain.
With Neth is possible to:
* establish a connection with the blockchain
* generate wallets 
* do transactions between wallets 
* call smart contract to manage files

### Connecting to Ethereum
In order to establish a connection to the Ethereum blockchain Neth uses endpoint services provided by [*Infura*](https://infura.io/), which allows nodes virtualization, making even simplier and scalable the access to Ethereum.

### Generating and managing wallets
Wallets are generated as JSON files and stored on the device. When the user wants to create a new wallet, he will be asked to insert a password to cipher the private key stored inside the JSON file. Such file then is stored in the devide internal storage and can be accessed only by the app in runtime. As an extra layer of security, the password must be reinsered whenever the app is launched. As a future implementation, fingerprint and such could be used to unlock the wallets faster.

Wallets are generated with the [*BIP39*](https://en.bitcoin.it/wiki/Seed_phrase#Explanation) standard and are Hierarchical Deterministic, namely every wallet is linked to a unique 12-word passphrase that allow the recover of the wallet in any given time.

Thanks to the web3j API is possible to check in real time the wallets status, inspecting their public address or ether balance. Additionally, it's possible to transfer ether between wallets.

### Smart Contracts
The smart contract feature is possible thanks to the solidity compiler and web3j Java Wrapper. To be able to call the smart contract functions is required to deploy such contract and save its public address; then the .sol object must be compiled: doing so we get the .abi and .bin objects, that will be input for the web3j java wrapper. The output will be the autogenerated java class of the contract to add to the project.
Creating autogenerated java classes starting from smart contracts makes the process extremely fast and simple, even considering the API limits (such as the impossibility to return data structures in contracts because web3js can't translate them)

The contract implemented by Neth is SignUpregistry that can perform the following operations:
- register an user
- upload IPFS hashes
- show heshes of already uploaded documents

Right now is not possible for Neth to interface directly with IPFS (such API do not exist)

### Features
The main page of the app is like this:

![main_page](https://i.imgur.com/WxetGUX.png)

1. Show the connection status
2. Create a new wallet
3. Recovery of a lost wallet by passphrase
4. Unlock the wallet using the password
5. Show wallet info
6. Transfer ether between wallets
7. Call the smart contract operations
8. Delete the wallet

### Technologies involved
 * Android Studio
 * web3j API
 * web3j Command Line Tools
 * solc compiler

## Author
**Gabriele Lavorato**