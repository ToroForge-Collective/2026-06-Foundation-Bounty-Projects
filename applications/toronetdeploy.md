# toronetdeploy

## 🌟 Project Overview

**toronetdeploy** is a CLI tool and Node.js library for deploying Solidity smart contracts to the ToroNet blockchain.

Deploying smart contracts to ToroNet involves conventions and network-specific requirements — such as enforcing the `Ownable` pattern and passing an explicit owner address — that standard EVM deployment tools do not handle out of the box. toronetdeploy was built specifically to make this process simple and repeatable. Developers can invoke a single command and have their contract compiled and deployed to ToroNet testnet or mainnet, with deployment metadata automatically saved to disk.

The tool integrates directly into Foundry-based workflows, acts as the deployment layer in projects like [Scaffold Toro](https://github.com/toronet-guidl/scaffold-toro-app), and is available both as a CLI (`npx toronetdeploy`) and as a programmatic Node.js library (CommonJS and ESM).

I built toronetdeploy because there was no dedicated deployment tool for ToroNet when I started building on the network. Every developer was navigating the same low-level steps manually. Having a focused, zero-friction deployment CLI removes that barrier and lets developers spend their time on what actually matters — writing contracts and building applications.

---

## 🔍 Project Details

### Technology Stack

- **Runtime:** Node.js (CommonJS + ESM dual module support)
- **Distribution:** npm package, invocable via `npx` without a global install
- **Contract Compilation:** Foundry (`forge build`) — the tool compiles the target Solidity file before deployment
- **Language:** JavaScript / Node.js
- **License:** MIT

### Architecture & Core Functionality

toronetdeploy wraps the ToroNet smart contract deployment flow into a single ergonomic interface. At its core, the `deployContract()` function accepts a set of deployment parameters, compiles the specified Solidity file using Foundry tooling, and submits the deployment transaction to the ToroNet network.

**CLI usage (via npx):**

```bash
npx toronetdeploy --file contracts/MyToken.sol --contract MyToken \
  --owner 0xYourOwnerAddress --args '["0xabc...", "1000"]' --network testnet
```

**Library usage (ESM):**

```js
import { deployContract } from 'toronetdeploy';

const { address, abi } = await deployContract({
  file: 'contracts/MyToken.sol',
  contract: 'MyToken',
  owner: '0xYourOwnerAddress',
  args: ['0xabc...', '1000'],
  network: 'testnet',
});
```

**CLI Options:**

| Flag | Description |
|------|-------------|
| `--file` | Path to the Solidity source file |
| `--contract` | Name of the contract to deploy |
| `--owner` | Owner address for the deployment |
| `--args` | Constructor arguments as a JSON array or comma-separated values |
| `--network` | Target network: `testnet` (default) or `mainnet` |
| `--skip-dump` | Skip writing the deployment dump file |
| `--token` | Optional token required for mainnet deployments |

### Deployment Metadata Dumps

After every successful deployment, the tool writes two JSON files under a `deployments/` directory:

```
deployments/<chainId>-<contractName>-<unix_timestamp>.json
deployments/<chainId>-<contractName>-latest.json
```

Each dump records the deployment inputs, the deployed contract address, the ABI, and (when available) Foundry artifact metadata and source files for verification. This provides a built-in audit trail and makes it easy to reference deployed contracts in subsequent scripts or front-end integrations.

### Prior Work & References

- **npm package:** https://www.npmjs.com/package/toronetdeploy
- **Repository:** https://github.com/toronet-guidl/toronetdeploy
- **Tutorial article:** https://medium.com/@nwaforemmanuel005/building-on-toronet-with-toronetdeploy-5937e0e2aea0
- **Demo project:** https://github.com/Emmo00/toronet-demo

### Scope & Limitations

toronetdeploy is a deployment tool, not a full development framework. It does not:

- Provide a local development node or simulation environment
- Handle contract upgrades or proxy patterns
- Replace Foundry or Hardhat for testing and development
- Offer a front-end or UI component

---

## 🧩 Ecosystem Fit

### Where It Fits

toronetdeploy sits at the critical last step of the smart contract development lifecycle on ToroNet — the deployment step. It is the bridge between a developer's local Foundry project and the live ToroNet network.

It is also used internally by [Scaffold Toro](https://github.com/toronet-guidl/scaffold-toro-app), the ecosystem's full-stack bootstrapping tool, which integrates toronetdeploy as part of its supported smart contract deployment flow.

### Target Audience

- Solidity developers building on ToroNet for the first time
- Existing EVM developers migrating projects or experiments to ToroNet
- Any developer using Foundry who wants to deploy contracts to ToroNet testnet or mainnet with a single command

### Problems It Solves

ToroNet has specific deployment requirements that generic EVM tools do not account for:

1. **The `Ownable` convention** — every ToroNet contract is expected to inherit an ownership trait, and the deployment flow requires an explicit owner address to be passed.
2. **Network configuration** — developers need to know the correct RPC endpoints, chain IDs, and token requirements for ToroNet testnet and mainnet.
3. **No existing deployment CLI** — before toronetdeploy, there was no dedicated tool for deploying to ToroNet. Developers had to piece together raw scripts or adapt other tools manually.

toronetdeploy removes all of these friction points with a single command.

### Existing Alternatives

At the time this project was built, there were no existing tools within the Toronet ecosystem that provided a dedicated, streamlined deployment CLI for smart contracts. This gap is what motivated the project.

---

# 👥 Team

- **Team Name:** Toronet Guidl
- **Contact Name:** Emmanuel Nwafor (Emmo00)
- **Contact Email:** nwaforemmanuel005@gmail.com
- **Website:**
  - https://github.com/emmo00
  - https://github.com/toronet-guidl/

---

## Team Members

- Emmanuel Nwafor

### LinkedIn Profiles

- https://www.linkedin.com/in/emmanuel-nwafor-53735a270/

---

## Team Code Repositories

- https://github.com/toronet-guidl/toronetdeploy
- https://github.com/toronet-guidl/scaffold-toro-app
- https://github.com/toronet-guidl/create-toro

GitHub accounts of all team members:

- https://github.com/emmo00

---

## Team Experience

Emmanuel Nwafor (Emmo00) is a Web3 full-stack software engineer with a focus on developer tooling and open-source contributions. He is the author of toronetdeploy, the creator of Scaffold Toro, and a contributor to the ToroForge collective ecosystem.

His work spans smart contract deployment infrastructure, CLI tooling, and full-stack dApp development. He has practical experience building on EVM-compatible chains and has written educational content on ToroNet development for the broader developer community.

---

# 📊 Development Status

This project is **complete**. All planned functionality has been implemented and published.

- **Repository:** https://github.com/toronet-guidl/toronetdeploy
- **npm package:** https://www.npmjs.com/package/toronetdeploy
- **Tutorial & Documentation:** https://medium.com/@nwaforemmanuel005/building-on-toronet-with-toronetdeploy-5937e0e2aea0
- **Demo project:** https://github.com/Emmo00/toronet-demo

The tool supports:
- CLI deployment via `npx toronetdeploy`
- Programmatic deployment via the `deployContract()` library export (CommonJS and ESM)
- Testnet and mainnet targets
- Deployment metadata dumps
- Constructor argument passing
- Optional token support for mainnet

---

# 📅 Development Roadmap

All milestones have been completed. The project is considered finished and no further updates are planned.

## Overview

- **Estimated Duration:** Completed
- **Full-Time Equivalent (FTE):** 1 (Emmanuel Nwafor)

---

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | README with full CLI and library usage examples: https://github.com/toronet-guidl/toronetdeploy/blob/main/README.md |
| 0c. | Testing and Testing Guide | Core deployment functionality is verifiable by running `npx toronetdeploy` against a Foundry project and confirming the contract address and deployment dump are produced |
| 0d. | Article / Report | Published tutorial article covering the full workflow from Foundry project setup to ToroNet deployment: https://medium.com/@nwaforemmanuel005/building-on-toronet-with-toronetdeploy-5937e0e2aea0 |
| 1. | CLI Tool | `npx toronetdeploy` command supporting `--file`, `--contract`, `--owner`, `--args`, `--network`, `--token`, and `--skip-dump` flags for deploying Solidity contracts to ToroNet |
| 2. | Library Interface | Programmatic `deployContract()` export supporting both CommonJS and ESM, returning the deployed contract address and ABI |
| 3. | Deployment Metadata Dumps | Automatic generation of timestamped and latest JSON dump files under `deployments/` recording deployment inputs, address, ABI, and Foundry artifact metadata |

---

# 🔮 Future Plans

This project is complete and no future updates are currently planned. The tool is stable, published to npm, and ready for use by any developer building on ToroNet.

Its role in the ecosystem is intended to remain as a foundational deployment primitive — particularly as a dependency within Scaffold Toro — ensuring that developers using that toolchain have a reliable and dedicated deployment path to ToroNet.

---

# ℹ️ Additional Information

- toronetdeploy is already integrated into [Scaffold Toro](https://github.com/toronet-guidl/scaffold-toro-app) as the recommended deployment method for smart contracts bootstrapped with the `create-toro` CLI.
- The accompanying Medium article serves as the primary educational resource and has been written to guide developers through a complete end-to-end workflow: Foundry project setup, contract writing, and ToroNet deployment.
- The demo project at https://github.com/Emmo00/toronet-demo provides a working example repository that reviewers can clone and use to validate the tool.