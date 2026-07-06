# 📝 Toronet Backend Starter Kit

> **🏗️ Builder Bounty Project** — This application is submitted under the **Builder Bounty** track of the June 2026 Bounty Program.

## 🌟 Project Overview

**Tagline:** A production-grade Node.js/TypeScript backend starter kit with deep Toronet blockchain integration, custom custodial TORO transfer, and verifiable on-chain proof.

**Description:** The Toronet Backend Starter Kit wraps `torosdk` v0.2.0 into a clean Express REST API with full type safety, strict input validation, classified error handling, and an offline-testable test suite. It exposes 9 service modules — Wallet, Blockchain, Balance, TNS, KYC, Currency, Bridge, Products, and Deployer — plus a custom custodial TORO transfer path that fills a gap in the base SDK.

**Toronet integration:** Every core SDK function is exposed through REST endpoints with consistent response shapes. Beyond the base SDK, the project discovered that `torosdk` v0.2.0 ships with incorrect default API endpoints — the real testnet lives at `https://testnet.toronet.org/api` (chain 54321), not the SDK defaults. This discovery is documented with a full root-cause analysis, balance timeline, and regression test guard.

**Demo video:** https://youtu.be/g9SuSx73NRQ

**Why we built this:** When starting Toronet development, we found the SDK's default URLs pointed to wrong endpoints, the TORO token had no transfer method in the SDK, and there was no production-grade backend starter to build on. This project solves all three: it documents the real network topology, implements the missing TORO transfer, and provides a fully-tested, CI-verified backend template.

---

## 🔍 Project Details

**Technology stack:**
- TypeScript 5.x (strict mode)
- Node.js, Express 4.x
- Pino (structured logging)
- Vitest (testing, 118 tests across 5 files)
- Supertest (HTTP integration tests)
- ESLint flat config
- `torosdk` v0.2.0 (upstream)
- Axios (custom TORO API calls)
- GitHub Actions CI (Node 20/22)

**Core architecture:**

```
src/
├── config/env.ts        — environment validation (Zod)
├── index.ts             — Express app setup, middleware, routes
├── main.ts              — server entry point
├── middleware/
│   └── error-handler.ts — classified error handling (400/502/500)
├── routes/              — 10 route files, all using asyncWrap + sendSuccess
│   ├── wallet.routes.ts
│   ├── blockchain.routes.ts
│   ├── balance.routes.ts
│   ├── currency.routes.ts   — includes custom /toro/transfer and /toro/import-key
│   ├── tns.routes.ts
│   ├── kyc.routes.ts
│   ├── bridge.routes.ts
│   ├── products.routes.ts
│   ├── deployer.routes.ts
│   └── index.ts
├── sdk/                 — SDK wrapper layer
│   ├── currency.ts      — custom transferToro() and importWalletKey() with strict validation
│   ├── client.ts        — SDK init
│   └── ...
├── types/errors.ts      — ValidationError (400), SdkError (502), ToronetError base
└── utils/
    ├── response.ts      — sendSuccess / sendError helpers
    └── logger.ts        — Pino logger
```

**Key architectural decisions:**

1. **Thin route layer** — Routes are thin wrappers that validate input, call SDK functions, and return consistent responses. Business logic lives in the SDK layer.

2. **Strict input validation** — Address format (`/^0x[a-fA-F0-9]{40}$/`), private key format (`/^0x[a-fA-F0-9]{64}$/`), positive amount checks. Validation errors return 400, upstream failures return 502.

3. **Classified error handling** — `ValidationError` (400) vs `SdkError` (502) vs unhandled (500). Every route uses `asyncWrap` for consistent error propagation.

4. **Custom TORO transfer** — The SDK has no `transferToro()` method. This project implements it via a custodial POST to `/api/token/toro/cl` with keystore key import, strict validation, and optional tx hash lookup.

