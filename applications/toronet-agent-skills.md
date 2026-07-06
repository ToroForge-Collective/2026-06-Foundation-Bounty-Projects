# ToroNet Agent Skills

## Project Overview

ToroNet Agent Skills is a collection of installable AI agent skill files that give AI coding assistants — such as Claude, GitHub Copilot, Cursor, and others — deep, accurate knowledge of the ToroNet ecosystem so they can provide better, more reliable guidance when developers build on ToroNet.

Rather than having every developer manually explain ToroNet's conventions to their AI tools on every new project, this repository provides ready-made skill files that can be installed once and immediately improve the quality of AI-assisted development across smart contract writing, contract deployment, frontend/backend integration, and SDK usage.

### How It Relates to the Toronet Ecosystem

Developers building on ToroNet increasingly rely on AI coding agents to speed up their workflows. Without ToroNet-specific context, these agents often give generic or incorrect guidance — suggesting patterns from Ethereum or other ecosystems that don't translate cleanly to ToroNet. ToroNet Agent Skills bridges that gap by giving AI agents the context they need to assist developers accurately and efficiently within the Toronet ecosystem.

### Why I'm Interested in Building This

While building other tools in the ToroNet ecosystem, I noticed that AI coding assistants were producing generic blockchain guidance that didn't account for ToroNet's specific APIs, SDK patterns, and deployment flows. Every developer has to re-explain these things to their tools, wasting time on context-setting instead of building. ToroNet Agent Skills solves this at the ecosystem level by creating a shareable, installable knowledge layer for AI agents.

---

## Project Details

### Stack

The skills in this repository are written in TypeScript-compatible formats and structured to be compatible with agent skill runners. The repository is written in TypeScript (100% of the codebase) to ensure type-safe, well-structured skill definitions.

### Skills

The repository provides four skills, each targeting a core area of ToroNet development:

- **`toronet-smart-contract-development`** — Helps AI agents assist with writing and reviewing ToroNet-compatible smart contracts. Covers ToroNet-specific patterns, conventions, and best practices that differ from other EVM-compatible chains.

- **`toronet-smart-contract-deployment`** — Provides accurate guidance on deploying contracts to ToroNet correctly. Covers deployment configuration, network settings, and tooling workflows (including compatibility with `toronetdeploy`).

- **`toronet-app-integrations`** — Guides AI agents when helping developers integrate ToroNet into frontend and backend applications. Covers wallet connections, RPC configuration, and common integration patterns.

- **`toronet-sdk`** — Helps AI agents understand ToroNet's SDK, including usage patterns, method signatures, and common implementation flows.

### Installation

Skills can be installed using any agent skills-compatible workflow:

```bash
# Install all skills
npx skills add emmo00/toronet-agent-skills

# Install a specific skill
npx skills add emmo00/toronet-agent-skills --skill toronet-smart-contract-deployment
```

### Repository

- https://github.com/toronet-guidl/toronet-agent-skills

### Scope

The objective of this project is to create accurate, up-to-date, installable AI agent skills that cover the core developer workflows on ToroNet.

This project will **not**:
- Build a standalone AI tool or chatbot
- Replace official ToroNet documentation
- Provide skills for non-ToroNet blockchains or ecosystems
- Handle runtime execution or on-chain transactions

---

## Ecosystem Fit

### Where It Fits

ToroNet Agent Skills sits at the intersection of AI tooling and developer experience within the ecosystem. It works best as a companion to other developer tools — including Scaffold Toro and `toronetdeploy` — giving developers AI assistants that are actually context-aware of the tools and patterns those projects use.

### Target Audience

Any developer building on ToroNet who uses an AI coding assistant. This includes:
- New developers exploring the ecosystem who want accurate AI guidance from day one
- Experienced ecosystem developers who want faster, more reliable AI-assisted code generation
- Teams using AI-assisted pair programming or code review workflows

### Problem It Solves

Without ToroNet-specific context, AI coding agents default to generic EVM patterns that often don't translate correctly to ToroNet. Developers waste time correcting AI suggestions or re-explaining ToroNet conventions on every session. ToroNet Agent Skills makes AI assistants reliably useful for ToroNet development from the very first install.

### Existing Alternatives

There are currently no existing installable AI agent skill collections for the ToroNet ecosystem. This project fills a gap that becomes more important as AI-assisted development becomes the norm rather than the exception.

---

# 👥 Team

