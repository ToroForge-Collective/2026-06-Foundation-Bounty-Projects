# Scaffold Toro

## Project Overview

Scaffold Toro is the easiest way for developers to get started building on Toronet.

It bootstraps a full stack application with everything you need to build a dApp in the Toronet ecosystem. Scaffold Toro includes batteries that make building very easy.

It is composed of two main components that developers need to build dApps:

* Full Stack Web App with everything you need to start development.

  * Starter code
  * Ready hooks
  * Easy-to-understand components you can import immediately
* Smart contract development environment that is fully set up.

  * Use the framework you're comfortable with
  * Have starter contracts and scripts to move faster

### Why I'm Interested in Building This

When I got introduced to Toronet, it was through a partnership between a company I work for and the Toronet team. I wish I had a tool like this that could help me bootstrap a Proof of Concept really fast, but there was none.

I am building Scaffold Toro the way I wish it existed, so that developers after me who are looking to try out Toronet or even build production applications can get started quickly and easily.

## Project Details

### Stack

Scaffold Toro creates a project template that includes a full stack application and a Solidity development framework of your choice.

The full stack template is written in Next.js and contains the boilerplate code needed to build your application. The template uses DaisyUI as its styling component library.

The smart contract development template is already configured, allowing developers to immediately write code, test, and deploy contracts without additional setup. While scaffolding the application with the tool, developers can choose the framework they would like to use (Foundry, Hardhat, or None).

### Links

* `create-toro`: CLI tool used in bootstrapping projects. https://www.npmjs.com/package/create-toro
* `scaffold-toro-app`: Specifications of the starter template. https://github.com/toronet-guidl/scaffold-toro-app

### Scope

The scope and objective of this project are simple: create boilerplate templates that make development within the Toronet ecosystem fast and easy to get started with.

Many more updates to this project will come that push us closer to our goal. Everything will be open source and community-led to enhance transparency.

Our scope might seem simple and broad at the same time, but anything that does not align with this goal will not be done.

This project also involves creating comprehensive documentation and educational content that developers can use to learn both how to use the tools and how to build on Toronet in general.

## Ecosystem Fit

Scaffold Toro will sit at a critical point in developer onboarding within the ecosystem.

New and interested developers can use it to understand how to start developing on Toronet. Existing developers in the ecosystem can also use it to create Proof of Concept demos and even production applications.

The target audience for this tool is every developer in the ecosystem because it solves the problem of developing quickly while making it easier to understand the ecosystem.

There are currently no existing projects doing exactly what Scaffold Toro is doing. I know this because I have discussed it with seasoned developers from the ToroForge collective.

## Team

* **Team Name:** Toronet Guidl
* **Contact Name:** Emmanuel Nwafor (Emmo00)
* **Contact Email:** [nwaforemmanuel005@gmail.com](mailto:nwaforemmanuel005@gmail.com)
* **Website:**

  * https://scaffold-toro.vercel.app/
  * https://github.com/toronet-guidl/
  * https://github.com/Emmo00/

## Team Members

* Emmanuel Nwafor

### LinkedIn Profiles (if available)

* https://www.linkedin.com/in/emmanuel-nwafor-53735a270/

## Team Code Repositories

* https://github.com/toronet-guidl/create-toro
* https://github.com/toronet-guidl/scaffold-toro-app
* https://github.com/toronet-guidl/scaffold-toro-site

Please also provide the GitHub accounts of all team members:

* https://github.com/emmo00

## Team Experience

Emmo00 is a Web3 full stack software engineer who enjoys open source contributions.

He is also the creator of toronetdeploy and toronet-agent-skills.

## Development Status

Development has already started.

We have developed an initial version of the tool, but we noticed there are supporting tools that need to exist within the Toronet ecosystem in order to make the experience as seamless as possible.

As we continue building Scaffold Toro, we will also help fill those gaps by creating complementary tools and applications that improve the overall developer experience.

## Development Roadmap

### Milestone #1 (Done)

Build the CLI tool.

Be able to bootstrap full stack projects and smart contracts.

Support 2 Solidity frameworks.

Support full smart contract development flows, including development, testing, and deployment using `toronetdeploy`.

#### Validation

Be able to create a project using the `create-toro` CLI tool.

### Milestone #2

After development of wallet connection infrastructure (on the side), I am going to integrate it into the templates.

Build custom hooks and components that developers can use immediately.

Provide starter implementations for common Toronet development workflows.

#### Validation

Developers can build a complete application with functionality powered by the components and hooks we provide.

Wallet connection and blockchain interactions can be achieved with minimal configuration.

### Milestone #3

Create comprehensive documentation.

Create educational content explaining Toronet and how to use Scaffold Toro.

Provide tutorials, walkthroughs, and example projects.

#### Validation

Anyone can find content and guides on how to build with Scaffold Toro.

A new developer should be able to go from installation to deployment by following the documentation.

## Overview

Milestone #1 is done and we are immediately working on the second milestone.

* **Estimated Duration:** 2 weeks for Milestone #1 and approximately 1 month for the remaining milestones.
* **Full-Time Equivalent (FTE):** Emmo00 is currently the only contributor working directly on this project, but the project is open source and can receive feedback and contributions from anyone.

| Number | Deliverable                         | Specification                                                                                              |
| -----: | ----------------------------------- | ---------------------------------------------------------------------------------------------------------- |
|    0a. | License                             | MIT                                                                                                        |
|    0b. | Documentation                       | https://github.com/toronet-guidl/create-toro/blob/main/README.md                                           |
|     1. | CLI Scaffolding Tool                | Create and maintain the `create-toro` CLI that bootstraps full stack Toronet applications                  |
|     2. | Developer Hooks & Components        | Build reusable hooks, wallet integrations, and UI components for common Toronet development workflows      |
|     3. | Documentation & Educational Content | Produce guides, tutorials, example projects, and onboarding resources for developers building on Toronet   |

# 🔮 Future Plans

### Continuing Development After the Grant

Scaffold Toro is not intended to be a one-time project. My goal is to continue maintaining and improving it as the Toronet ecosystem grows.

After the grant, I plan to:

* Continue adding developing the templates and starter kits.
* Maintain compatibility with new Toronet tooling and ecosystem updates.
* Improve the developer experience based on community feedback.
* Add more reusable hooks, components, and utilities that developers commonly need.
* Expand the documentation and educational resources available to developers.

### Funding, Partnerships, and Ecosystem Collaboration

I plan to work closely with other teams and contributors within the Toronet ecosystem to identify missing developer tools and improve the overall onboarding experience.

As adoption grows, I would like to:

* Collaborate with ecosystem projects to create official integrations and starter templates.
* Work with the ToroForge collective and other ecosystem contributors to gather feedback and prioritize features.
* Seek additional grants or ecosystem funding opportunities that align with improving developer tooling and onboarding.
* Encourage community contributions by keeping the project fully open source and community-driven.

### Long-Term Vision

My long-term vision is for Scaffold Toro to become the default starting point for anyone building on Toronet.

A developer should be able to install a single tool, generate a project, connect a wallet, write contracts, test, deploy, and build a production-ready application with minimal setup.

The ultimate goal is to reduce the time it takes a developer to go from learning about Toronet to successfully shipping an application on the network.
