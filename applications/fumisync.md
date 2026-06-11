# FumiSync: Unified Healthcare Operations and Toronet Billing Infrastructure

> Builder Bounty Project - This application is submitted under the June 2026 Bounty Program.

## Project Overview

**Tagline:** A healthcare operations backend that connects fragmented clinic workflows with auditable sync infrastructure, workspace management, and Toronet-powered billing wallets.

**Description:** FumiSync is a backend infrastructure project for dental and healthcare operations teams that need to coordinate data across PMS/EHR-style systems, CRMs, billing workflows, team workspaces, premium service billing, and automation pipelines. The current implementation provides a FastAPI backend for clinic/DSO registration, role-based workspace access, CRM webhook ingestion, sync log visibility, ToroForge wallet creation, KYC submission, wallet funding, ledger entries, and DSO-to-clinic wallet transfers.

Healthcare teams often operate across fragmented systems: patient data may live in one platform, appointment events in another, CRM automations in another, and billing operations in yet another. FumiSync is designed as the backend layer that preserves operational meaning while these systems exchange data.

**Toronet integration:** FumiSync integrates with ToroForge/Toronet services for wallet provisioning, TNS registration, KYC, wallet funding, balance verification, and DSO-to-clinic wallet transfers. The project uses Toronet-backed wallet operations to support real-world clinic billing workflows, including treasury-style DSO wallets, clinic wallets, auditable ledger entries, idempotent funding flows, internal wallet transfers, and wallet-based access to premium healthcare operations services.

**Premium service billing model:** Clinics and DSOs can fund their FumiSync wallets and use the wallet balance to pay for premium operational services such as insurance eligibility checks, patient messaging, appointment reminders, AI-assisted patient calls, and other automation services. When a clinic uses a billable service, FumiSync can debit the clinic wallet automatically, record the service type, store the usage metadata, and create an auditable ledger entry. This makes premium healthcare workflow automation easier to meter, reconcile, and control across standalone clinics and DSO-managed clinics.

**Why we are building this:** Healthcare interoperability is usually discussed at the standards layer, but clinic operations break at the workflow layer. Teams need systems that can handle identity, roles, retries, partial failures, duplicate prevention, audit trails, and billing state. FumiSync is being built to make healthcare operational data and payment workflows more consistent, recoverable, and useful.

---

## Project Details

**Technology stack:**

- Python 3.x
- FastAPI
- SQLAlchemy
- Alembic migrations
- PostgreSQL
- Redis/RQ-ready worker infrastructure
- Pydantic v2
- OAuth2/JWT authentication
- Role-based access control for DSO and clinic workspaces
- ToroForge/Toronet API integrations
- HTTPX async upstream clients

**Core architecture:**

```txt
FumiSync API
  |
  |-- API routers
  |     |-- user, DSO, clinic registration
  |     |-- workspace and team access
  |     |-- CRM webhook ingestion
  |     |-- sync log visibility
  |     |-- ToroForge wallet endpoints
  |
  |-- Service layer
  |     |-- wallet provisioning
  |     |-- KYC submission/status
  |     |-- wallet funding verification
  |     |-- DSO-to-clinic wallet transfer
  |
  |-- ToroForge clients
  |     |-- keystore
  |     |-- TNS
  |     |-- KYC
  |     |-- payment/funding
  |     |-- wallet transfer
  |
  |-- Database models
        |-- users, DSOs, clinics
        |-- role assignments and invites
        |-- sync logs
        |-- wallets, ledger entries, transfers, payment transactions
```

**Current implementation status:**

- User registration and authentication flow
- DSO and clinic registration
- Role assignments for DSO/clinic access
- Team and workspace endpoints
- CRM webhook configuration and ingestion
- Sync log listing, detail view, and streaming endpoints
- ToroForge wallet creation for standalone clinics, DSO clinics, and DSO treasury wallets
- Wallet password rotation
- KYC submission and KYC status endpoints
- Wallet funding initialization and deposit verification
- Balance-aware funding verification logic
- Wallet ledger entries for top-ups and transfers
- DSO-to-clinic wallet transfer service and API endpoint
- Circuit-breaker-aware ToroForge HTTP client

**How clinics use the wallet flow:**

