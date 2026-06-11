# 📝 toronode-backend

> **🏗️ Builder Bounty Project** — This application is submitted under the **Builder Bounty** track of the June 2026 Bounty Program.

## 🌟 Project Overview

**Tagline:** A production-structured Express.js backend API for Toronet wallet management, built as the go-to reference for Node.js developers integrating torosdk v0.2.0.

**Description:** ToroNode is a complete, test-driven backend API that wraps torosdk v0.2.0 into a clean Express.js service layer. It demonstrates how a real Node.js project should structure Toronet integration — with separate service modules for wallets, balances, deposits, KYC, TNS names, and exchange rates, all behind a consistent REST API with error handling, input validation, and a comprehensive test suite.

**Toronet integration:** torosdk v0.2.0 is the central integration in every service module. The SDK is imported in 7 service files covering the full surface area a production backend would need: wallet create/import/delete, balance queries, deposit fund/verify, KYC submission/status, TNS configure/resolve/lookup, and exchange rate fetching.

**Why we built this:** A developer who finds Toronet today has no single reference for how to integrate the JS SDK into a real backend. There is no well-structured Node.js wrapper they can study to understand service layering, error handling patterns, and test methodology. ToroNode closes that gap — it is designed to be the go-to backend reference for Toronet JS SDK integration.

---

## 🔍 Project Details

**Technology stack:**
- Node.js v18/20/22
- TypeScript 5.x (strict mode)
- Express.js 4.x with express-async-errors
- torosdk v0.2.0
- Jest 29 + ts-jest (50 tests, 15 suites)
- Winston (structured logging)
- Joi (request validation)
- pnpm (package manager)

**Core architecture:**
```
src/
├── app.ts                  # Express app setup, middleware, routes
├── server.ts               # Entry point
├── config/
│   └── sdk.ts              # torosdk initializeSDK + getSDKConfig singleton
├── middlewares/
│   ├── errorHandler.ts     # Centralized error → JSON response
│   └── auth.middleware.ts   # Api-Key + Bearer token auth
├── routes/
│   ├── index.ts            # Route aggregator
│   ├── wallet.routes.ts    # POST /wallet/create, POST /wallet/import, DELETE /wallet
│   ├── balance.routes.ts   # GET /balance/:address
│   ├── deposit.routes.ts   # POST /deposit/fund, POST /deposit/verify
│   ├── exchange.routes.ts  # GET /exchange/rates
│   ├── kyc.routes.ts       # POST /kyc/submit, GET /kyc/status/:address
│   └── tns.routes.ts       # POST /tns/configure, GET /tns/resolve/:address, GET /tns/lookup/:name
├── services/
│   ├── wallet.service.ts   # createWallet, importWallet, deleteWallet
│   ├── balance.service.ts  # getBalance (wraps torosdk getBalance)
│   ├── deposit.service.ts  # depositFunds, verifyDeposit
│   ├── exchange.service.ts # getSupportedAssetsExchangeRates
│   ├── kyc.service.ts      # performKYCForCustomer, isAddressKYCVerified
│   ├── tns.service.ts      # configureTNS, getName, getAddr
│   └── toro.service.ts     # getCurrencyBalance (ToroG)
├── utils/
│   ├── logger.ts           # Winston logger (silent in test mode)
│   └── validation.ts       # Joi schemas
└── types/
    └── index.ts            # Shared interfaces
```

**Key design decisions:**
1. **Test-driven from day one** — 50 tests covering all services with inline mock factories for torosdk, ensuring zero test pollution and fast execution.
2. **Service-layer abstraction** — Each torosdk function is wrapped in a dedicated service module with proper error translation, so route handlers never import torosdk directly.
3. **CI-ready** — GitHub Actions workflow tests on Node 18/20/22, with clean test output (no log noise, no forceExit).
4. **torosdk v0.2.0 inline mock factories** — Each test file has its own `jest.mock('torosdk', () => ({...}))` block, eliminating shared mock state entirely.

**What this project does not provide:**
- A frontend UI or wallet app (this is a backend API only)
- Smart contract deployment or interaction beyond the Toronet API surface
- Real-time event subscriptions or WebSocket support
- A mobile SDK (the existing `torosdk-expo` project covers mobile)

---

## 🧩 Ecosystem Fit

**Where it fits:** Developer tooling / infrastructure. ToroNode is a reference backend implementation that shows Node.js developers how to structure a production-quality torosdk integration.

**Target audience:** Node.js backend developers who need to integrate Toronet wallet, transfer, KYC, TNS, and exchange rate functionality into their server-side applications. This includes both indie developers and teams building Toronet-powered services.

**Problems solved:**
- **No existing backend reference for torosdk** — developers must currently figure out service layering, error handling, and testing on their own
- **Authentication done right** — Api-Key + Bearer token middleware with proper error responses
- **Test methodology** — 50 tests with inline mock factories demonstrate how to test torosdk integrations without hitting the real network
- **Clean project structure** — Separate service/routes/middleware layers make the code easy to navigate and extend

