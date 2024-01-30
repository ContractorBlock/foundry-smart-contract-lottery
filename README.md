# Decentralized Lottery System on Sepolia testnet

### Overview

This lottery is implemented as a smart contract on the Sepolia testnet. It leverages Chainlink's Verifiable Random Function (VRF) and was developed using the Foundry framework. This ensures equitable and transparent outcomes, standing apart from the flaws often associated with centralized alternatives. Here, decisions and money transfers occur autonomously, governed by predetermined logic that cannot be altered, rendering reliance on a central authority entirely unnecessary!

The smart contract is deployed and usable on the Sepolia testnet at this address:
[0x72F27838729ab83275265A78662F9adc290CDfD0](https://sepolia.etherscan.io/address/0x72F27838729ab83275265A78662F9adc290CDfD0#code).

## Requirements

1. **Git Installation**

   Git must be installed on your system to clone and manage the project repository. If Git is not already installed, follow the detailed installation instructions [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

2. **Foundry Installation**

   If Foundry is not already installed on your system, you can obtain it by running [this](https://getfoundry.sh/) command.

## Getting Started

Follow these steps to set up the project:

1.  **Clone the Repository:** Use the following command to create a local copy of the project on your computer:

```
git clone https://github.com/ContractorBlock/foundry-smart-contract-lottery.git

```

2. **Navigate to the Project Directory:** The following command will take you into the newly cloned project directory:

```
cd foundry/smart-contract-lottery
```

3. **Build the Project:** Finally, build the project by running the following command:

```
forge build
```

## Deploying to a Simulated Environment

To deploy the project to a simulated environment, follow the steps outlined below:

1. **Start the Anvil Chain:**
   Execute the following command to create a local testnet node that we will deploy to:

   ```
   anvil
   ```

   This command spins up a simulated blockchain environment, akin to a sandbox, where we can safely deploy and test our smart contract. Think of it as creating a miniature, self-contained Ethereum universe on your local machine.

2. **Run the Deployment Script:** Execute the following command to deploy the project onto anvil:

```
forge script script/DeployRaffle.s.sol --rpc-url http://<LOCAL_HOST_RPC_URL> --private-key <SIMULATED_PRIVATE_KEY>
```

`LOCAL_HOST_RPC_URL`: Replace this with the URL of the local host where the Anvil terminal is running. It's the address of the port that Anvil is listening to.

`SIMULATED_PRIVATE_KEY`: Replace this with any one of the private keys that the Anvil chain generates.

**Note**: Switch back to the terminal session where anvil is running to access these variables.

### Deploying to a Testnet or Mainnet

Before deploying your smart contract to a testnet or mainnet, you'll need to set up some environment variables. Follow these steps:

### Environment Variables Setup

1. Create a `.env` file in your project directory.

2. Define the following environment variables in your `.env` file:

   - `PRIVATE_KEY`: Your account's private key (e.g., from Metamask). **Note**: For development, it's crucial to use a key with no real funds associated with it.

   - `SEPOLIA_RPC_URL`: The URL of the Sepolia testnet node we are working with. You can obtain a free testnet node from [Alchemy](https://www.alchemy.com/).

### Obtaining Testnet ETH and LINK

3. The last step is to Visit [faucets.chain.link](https://faucets.chain.link) to request some testnet ETH and test LINK. This will provide you with the necessary test tokens for funding the [VRF subscription](https://docs.chain.link/vrf/v2/introduction) and for deployment. You should see the test ETH and LINK reflected in your [Metamask](https://support.metamask.io/hc/en-us/articles/360015489531-Getting-started-with-MetaMask) wallet.

## Deploy

Run the following script to deploy:

```
forge script script/DeployRaffle.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast
```

Note: This will setup a ChainlinkVRF Subscription for you. If you already have one, update it in the ` scripts/HelperConfig.s.sol` file. It will also automatically add your contract as a consumer

### Register a Chainlink Automation Upkeep

Go [here](https://automation.chain.link/new) and register a new upkeep. Choose `Custom logic` as your trigger mechanism for automation.
[Documentation](https://docs.chain.link/chainlink-automation/compatible-contracts)