1. A standalone clinic or DSO-managed clinic creates a FumiSync wallet through ToroForge.
2. The clinic completes KYC and funds the wallet.
3. The clinic uses premium services such as eligibility checks, patient messaging, appointment reminders, or AI-assisted calls.
4. Each premium service usage can be priced, debited from the wallet, and stored as a ledger entry.
5. Clinic owners and DSO admins can review wallet funding, service usage, transfer history, and billing activity from one operational backend.

**Data models / API surface:**

Key models include:

- `Users`
- `Dso`
- `RegisteredClinics`
- `RoleAssignment`
- `MemberInvite`
- `AppointmentSyncLog`
- `Wallet`
- `WalletCreationRequest`
- `WalletLedgerEntry`
- `WalletTransfer`
- `PaymentTransaction`

Key ToroForge endpoints include:

- `POST /toroforge/clinics/{clinic_id}/wallet`
- `POST /toroforge/dsos/{dso_id}/wallet`
- `POST /toroforge/dsos/{dso_id}/clinics/{clinic_id}/wallet`
- `POST /toroforge/wallets/{wallet_id}/kyc`
- `GET /toroforge/wallets/{wallet_id}/kyc-status`
- `POST /toroforge/wallets/{wallet_id}/funding`
- `POST /toroforge/wallets/{wallet_id}/funding/{payment_transaction_id}/verify-deposit`
- `POST /toroforge/dsos/{dso_id}/clinics/{clinic_id}/wallet-transfer`

**Scope boundaries:**

- The backend is the primary bounty deliverable, but the existing frontend can be shared as supporting demo code/reviewer context
- Direct clinical diagnosis or treatment decision support
- Custodial financial advice or investment features
- FHIR/HL7 production gateway implementation in the first bounty milestone
- Production PHI hosting without a deployment-specific compliance review

---

## Ecosystem Fit

**Where it fits:** FumiSync fits into the Toronet ecosystem as real-world healthcare payment and operations infrastructure. It demonstrates how Toronet/ToroForge wallet services can power practical business workflows beyond generic wallet demos: clinic funding, DSO treasury management, KYC-gated wallets, and internal clinic transfers backed by an auditable ledger.

**Target audience:**

- Dental service organizations
- Multi-location clinics
- Healthcare operations teams
- Clinic billing administrators
- Healthtech builders integrating PMS/EHR workflows with payments
- Developers building real-world utility on Toronet/ToroForge

**Problems solved:**

- Fragmented clinic data across PMS/EHR, CRM, billing, and internal tools
- Lack of auditability in operational sync and billing workflows
- Manual clinic wallet funding and reconciliation
- Manual billing for premium services such as eligibility checks, patient messaging, appointment reminders, and AI-assisted calls
- Missing role-aware DSO/clinic workspace infrastructure
- Need for Toronet wallet use cases tied to real-world business operations
- Duplicate/unsafe payment state transitions without idempotency and ledger records

**Similar projects:** We are not aware of a Toronet ecosystem project focused specifically on healthcare operations, clinic workspace management, sync auditability, and DSO/clinic wallet infrastructure. FumiSync is different because it combines healthcare workflow context with Toronet-backed wallet and ledger operations.

---

# Team

- **Team Name:** FumiSync
- **Contact Name:** Ayomide Ganiyu
- **Contact Email:** Ganiyuaa2019@gmail.com
- **Website:** https://github.com/FunmiSync

---

## Team Members

- Ayomide Ganiyu

### LinkedIn Profiles (if available)

- https://www.linkedin.com/in/ayomide-ganiyu-52658824b

---

## Team Code Repositories

- https://github.com/FunmiSync/FunmiSync-Dental-Solution-
- https://github.com/AYTIPS/unified-dental-data-layer

## Demo Access

- Live Frontend Demo: https://fumisync-project.vercel.app/
- Backend Repository: https://github.com/FunmiSync/FunmiSync-Dental-Solution-

Please also provide the GitHub accounts of all team members:

- https://github.com/AYTIPS

---

## Team Experience

The FumiSync team has experience building backend systems for healthcare operations, CRM/PMS synchronization, role-based workspace management, webhook ingestion, billing workflows, and ToroForge/Toronet wallet integrations. The current backend demonstrates practical engineering around authentication, encrypted secrets, DSO/clinic access control, idempotent payment flows, wallet ledger entries, upstream API clients, and audit-friendly operational records.

