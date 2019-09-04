---
id: omisego-network-resources
title: OmiseGO Network Rresources
sidebar_label: OmiseGO Network Resources
---


## OMG-JS 

Javascript style guide resources:
* https://standardjs.com
* https://github.com/standard/standard

### Getting started
OMG-JS is the OmiseGO Javascript library you use for communicating with OmiseGo's MoreVP implementation of Plasma, and provides the following functions:

* Deposit (Eth/Token) from the RootChain into the ChildChain.
* Transact on the ChildChain.
* Exit from the ChildChain back to the RootChain.
* Challenge an invalid exit.



### Compatibility

This library is currently compatible with version 0.2 of the OMG Network

### Getting Started

The project is organized into 3 submodules:

1. @omisego/omg-js-rootchain
2. @omisego/omg-js-childchain
3. @omisego/omg-js-util

You can use any of them separately, or all at once by importing the parent `@omisego/omg-js` package

### Installation

#### Node
Requires Node >= 8.11.3
```
npm install @omisego/omg-js
```


#### Browser
Copy the `dist/omg.js` file into your project and include it.
```
<script type="text/javascript" src="omg.js"></script>
```


### API Documentation

[Documentation for omg-js ](http://omisego.github.io/omg-js)

### Design Documentation

[How to sign a transaction](/integration-docs/signing-methods.md)

### Examples

#### Prerequisites

Both Alice's and Bob's Ethereum accounts need to have some ETH in them. The ETH is used for gas costs on the rootchain, fees on the childchain and the actual ETH transferred from Alice to Bob.

#### Running the Examples

You can find example code inside `examples` folder. To run the examples, step inside the `examples` directory. Run `npm install`. Edit your `config.js` file to have to correct settings for your environment.

Let's run through a story between Alice and Bob. In this story, Alice will first deposit some ETH from the root chain into the child chain. Then Alice will transfer some of that ETH to Bob on the child chain. Finally, Bob will exit his funds from the child chain back into the root chain. His root chain balance will be reflected with the extra ETH that Alice sent to him on the child chain.

From the `examples` folder run the scripts below in order to follow the story.

1. [Deposit some ETH from Alice's Rootchain to the Childchain](examples/childchain-deposit.js)
    
    `npm run childchain-deposit`

2. [Send some ETH from Alice's Childchain to Bob's Childchain](examples/childchain-transaction.js)
    
    `npm run childchain-transaction`

Alice has now sent some ETH to Bob. You should see a UTXO for Alice and a UTXO for Bob as a result of this transaction.

3. [Get Alice's and Bob's Childchain UTXOs](examples/childchain-utxos.js)

    `npm run childchain-utxos`

4. [Transfer (exit) all of Bob's Childchain funds to the Rootchain](examples/childchain-exit.js)

    `npm run childchain-exit`

Checking Bob's final rootchain balance you will notice it will be a little less than expected. This is because of rootchain gas costs Bob had to pay to exit the childchain.