- **Team Name:** Toronet Guidl
- **Contact Name:** Emmanuel Nwafor (Emmo00)
- **Contact Email:** nwaforemmanuel005@gmail.com
- **Website:**
  - https://github.com/toronet-guidl/
  - https://github.com/Emmo00/

---

## Team Members

- Emmanuel Nwafor

### LinkedIn Profiles (if available)

- https://www.linkedin.com/in/emmanuel-nwafor-53735a270/

---

## Team Code Repositories

- https://github.com/toronet-guidl/toronet-agent-skills
- https://github.com/toronet-guidl/scaffold-toro-app
- https://github.com/toronet-guidl/create-toro

Please also provide the GitHub accounts of all team members:

- https://github.com/emmo00

---

## Team Experience

Emmo00 is a Web3 full stack software engineer with experience across smart contract development, developer tooling, and open source contributions within the ToroNet ecosystem.

He is the creator of Scaffold Toro, a bootstrapping tool for full stack ToroNet applications, and `toronetdeploy`, a deployment utility for ToroNet smart contracts. ToroNet Agent Skills is his third ecosystem tooling project, and is designed to complement both of those tools by giving AI agents the context they need to use them correctly.

---

# 📊 Development Status

Development has already started.

The repository is live at https://github.com/toronet-guidl/toronet-agent-skills and contains the initial project structure and skill scaffolding. The skills directory is in place and the foundational TypeScript architecture has been set up.

The four planned skills are defined and in active development. This application is being submitted to support completing the full implementation of all four skill files with thorough content and documentation.

---

# 📅 Development Roadmap

## Overview

- **Estimated Duration:** Approximately 3–4 weeks
- **Full-Time Equivalent (FTE):** 1 (Emmo00 is the primary contributor; the project is open source and welcomes community input)

> Deliverables 0a to 0d are mandatory.

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | Inline skill documentation and a README explaining installation, usage, and how each skill helps developers on ToroNet |
| 0c. | Testing and Testing Guide | Instructions for reviewers on how to install and validate each skill in a supported agent environment, with example prompts demonstrating improved output quality |
| 0d. | Article / Report | A short write-up explaining what ToroNet Agent Skills is, how to use it, and what it improves for developers in the ecosystem |
| 1. | `toronet-smart-contract-development` skill | Complete skill file covering ToroNet-compatible smart contract writing and review patterns, including best practices, common pitfalls, and ToroNet-specific conventions |
| 2. | `toronet-smart-contract-deployment` skill | Complete skill file covering correct deployment flows to ToroNet, including network configuration, deployment scripts, and integration with `toronetdeploy` |
| 3. | `toronet-app-integrations` skill | Complete skill file covering frontend and backend integration with ToroNet, including wallet connections, RPC setup, and common integration patterns |
| 4. | `toronet-sdk` skill | Complete skill file covering ToroNet SDK usage patterns, method references, and implementation guidance |

---

# 🔮 Future Plans

### Continuing Development After the Grant

ToroNet Agent Skills is designed to be a living resource. As the ToroNet ecosystem evolves — new SDK versions, new deployment patterns, new tooling — the skills need to stay current. I plan to maintain and update the skills on an ongoing basis beyond the initial grant period.

After the grant, I plan to:

- Keep skills updated as ToroNet's SDK and tooling evolves
- Add new skills as new development patterns emerge in the ecosystem
- Gather feedback from developers using the skills to improve accuracy and coverage
- Explore integration with Scaffold Toro so that new projects can automatically prompt developers to install the relevant skills

### Funding, Partnerships, and Ecosystem Collaboration

I plan to coordinate with other ecosystem tool builders — particularly those working on developer experience — to make sure the skills stay aligned with the actual patterns developers use. As the ecosystem grows and more tooling matures, additional skills may be added to cover those tools.

### Long-Term Vision

The long-term goal is for ToroNet Agent Skills to become the default AI context layer for ToroNet development — something every developer installs alongside their development environment so their AI tools are always ToroNet-aware from day one.

Paired with Scaffold Toro and `toronetdeploy`, it contributes to a complete, AI-assisted developer experience where a developer can go from scaffolding a project to writing, reviewing, deploying, and integrating smart contracts with AI assistance that is fully grounded in accurate ToroNet knowledge.

---

# ℹ️ Additional Information

ToroNet Agent Skills is part of a broader suite of developer tooling being built under the Toronet Guidl banner, which includes Scaffold Toro and `toronetdeploy`. These tools are designed to work together, and the agent skills are specifically built to complement them — covering the AI-assistance layer that makes each of those tools easier to learn and use.

The project is fully open source (MIT license) and community contributions are welcome.