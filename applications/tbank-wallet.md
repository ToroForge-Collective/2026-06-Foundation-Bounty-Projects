# 📝 ToroBank (TBank)

## 🌟 Project Overview

**Tagline:** A gorgeous, decentralized Flutter wallet for Toronet that natively integrates fiat and crypto, serving as a central payment provider for any e-commerce store via deep linking.

**Project Description:** 
ToroBank is a fully-featured, decentralized Web3 wallet built entirely in Flutter. It eliminates the need for raw backend code or direct private key management by leveraging the Toronet SDK and a secure PIN-based signing system. It natively fetches user balances (like USD, Naira, and ToroG), executes cross-chain bridges seamlessly, and uses deep linking (`torobank://sign-tx`) to intercept transaction requests from external web stores, instantly transforming the app into a payment approval gateway.

**Toronet Ecosystem Integration:** 
It natively utilizes the `toronet` Flutter SDK (`ToronetClient`) and raw Toronet Node APIs via `dio` to query balances, resolve Toronet Name Service (TNS) usernames, and execute peer-to-peer token transfers. The application demonstrates how to auto-enroll users on the Toronet testnet and securely manage cross-currency settlements.

**Why we are interested:** 
We built ToroBank to prove that developing on Web3 doesn't have to be complex. We wanted to eliminate the steep learning curves and demonstrate that developers can build powerful, user-friendly decentralized financial tools and web store integrations using regular fiat currencies.

# **Demo(the walkthrough):** 

[![TBank Video](https://img.youtube.com/vi/gjupv7sZ54Y/0.jpg)](https://youtu.be/gjupv7sZ54Y)

### ***the deeplink payment preview***
[![TBank Video](https://img.youtube.com/vi/rq2wyV3MVis/0.jpg)](https://youtu.be/rq2wyV3MVis)

### ***X post : https://x.com/thetechyxander/status/2063509250014351651?s=20***
[![Check out the update on X](https://pbs.twimg.com/ext_tw_video_thumb/2063509198806130688/pu/img/349gClFVDh0LHGLH?format=jpg&name=120x120)](https://x.com/thetechyxander/status/2063509250014351651?s=20)



**Related Repositories:**
- **T-store (Test Web Store):** https://github.com/xanderelsmith/T-store (Demonstrates the e-commerce deep-link checkout flow connected to ToroBank)

here: https://t-store-umber.vercel.app/
---

## 🔍 Project Details

**Technology Stack:**
- **Frontend/Mobile:** Flutter, Dart
- **Blockchain SDK:** `toronet` Flutter SDK, Dio for raw Toronet Node API access
- **Deep Linking:** `app_links` to intercept custom schemas
- **Architecture:** Feature-first Clean Architecture (Data, Domain, Presentation layers)

**Core Architecture & Infrastructure:**
- **Dashboard Layer:** Fetches and maps real-world fiat and crypto balances in a single API call using Toronet's unified ledger.
- **Transfer Layer:** Manages peer-to-peer transfers using a secure PIN instead of raw private keys. Handles Toronet Name Service (TNS) resolution for human-readable addresses.
- **Deep Link Interception:** Listens to `torobank://sign-tx` payloads from external Web Stores, parses transaction parameters, and opens a transaction approval screen. Once the user signs the transaction with their PIN, ToroBank triggers a callback URL to the web store with the transaction hash for order fulfillment.

**What your project will NOT provide:**
- We do not provide an exhaustive backend indexer, relying purely on the decentralized Toronet node ledger.

---

## 🧩 Ecosystem Fit

**Fit in the Toronet Ecosystem:** 
ToroBank acts as both a consumer-facing app and essential platform infrastructure. It serves as the critical bridge between end-users holding Toronet assets and decentralized applications or web stores wanting to accept Web3 payments.

**Target Audience:** 
- Everyday Developers that want to speed up  their development with toronet and looking for a real application
- Everyday consumers who want a beautiful, simple interface for their assets, and merchants looking for a frictionless way to accept Toronet payments without forcing users to interact with complex browser extensions.

**Problems Solved:**
- Abstracts away complex smart contracts for simple P2P transfers.
- Replaces scary private key management with secure PINs.
- Enables seamless checkout for external stores via deep-link payment routing, completely bypassing traditional payment gateways like Apple Pay.

**Similar Projects:** 
While other wallets exist, ToroBank provides a native, highly aesthetic Flutter implementation specifically optimized for developer infrastructure—demonstrating how any app can become a central payment provider for the Toronet ecosystem.

---

# 👥 Team

- **Team Name:** TBank
- **Contact Name:** Emmanuel Onyeji (xander)
- **Contact Email:** Xanderelsmith@gmail.com
- **Website/GitHub:** https://github.com/xanderelsmith/tbank

---

## Team Members
- Emmanuel Onyeji (xander)

### LinkedIn Profiles (if available)
 - https://www.linkedin.com/in/emmanuel-onyeji-a09705231/