**Similar projects:** No equivalent backend reference exists in the Toronet ecosystem. The `torosdk-expo` project covers React Native mobile development; ToroNode covers the server side. Together they form a complete developer onboarding path.

---

# 👥 Team

- **Team Name:** yeziR4
- **Contact Name:** Yezir
- **Contact Email:** [available upon request]
- **Website:** https://github.com/yeziR4

Team member GitHub accounts:
- https://github.com/yeziR4

## Team Experience

- **Blockchain development:** Deep experience with Toronet ecosystem and torosdk v0.2.0 API surface, including wallet management, balance queries, deposit verification, KYC workflows, TNS operations, and exchange rate integration.
- **Backend development:** Production Node.js/TypeScript development with Express.js, including service-oriented architecture, middleware chains, input validation, structured logging, and CI/CD pipelines.
- **Testing methodology:** Jest with inline mock factories, ts-jest, async error handling patterns, and comprehensive coverage across all service layers.
- **Open source:** This project is MIT-licensed and publicly available as a community resource.

---

# 📊 Development Status

The project is **complete and production-ready.** All planned features have been implemented and tested.

**Repository:** https://github.com/yeziR4/-yeziR4-toronode

**Current implementation status (100% complete):**

| Layer | Files | Tests | Status |
|-------|-------|-------|--------|
| Config/SDK init | `config/sdk.ts` | — | ✅ Complete |
| Wallet service + routes | `services/wallet.service.ts`, `routes/wallet.routes.ts` | 7 | ✅ Complete |
| Balance service + routes | `services/balance.service.ts`, `routes/balance.routes.ts` | 4 | ✅ Complete |
| Deposit service + routes | `services/deposit.service.ts`, `routes/deposit.routes.ts` | 6 | ✅ Complete |
| KYC service + routes | `services/kyc.service.ts`, `routes/kyc.routes.ts` | 6 | ✅ Complete |
| TNS service + routes | `services/tns.service.ts`, `routes/tns.routes.ts` | 9 | ✅ Complete |
| Exchange service + routes | `services/exchange.service.ts`, `routes/exchange.routes.ts` | 4 | ✅ Complete |
| Toro service | `services/toro.service.ts` | 2 | ✅ Complete |
| Auth middleware | `middlewares/auth.middleware.ts` | 4 | ✅ Complete |
| Error handler | `middlewares/errorHandler.ts` | 2 | ✅ Complete |
| App integration | `app.ts`, `routes/index.ts` | 6 | ✅ Complete |

**Test results:** 50 tests, 15 suites, all green — verified on Node 18/20/22 via GitHub Actions CI.

**Demo video:** https://youtu.be/g9SuSx73NRQ

---

# 📅 Development Roadmap

## Overview

- **Estimated Duration:** Completed (all milestones delivered)
- **Full-Time Equivalent (FTE):** 1 contributor

---

| # | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | Comprehensive README with prerequisites, Quick Start (7 steps), API reference (16 endpoints), Testing Strategy table, project structure tree, and environment variable documentation. See `docs/PROOF.md` for verifiable evidence. |
| 0c. | Testing and Testing Guide | 50 tests across 15 suites covering all service, middleware, and route layers. Run with `pnpm test`. Test output verified clean (no encoding issues, no log noise, no `--forceExit`). See `docs/test-output.txt`. |
| 0d. | Article / Report | Demo video (https://youtu.be/g9SuSx73NRQ) and `SUBMISSION.md` with project narrative. |
| 1. | Wallet operations | POST /wallet/create, POST /wallet/import, DELETE /wallet — all backed by torosdk createWallet, importWalletFromPrivateKeyAndPassword, deleteWallet. |
| 2. | Balance queries | GET /balance/:address — wraps torosdk getBalance with proper error handling for invalid addresses. |
| 3. | Deposit workflow | POST /deposit/fund (initiate fiat deposit with admin credentials), POST /deposit/verify (verify deposit by currency + txid). |
| 4. | KYC system | POST /kyc/submit (perform identity verification), GET /kyc/status/:address (check verification status). |
| 5. | TNS operations | POST /tns/configure (set TNS name), GET /tns/resolve/:address (lookup name by address), GET /tns/lookup/:name (lookup address by name). |
| 6. | Exchange rates | GET /exchange/rates — wraps torosdk getSupportedAssetsExchangeRates. |
| 7. | CI pipeline | GitHub Actions workflow testing on Node 18, 20, 22. |

---

# 🔮 Future Plans

- Maintain compatibility with future torosdk releases
- Add WebSocket support for real-time balance updates
- Add transaction history endpoints (getAddressTransactions, getBlockById)
- Support for multi-chain bridge operations (bridgeTokenSol, bridgeTokenBase, etc.)
- Add Docker setup for one-command local development

---

# ℹ️ Additional Information

This project was built as a solo effort to create the missing backend reference for Toronet JS SDK integration. The code is original work, MIT licensed, and ready for community use. All 50 tests pass on Node 18/20/22 with zero warnings.
