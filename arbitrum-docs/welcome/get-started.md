---
title: 'Get started with Arbitrum'
description: An abbreviated introduction to the Arbitrum suite
author: symbolpunk
user_story: As a curious reader, I'd like to be quickly guided towards first steps based on my particular needs.
content_type: quickstart
---

<a data-quicklook-from='arbitrum'>Arbitrum</a> is a suite of Ethereum scaling solutions that make it easy to build and use decentralized applications. This document provides a high-level overview of the Arbitrum suite along with onboarding guidance tailored to specific audiences.


## The Arbitrum suite

The Arbitrum suite includes the protocols, chains, services, and SDKs that power the Arbitrum ecosystem:

| Component                                                         | Description                                                                                         |
| ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [Arbitrum Rollup](/inside-arbitrum-nitro)                         | A **protocol** for scaling Ethereum smart contracts.                                                |
| [Arbitrum AnyTrust](/inside-anytrust)                             | A **protocol** for scaling Ethereum smart contracts even further, with a mild trust assumption.     |
| [Arbitrum Nitro](/inside-arbitrum-nitro)                          | The node **software** that codifies the Rollup and AnyTrust protocols.                              |
| [Arbitrum nodes](/node-running/how-tos/running-a-full-node)       | **Machines** that run Nitro in order to service and/or interact with an Arbitrum chain.             |
| [Arbitrum One](https://portal.arbitrum.io/?chains=arbitrum-one)   | A public Rollup **chain**.                                                                          |
| [Arbitrum Nova](https://portal.arbitrum.io/?chains=arbitrum-nova) | A public AnyTrust **chain**.                                                                        |
| [Arbitrum Bridge](https://bridge.arbitrum.io/)                    | Lets you move ERC-20 tokens between Ethereum and Arbitrum.                                          |
| [Arbitrum Orbit](https://orbit.arbitrum.io/)                      | Lets you run your own Rollup and AnyTrust chains.                                                   |
| [Stylus](/stylus/stylus-gentle-introduction)                      | Lets you write EVM-compatible smart contracts in Rust and any other language that compiles to Wasm. |



## Arbitrum for users

**Users** can interact with Arbitrum either through the Arbitrum Bridge or by using dApps that have been deployed to an Arbitrum chain.

| Resource                                                  | Description                                                     |
| --------------------------------------------------------- | --------------------------------------------------------------- |
| [Arbitrum bridge](/bridge-tokens/concepts/bridge-concept) | Lets you move ERC-20 tokens between Ethereum and Arbitrum.      |
| [Arbitrum Portal](https://portal.arbitrum.io/)            | A directory of dApps on Arbitrum.                               |
| [Quickstart (bridge)](/getting-started-users)             | Provides step-by-step instructions for first-time bridge users. |


## Arbitrum for developers

**Developers** can build Arbitrum dApps by deploying smart contracts to an Arbitrum chain.

| Resource                                                                 | Description                                                                                              |
| ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| [A gentle introduction to Arbitrum](/for-devs/gentle-introduction-dapps) | A technical introduction to Arbitrum's suite of scaling solutions.                                       |
| [Quickstart (Solidity)](/getting-started-devs)                           | Targeted at web2 developers who want to deploy their first Solidity smart contract to Arbitrum.          |
| [Quickstart (Rust)](/stylus/stylus-quickstart)                           | Targeted at web3 developers who want to deploy their first Rust smart contract to Arbitrum using Stylus. |


## Arbitrum for node runners

**Node runners** run the machines that support the Arbitrum ecosystem.

| Resource                                                                                                  | Description                                                                                                           |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| [Run a full node](/node-running/how-tos/running-a-full-node)                                              | Targeted at node runners who want to access Arbitrum chains without having to connect to a third-party node.          |
| [Configure a Data Availability Committee](/node-running/how-tos/data-availability-committee/introduction) | Targeted at Data Availability Committee members and Orbit chain operators who want to run a Data Availability Server. |


## Arbitrum for chain operators

**Chain operators** use Arbitrum Orbit to run special-purpose Rollup and AnyTrust chains.

| Resource                                                                   | Description                                                                                     |
| -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [Orbit gentle introduction](/launch-orbit-chain/orbit-gentle-introduction) | Targeted at readers who want to understand Orbit's value proposition and use cases.             |
| [Orbit quickstart](/launch-orbit-chain/orbit-quickstart)                   | Targeted at chain operators who want to deploy their first Arbitrum chain using Arbitrum Orbit. |



## Arbitrum for curious readers

| Resource                                                                                           | Description                                       |
| -------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| [Arbitrum whitepaper](https://github.com/OffchainLabs/nitro/blob/master/docs/Nitro-whitepaper.pdf) | The original whitepaper that introduced Nitro.    |
| [DAO docs](https://docs.arbitrum.foundation/gentle-intro-dao-governance)                           | Docs that support members of the Arbitrum DAO.    |
| [Inside AnyTrust](/inside-anytrust)                                                                | A technical deep dive into the AnyTrust protocol. |
| [Inside Nitro](/inside-arbitrum-nitro)                                                             | A technical deep dive into Nitro's architecture.  |
