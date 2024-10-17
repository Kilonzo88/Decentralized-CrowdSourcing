# Decentralized Crowdsourcing Platform

## About

This project implements a decentralized crowdsourcing platform using Ethereum smart contracts. It allows users to create funding campaigns and contribute ETH to ongoing campaigns. The system uses Chainlink price feeds to ensure a minimum USD value for contributions and includes features for fund management and withdrawal.

## Key Features

- Create and manage funding campaigns
- Contribute ETH to campaigns with a minimum USD value threshold
- Automated price conversion using Chainlink oracles
- Secure fund management and withdrawal process
- Support for multiple Ethereum networks (Sepolia testnet, Mainnet, and local Anvil network)

## Getting Started

### Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Foundry](https://getfoundry.sh/)
- An Ethereum wallet (e.g., MetaMask)
- [Chainlink](https://chain.link/) Price Feed contract addresses for your chosen network

### Quickstart

1. Clone the repository:
   ```
   git clone https://github.com/your-username/crowdsourcing-platform.git
   cd crowdsourcing-platform
   ```

2. Install dependencies:
   ```
   forge install
   ```

3. Set up environment variables:
   Create a `.env` file in the root directory and add your private key and RPC URL:
   ```
   PRIVATE_KEY=your_private_key_here
   SEPOLIA_RPC_URL=your_sepolia_rpc_url_here
   ETHERSCAN_API_KEY=your_etherscan_api_key_here
   ```

4. Compile the contracts:
   ```
   forge build
   ```

5. Run tests:
   ```
   forge test
   ```

6. Deploy to a network (e.g., Sepolia testnet):
   ```
   forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
   ```

## Usage

### Creating a Campaign

To create a new funding campaign, deploy the `FundMe` contract with the appropriate price feed address for your chosen network.

### Contributing to a Campaign

Use the `fund()` function to contribute ETH to a campaign. Ensure that the value sent meets the minimum USD threshold (default is 5 USD).

### Withdrawing Funds

The contract owner can withdraw accumulated funds using either the `withdraw()` or `cheaperWithdraw()` function.

## Smart Contracts

- `FundMe.sol`: Main contract for managing funding campaigns
- `PriceConverter.sol`: Library for handling price conversions using Chainlink oracles

## Testing

The project includes a comprehensive test suite in `test/unit/FundMeTest.t.sol`. Run tests using:

```
forge test
```

For more verbose output, use:

```
forge test -vv
```

## Security Considerations

- The contract uses the `onlyOwner` modifier to restrict withdrawal access.
- Price feeds are obtained from trusted Chainlink oracles.
- Ensure proper management of the private key used for contract deployment and management.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License.