---

# Development Status

Development has already started.

**Repository links:**

- https://github.com/FunmiSync/FunmiSync-Dental-Solution-
- https://github.com/AYTIPS/unified-dental-data-layer

**Current implementation status:**

| Area | Status |
| ---- | ------ |
| FastAPI backend foundation | Implemented |
| Authentication and user registration | Implemented |
| DSO/clinic registration | Implemented |
| Role-based access control | Implemented |
| Workspace and team endpoints | Implemented |
| Webhook configuration and CRM ingestion | Implemented |
| Sync log list/detail/stream endpoints | Implemented |
| ToroForge wallet creation | Implemented |
| ToroForge KYC submission/status | Implemented |
| Wallet funding initialization | Implemented |
| Wallet funding verification | Implemented |
| Wallet ledger entries | Implemented |
| DSO-to-clinic wallet transfer | Implemented |
| Consumer/demo frontend | Existing; can be shared as reviewer context |
| Premium service wallet debit model | Planned bounty hardening |
| Setup documentation and deployment guide | Planned |
| Automated tests and reviewer guide | Planned |
| Demo environment or recorded walkthrough | Planned |

---

# Development Roadmap

## Overview

- **Estimated Duration:** 8 weeks
- **Full-Time Equivalent (FTE):** 1 contributor

---

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT license |
| 0b. | Documentation | Add a complete `README.md` with local setup, environment variables, database migration steps, API usage, ToroForge configuration, and deployment guidance |
| 0c. | Testing and Testing Guide | Add focused tests and a reviewer guide covering wallet creation, KYC, funding initialization, deposit verification, wallet transfer, RBAC checks, and sync log endpoints |
| 0d. | Article / Report | Publish a technical report explaining how FumiSync uses Toronet/ToroForge wallet infrastructure for healthcare operations and clinic billing workflows |
| 1. | Backend cleanup and public readiness | Remove environment-specific assumptions, document required secrets, verify `.env` is not tracked, add setup scripts or clear commands, and ensure the repository can be reviewed cleanly |
| 2. | ToroForge wallet and ledger hardening | Finalize DSO treasury wallet, clinic wallet, KYC, funding, balance verification, transfer, and ledger workflows with idempotency and error-handling documentation |
| 3. | Premium service wallet debits | Define billable service events for eligibility checks, patient messaging, appointment reminders, and AI-assisted calls; debit funded clinic wallets automatically; record service usage and ledger entries for reconciliation |
| 4. | Reviewer demo flow | Provide a seeded or documented test flow: create DSO, create clinic, create wallets, submit KYC payload, initialize funding, verify deposit, transfer funds from DSO wallet to clinic wallet, trigger a sample premium service debit, and inspect ledger records |
| 5. | API documentation | Provide endpoint documentation with request/response examples for workspace, sync log, wallet creation, KYC, funding, transfer, and premium service debit endpoints |
| 6. | Deployment guide | Provide Docker or cloud deployment guidance, including database migrations, environment variables, CORS, secrets, and recommended production boundaries |

---

# Future Plans

After the bounty, FumiSync will continue toward a broader healthcare interoperability platform. Planned work includes:

- More complete CRM/PMS sync adapters
- FHIR/HL7-aware mapping layer for healthcare data exchange
- Frontend dashboard for DSO and clinic operations
- Deeper audit and reconciliation tooling
- Notification workflows for patient and clinic communication
- Wallet-metered premium services for eligibility checks, patient messaging, appointment reminders, and AI-assisted patient calls
- Production deployment hardening
- Expanded Toronet/ToroForge use cases for clinic payments, billing automation, and settlement workflows

Long term, FumiSync aims to become a reliable backend layer for healthcare operations teams that need workflow-aware interoperability and real-world payment infrastructure.

---

# Additional Information

FumiSync is motivated by a practical healthcare infrastructure problem: clinics do not only need data movement; they need meaning-preserving workflow coordination. Appointment data, patient records, CRM events, billing state, KYC status, wallet funding, and internal transfers all need to be traceable and recoverable.

This project contributes to the Toronet ecosystem by showing a real-world utility path for ToroForge wallet infrastructure in healthcare operations, especially for DSO-to-clinic financial workflows and auditable billing records.

**Requested bounty / budget:** $500
