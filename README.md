# DeFi Stablecoin Project

📜 **Description**  

The DeFi Stablecoin Project is a decentralized finance (DeFi) protocol built to create a stablecoin pegged to a specific value, using collateralized assets. The protocol enables users to mint, redeem, and manage stablecoins while maintaining the system's stability. Built using Solidity and OpenZeppelin's secure and efficient contracts, this project offers features like collateral management, minting, and burning of stablecoins, along with a robust governance system to ensure decentralized decision-making.

🚀 **Features** 
 
- Mint and burn stablecoins with collateral
- Overcollateralization mechanism to ensure stability
- OpenZeppelin's ERC20 token standard for stablecoin issuance
- Full contract tests to ensure functionality and security
- Integration with price oracles for real-time price data and stability

📂 **Updates**  

The latest version of openzeppelin-contracts has changes in the ERC20Mock file. To follow along with the course, you need to install version 4.8.3 which can be done by forge install openzeppelin/openzeppelin-contracts@v4.8.3 --no-commit instead of forge install openzeppelin/openzeppelin-contracts --no-commit
Usage
Start a local node
make anvil

**Deploy** 

This will default to your local node. You need to have it running in another terminal in order for it to deploy.

make deploy

**Testing** 

We talk about 4 test tiers in the video.

Unit
Integration
Forked
Staging
In this repo we cover #1 and Fuzzing.

forge test
Test Coverage
forge coverage
and for coverage based testing:

forge coverage --report debug

**Deployment to a testnet or mainnet** 

Setup environment variables
You'll want to set your SEPOLIA_RPC_URL and PRIVATE_KEY as environment variables. You can add them to a .env file, similar to what you see in .env.example.

PRIVATE_KEY: The private key of your account (like from metamask). NOTE: FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
You can learn how to export it here.
SEPOLIA_RPC_URL: This is url of the sepolia testnet node you're working with. You can get setup with one for free from Alchemy
Optionally, add your ETHERSCAN_API_KEY if you want to verify your contract on Etherscan.

Get testnet ETH
Head over to faucets.chain.link and get some testnet ETH. You should see the ETH show up in your metamask.

Deploy
make deploy ARGS="--network sepolia"

**Scripts**

Instead of scripts, we can directly use the cast command to interact with the contract.

For example, on Sepolia:

Get some WETH
cast send 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 "deposit()" --value 0.1ether --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
Approve the WETH
cast send 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 "approve(address,uint256)" 0x091EA0838eBD5b7ddA2F2A641B068d6D59639b98 1000000000000000000 --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
Deposit and Mint DSC
cast send 0x091EA0838eBD5b7ddA2F2A641B068d6D59639b98 "depositCollateralAndMintDsc(address,uint256,uint256)" 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 100000000000000000 10000000000000000 --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
Estimate gas
You can estimate how much gas things cost by running:

forge snapshot
And you'll see an output file called .gas-snapshot

**Formatting**

To run code formatting:

forge fmt
Slither
slither :; slither . --config-file slither.config.json
Additional Info:
Some users were having a confusion that whether Chainlink-brownie-contracts is an official Chainlink repository or not. Here is the info. Chainlink-brownie-contracts is an official repo. The repository is owned and maintained by the chainlink team for this very purpose, and gets releases from the proper chainlink release process. You can see it's still the smartcontractkit org as well.

https://github.com/smartcontractkit/chainlink-brownie-contracts

**License**

This project is licensed under the MIT License.

💡 **Feel free to fork and modify this project for your needs!**