5. **Network topology regression guard** — A dedicated test file (`tests/network-topology.test.ts`) ensures the correct API base URL is never reverted to the wrong SDK defaults.

6. **Live proof script** — `scripts/verify-live-proof.ts` checks 8 live endpoints with categorized results (PASS, EXPECTED_DOMAIN_ERROR, REQUIRES_CREDENTIALS, UPSTREAM_FAILURE, FAIL) and a double-gate safety mechanism (`LIVE_PROOF_TRANSFER=1` + `--transfer` flag).

**What this project does not provide:**
- A frontend or mobile UI — this is purely a backend API
- Smart contract deployment tooling (the SDK's deployContract has upstream Prisma issues)
- Mainnet support (no public mainnet REST API exists — documented in ROOT_CAUSE.md)
- A UI dashboard — developers build their own frontend on top of the API

**Prior work:** The project is complete with a live on-chain verified TORO transfer (tx `0xad4ef...52071`) and a 300 TORO mint (tx `0x0895...2919`). Full documentation at `ROOT_CAUSE.md`, `LIVE_VERIFIED_FLOWS.md`, `docs/WALLET_BALANCE_DISCREPANCY.md`, `SUBMISSION.md`, and `docs/openapi.yaml`.

---

## 🧩 Ecosystem Fit

**Where it fits:** Developer tooling / infrastructure. This starter kit is the Node.js equivalent of what `wagmi` is for Ethereum — a production-grade backend template that handles the plumbing (configuration, validation, error handling, testing, CI) so developers can focus on their Toronet application logic.

**Target audience:** Node.js and TypeScript developers building Toronet applications — both indie developers and teams needing a reliable backend foundation.

**Problems solved:**
- **No production-grade backend starter for Toronet** — existing resources are minimal
- **Incorrect SDK default URLs** — the real testnet API was discovered and documented
- **No TORO transfer method in the SDK** — implemented as a custom custodial path
- **No CI pipeline** — `verify:repo` script and GitHub Actions provided
- **No API contract** — `docs/openapi.yaml` provides the spec
- **No regression protection** — network topology tests guard against URL drift

**Similar projects:** No equivalent production-grade backend starter exists in the Toronet ecosystem. The closest analogue is `torosdk-expo` (another bounty submission) which targets React Native mobile — this project targets Node.js/Express backend servers. Together they cover both the server and mobile client sides of Toronet development.

---

# 👥 Team

- **Team Name:** yeziR4
- **Contact Name:** yeziR4
- **Contact Email:** [available upon request]
- **Website:** https://github.com/yeziR4

---

## Team Members

yeziR4 — sole contributor

### LinkedIn Profiles (if available)

N/A

---

## Team Code Repositories

- https://github.com/yeziR4/toronet-backend-starter (this project)

Team member GitHub accounts:
- https://github.com/yeziR4

---

## Team Experience

- **Blockchain development:** Deep Toronet ecosystem exploration including network topology discovery (correct API endpoint at chain 54321 vs incorrect SDK defaults), custom custodial TORO transfer implementation, live on-chain transaction execution (mint + transfer verified).
- **Product development:** Full-stack TypeScript/Node.js development with Express, middleware architecture, structured logging, error classification, and CI/CD pipelines.
- **Open-source contributions:** This project is open-source (MIT licensed) with comprehensive documentation and a reviewer-friendly live proof script.
- **Technical expertise:** TypeScript strict mode, Express route architecture, Vitest testing patterns, Zod environment validation, Pino structured logging, GitHub Actions.

---

# 📊 Development Status

The project is **complete and production-ready.** All planned features have been implemented and verified against the live testnet.

**Repository:** https://github.com/yeziR4/toronet-backend-starter

**Current implementation status:**

| Area | What's delivered | Evidence |
|------|-----------------|----------|
| REST API | 9 service modules, 10 route files, consistent response shapes | `src/routes/` |
| Custom TORO transfer | `transferToro()` + `importWalletKey()` with strict validation | `src/sdk/currency.ts` |
| Error handling | Classified ValidationError (400) / SdkError (502) | `src/types/errors.ts` |
| Testing | 118 tests, 5 files, all mocked + deterministic | `pnpm test` |
| CI | GitHub Actions + `verify:repo` script | `.github/workflows/ci.yml` |
| Live proof | Categorized script with dry-run and double-gate safety | `scripts/verify-live-proof.ts` |
| API contract | OpenAPI 3.0 spec | `docs/openapi.yaml` |
| Network topology | Regression guard tests | `tests/network-topology.test.ts` |
| Documentation | ROOT_CAUSE, LIVE_VERIFIED_FLOWS, WALLET_BALANCE_DISCREPANCY, SUBMISSION | `docs/` |
| Demo video | Walkthrough of code, verification, and live proof | https://youtu.be/g9SuSx73NRQ |

---

# 📅 Development Roadmap

## Overview

- **Estimated Duration:** Completed (all milestones delivered)
- **Full-Time Equivalent (FTE):** 1 contributor

---

| # | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | README with network topology warning, balance timeline, feature table, bounty checklist; ROOT_CAUSE.md with full investigation; LIVE_VERIFIED_FLOWS.md with wallet/token findings; docs/WALLET_BALANCE_DISCREPANCY.md with resolution; docs/openapi.yaml with 7-endpoint OpenAPI spec |
| 0c. | Testing and Testing Guide | 118 tests across 5 files (integration: 61, routes: 34, sdk: 13, wallet: 7, network-topology: 3). Run `pnpm test` or `pnpm run verify:repo` (typecheck+build+test+lint) on a fresh clone with zero network dependency |
| 0d. | Article / Report | SUBMISSION.md — 820-word technical report covering network discovery, custom TORO path, engineering quality, live proof, and risks |
| 1. | Core REST API | 10 route files covering 9 service modules with asyncWrap, sendSuccess, classified error handling, and consistent response shapes |
| 2. | Custom TORO transfer | `transferToro()` and `importWalletKey()` with strict address/amount validation, ToroTransferResult/WalletKeyResult return types, error classification, and optional tx hash lookup |
| 3. | Network topology guard | `tests/network-topology.test.ts` with 3 regression tests (env config shape, URL construction pattern, SDK init passthrough) using dedicated `vi.mock("torosdk")` |
| 4. | Live verification script | `scripts/verify-live-proof.ts` with 8 categorized checks, dry-run mode, credential presence check, double-gate transfer safety, and balance timeline |
| 5. | CI pipeline | GitHub Actions with Node 20/22, pnpm v10, running typecheck+build+test+lint; `verify:repo` script for local verification |

---

# 🔮 Future Plans

**Post-bounty development:**
- Maintain compatibility with future `torosdk` releases as the SDK evolves
- Add support for mainnet when a public Toronet mainnet REST API becomes available
- Expand test coverage to additional edge cases and integration scenarios

**Long-term vision:**
- Become the standard Node.js backend starter for Toronet development
- Support community contributions and pull requests
- Continue documenting Toronet network topology as it changes

---

# ℹ️ Additional Information

**Live on-chain proof:**
- 300 TORO minted: tx `0x0895534d3788d7ee058ebad5da4d903358736d04b751d6457fec936402312919`
- 1 TORO transferred: tx `0xad4ef61bf2606f95018750247941341c8afeb88b5090c249faf8269f7b852071`
- Current sender balance: 299 TORO
- Current recipient balance: 1 TORO
- All verified via `scripts/verify-live-proof.ts --dry-run`

**Key discovery:** The `torosdk` v0.2.0 default URLs are incorrect. The real testnet API is at `https://testnet.toronet.org/api` (chain 54321). This is documented in full in `ROOT_CAUSE.md` with a balance timeline and regression test guard.
