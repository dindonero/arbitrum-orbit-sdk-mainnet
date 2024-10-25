# Arbitrum Orbit SDK (Fork)

This is a fork of the original [Arbitrum Orbit SDK](https://arbitrum.io/orbit), designed to make deploying and configuring rollups on Arbitrum One more seamless.

## Improvements

- **Mainnet Rollup Deployment**: Updated to deploy rollups directly on Arbitrum One instead of Sepolia.
- **Enhanced Config Outputs**: Generates `nodeConfig.json` and `orbitSetupScriptConfig.json` with configurations populated from `.env`, streamlining node setup.
- **Seamless Setup with Orbit Script**: New instructions for using the `orbit-setup-script` with the generated config files for quick and easy rollup deployment.

## Installation

Ensure you're using Node.js v18 or greater.

## Quick Start

### 1. Deploying a Rollup on Arbitrum One

- **Set Up Environment**: Navigate to `examples/create-rollup-eth`, and populate the `.env` file with necessary variables.
- **Install Dependencies**: Run the following command:
  ```bash
  yarn install
  ```
- **Deploy Rollup**: Execute:
  ```bash
  yarn dev
  ```
  This will deploy the rollup with ETH as the native token.

### 2. Configure Node Settings

After deploying the rollup, go to `examples/prepare-node-config`:
- **Set Up Environment**: Populate the `.env` file with necessary variables.
- **Install Dependencies**: Run the following command:
  ```bash
  yarn install
  ```
- **Deploy Rollup**: Execute:
  ```bash
  yarn dev
  ```

- This step outputs two files:
    - `nodeConfig.json` (with RPC defined from `.env`)
    - `orbitSetupScriptConfig.json`.

### 3. Complete Setup with Orbit Script

- **Clone the Orbit Setup Script**: Clone the [orbit-setup-script](https://github.com/OffchainLabs/orbit-setup-script) repository.
- **Place Config Files**: Move the generated `nodeConfig.json` and `orbitSetupScriptConfig.json` files to the `config` folder within `orbit-setup-script`.
- **Run Setup Script**: Use the command below, replacing placeholders as needed:
  ```bash
  PRIVATE_KEY="0xYourPrivateKey" L2_RPC_URL="<MAINNET_RPC_URL>" L3_RPC_URL="<L3_RPC_URL>" yarn run setup
  ```

This process finalizes the setup, allowing you to deploy and manage rollups on Arbitrum One. It also generates the `outputInfo.json`.

## Integration Tests

For testing, clone the `main` branch of [nitro-testnode](https://github.com/OffchainLabs/nitro-testnode) and run the following command:

```bash
./test-node.bash --init --tokenbridge --l3node --l3-fee-token --l3-token-bridge
```

Then, run the integration tests:

```bash
yarn test:integration
```

## Examples

See more usage examples in the [examples](./examples) folder.
