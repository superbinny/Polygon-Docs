---
id: remix
title: Using Remix
sidebar_label: Using Remix
keywords:
  - docs
  - matic
image: https://matic.network/banners/matic-network-16x9.png
description: Build your next blockchain app on Polygon.
---

# Using Remix

import useBaseUrl from '@docusaurus/useBaseUrl';

A Hello World style starter project. Deploys a smart contract with a message, and renders it in the front-end. You can change the message using the interact panel!

This dapp implements a "Hello World" style application that echoes a message passed to the contract to the front end. This tutorial is intended to be followed using the online IDE available at [Remix IDE](https://remix.ethereum.org).

#### Setting up [Remix IDE](https://remix.ethereum.org)

* Remix IDE - an online IDE to develop smart contracts.
* If you’re new to Remix, You’ll first need to activate two modules: Solidity Compiler and Deploy and Run Transactions.
* search for 'Solidity Compiler' and 'Deploy and Run Transactions' plugins in the plugin tab in Remix

![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/search-plugins.png%22\)%7D)- Activate the two plugins![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/add-plugins.png%22\)%7D)- Select Solidity Environment![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/RemixIDE\_Step1.png%22\)%7D)- ![RemixIDE\_Step2](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/Screenshot\_2020-02-14\_at\_12.52.45\_PM.png%22\)%7D) Go to File Explorers, And Create a new file ![](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/Screenshot\_2020-02-14\_at\_12.51.59\_PM.png%22\)%7D), Name it HelloWorld.sol

* Copy/Paste the Smart contract below into the newly created file `HelloWorld.sol`

## **The smart contract**

```js
// Specifies that the source code is for a version
// of Solidity greater than 0.5.10
pragma solidity ^0.5.10;

// A contract is a collection of functions and data (its state)
// that resides at a specific address on the Ethereum blockchain.
contract HelloWorld {

    // The keyword "public" makes variables accessible from outside a contract
    // and creates a function that other contracts or SDKs can call to access the value
    string public message;

    // A special function only run during the creation of the contract
    constructor(string memory initMessage) public {
        // Takes a string value and stores the value in the memory data storage area,
        // setting `message` to that value
        message = initMessage;
    }

    // A publicly accessible function that takes a string as a parameter
    // and updates `message`
    function update(string memory newMessage) public {
        message = newMessage;
    }
}
```

The first line, `pragma solidity ^0.5.10` specifies that the source code is for a Solidity version greater than 0.5.10. [Pragmas](https://solidity.readthedocs.io/en/latest/layout-of-source-files.html#pragma) are common instructions for compilers about how to treat the source code (e.g., pragma once).

A contract in the sense of Solidity is a collection of code (its functions) and data (its state) that resides at a specific address on the Ethereum blockchain. The line `string public message` declares a public state variable called `message` of type `string`. You can think of it as a single slot in a database that you can query and alter by calling functions of the code that manages the database. The keyword public automatically generates a function that allows you to access the current value of the state variable from outside of the contract. Without this keyword, other contracts have no way to access the variable.

The [constructor](https://solidity.readthedocs.io/en/latest/contracts.html#constructor) is a special function run during the creation of the contract and cannot be called afterward. In this case, it takes a string value `initMessage`, stores the value in the [memory](https://solidity.readthedocs.io/en/latest/introduction-to-smart-contracts.html#storage-memory-and-the-stack) data storage area, and sets `message` to that value.

The `string public message` function is another public function that is similar to the constructor, taking a string as a parameter, and updating the `message` variable.

#### Compile Smart Contract

*

\<img src={useBaseUrl("img/helloworld/Screenshot\_2020-02-14\_at\_1.00.03\_PM.png")} /> Go to Solidity Compiler

* Select Compiler Version to 0.5.10
* Now, `Compile HelloWorld.sol`
* After Successful Compilation, it will show \<img src={useBaseUrl("img/helloworld/Screenshot\_2020-02-14\_at\_1.08.22\_PM.png")} />
* Now, We have to deploy our smart contract on Polygon Network. For that, we have to connect to web3 world, this can be done by using any of the services like Metamask, Brave, Portis etc. We will be using Metamask. Please follow this [tutorial to setup a Metamask Account](../docs/develop/metamask/hello/).
* Open Metamask and select Custom RPC from the networks dropdown

![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/metamask-custom-rpc.png%22\)%7D)

* Put in a Network name - “Matic Mumbai Testnet”
* In URL field you can add the URL as "https://rpc-mumbai.maticvigil.com"
* Enter the Chain ID: 80001
* (Optional Fields) Symbol: "maticmum" and Block Explorer URL: "https://mumbai.polygonscan.com/"

![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/metamask\_mumbai\_setup.png%22\)%7D)- Go ahead and click save - Copy your address from Metamask![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/Screenshot\_2020-01-09\_at\_1.24.49\_PM.png%22\)%7D)

* Head over to [Faucet](https://faucet.polygon.technology) and request test ether - you will need this pay for gas on Matic. Select 'Mumbai' as the network and 'MATIC Token' as the token in the faucet
* Now, let's Deploy the Smart Contract on Matic Network
* Select Injected Web3 in the Environment dropdown and your contract

![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/Screenshot\_2020-02-14\_at\_1.39.04\_PM.png%22\)%7D)

* Accept the Connection Request!

![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/Screenshot\_2020-02-14\_at\_1.59.10\_PM.png%22\)%7D)

* Once Metamask is connected to Remix, the ‘Deploy’ transaction would generate another metamask popup that requires transaction confirmation.

![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/Screenshot\_2020-02-14\_at\_1.45.23\_PM.png%22\)%7D)

**Congratulations!** You have successfully deployed HelloWorld Smart Contract. Now you can interact with the Smart Contract. Check the deployment status here: https://mumbai.polygonscan.com/.

![RemixIDE\_Step1](../docs/develop/%7BuseBaseUrl\(%22img/helloworld/Screenshot\_2020-02-14\_at\_2.00.19\_PM.png%22\)%7D)

## **Verifying your Contracts on PolygonScan**

The first and foremost step is to flatten the solidity contract into a single file.

### **Flatten your solidity contract**

Install [truffle-flattener](https://github.com/nomiclabs/truffle-flattener) or [sol-merger](https://github.com/RyuuGan/sol-merger)

Flatten using command

`sol-merger \"./contracts/*.sol\" ./build`

### **Verifying on Polygonscan**

Navigate to your contract's polygonscan page and then click verify and publish

\<img src={useBaseUrl("img/verification/verify-publish.png")} />

* Select `Solidity (Single File)` in compiler type
* Select appropriate compiler version
* Choose the license type of your contract

Onto the next section, paste your flattended contract here.

If you had enabled optimization then adjust the `optimization` section accordingly.

Constructor arguments should have been filled in automatically, if not, they can be retrieved from the trailing bytes of the deployment transaction, they resemble something like `000000000000000000000000a6fa4fb5f76172d178d61b04b0ecd319c5d1c0aa`

That's it, you are done. 🎉
