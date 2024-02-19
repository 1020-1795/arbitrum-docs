---
title: 'ArbOS software releases'
sidebar_label: 'ArbOS software releases'
author: dlee
---

:::info
This reference document provides an overview of Nitro node software releases that upgrade ArbOS. Visit the [Nitro Github Repository](https://github.com/OffchainLabs/nitro/releases) for a detailed index of Nitro releases.

:::

Arbitrum chains are powered by Arbitrum nodes running the Nitro software stack. The Nitro software stack includes [ArbOS](https://forum.arbitrum.foundation/t/arbitrum-arbos-upgrades/19695), the Layer 2 EVM hypervisor that facilitates the execution environment of an Arbitrum chain.

Although Nitro is updated regularly, only a subset of Nitro releases carry ArbOS upgrades. These releases are significant because ArbOS upgrades are Arbitrum's equivalent to a hard fork - they can alter a node's ability to produce valid Arbitrum blocks. This is why validator nodes supporting a public Arbitrum chain (One, Nova) **must update Nitro** whenever a new ArbOS version is released.

Note that every Nitro release is backwards compatible. In other words, the latest version of Nitro will support all previous ArbOS releases. This means that your validator's Nitro version must be greater than or equal to the version that includes the latest ArbOS upgrade.

ArbOS upgrades are carried out by the chain's owner; in the case of Arbitrum One and Nova, the owner is the Arbitrum DAO and so an upgrade will require a governance proposal and vote to pass to complete the upgrade. [This is an example of a Nitro release that contains an ArbOS version bump, specifically to ArbOS 11](https://github.com/OffchainLabs/nitro/releases/tag/v2.2.0).

Visit [Inside Arbitrum Nitro](../../inside-arbitrum-nitro/inside-arbitrum-nitro.mdx) to learn more about Nitro's architecture; more information about ArbOS software releases is available on [the Arbitrum DAO forum](https://forum.arbitrum.foundation/t/arbitrum-arbos-upgrades/19695).

## Naming and numbering scheme

Beginning with ArbOS 20, ArbOS releases use the name of planetary moons in our solar system, ascending in alphabetical order (i.e. the next ArbOS upgrade after ArbOS 20 "Atlas" will be a planetary moon that begins with the letter "B").

The number used to denote each upgrade will increment by 10, starting from ArbOS 20 (i.e. the next ArbOS upgrade after ArbOS 20 will be ArbOS 30). This was done because there are teams who have customized their Orbit chain's [behavior](../../launch-orbit-chain/how-tos/customize-stf.mdx) or [precompiles](../../launch-orbit-chain/how-tos/customize-precompile.mdx) and who may wish to use ArbOS's naming schema between official ArbOS version bumps (e.g. ArbOS 12 could be the name of a customized version of ArbOS for a project's L3 Orbit chain).

## ArbOS 20: Atlas [Upcoming]

ArbOS 20 is an upcoming upgrade to ArbOS that will be shipped in a future version of Nitro. The Nitro version will be available as a Docker image on Docker Hub when finalized. For Arbitrum One and Nova, the ArbOS 20 upgrade requires a governance vote to activate.

### High-level description of ArbOS 20 changes

ArbOS 20 is an upgrade to enable Arbitrum's support for L1 Ethereum's [Dencun upgrade](https://eips.ethereum.org/EIPS/eip-7569) scheduled for March 2024. As a result, all of the ArbOS specific changes revolve around implementing the majority of the [Cancun EIPs](https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/cancun.md) on Arbitrum:

- Enable Arbitrum chains to batch and post transaction data in the form of Blobs to L1 Ethereum, to support [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844). This includes updates to the Sequencer Inbox contract to support posting transactions in the form of blobs, updating Nitro's fraud prover to support proving additional hashes (KZG and SHA256 preimages), and updates to the core Nitro node software to handle parsing data from EIP-4844 blobs.
- Addition of the `TSTORE` and `TLOAD` EVM opcodes introduced in [EIP-1153](https://eips.ethereum.org/EIPS/eip-1153) offering a cheaper option than storage for data that’s discarded at the end of a transaction.
- Addition of the `MCOPY` EVM opcode introduced in [EIP-5656](https://eips.ethereum.org/EIPS/eip-5656) for cheaper memory copying.
- Changes to the `SELFDESTRUCT` EVM opcode to reflect the behavior on L1 Ethereum, as outlined in [EIP-6780](https://eips.ethereum.org/EIPS/eip-6780).

### Special notes on ArbOS 20: Atlas support for EIP-4844

- Applications on Arbitrum will not have to be modified or take any explicit action to get the benefits of using EIP-4844 (i.e. the whole chain opts-in with ArbOS 20 “Atlas”).
- ArbOS 20 “Atlas” adds support for Arbitrum chains to send data in a blob storage format to data availability layers, like L1 Ethereum, that support the blob transaction type. This includes Arbitrum One and Nova. ArbOS 20 “Atlas” does not add support for Arbitrum chains to receive data in a blob storage format. This means that any L3 Orbit chain settling to an L2 Arbitrum chain will post data to the underlying L2 Arbitrum chain as calldata. The L2 Arbitrum chain will then be able to post data to a L1 data availability layer like Ethereum using blobs.
- There currently aren’t estimates on what the end-user gas savings of using blob data will be. This topic is something being actively worked on and monitored. Without Mainnet data, the estimates for blob gas prices will not be accurate enough to reliably predict the cost reductions that users will experience - and even with Mainnet data, the savings will vary by use case (i.e. no current way to predict the price impacts from all blob gas market participants yet). In general, however, the use of blobs will reduce the cost of using Arbitrum L2s.

### Reference links

- Original DAO proposal: [AIP: ArbOS Version 20 "Atlas"](https://forum.arbitrum.foundation/t/aip-arbos-version-20-atlas/20957)
- [AIP: ArbOS Version 20 "Atlas" Snapshot Vote](https://snapshot.org/#/arbitrumfoundation.eth/proposal/0x813a366e287a872ada13d4f8348e771c7aa2d8c3cb00b2be31539ceab5627513)

# ArbOS 11

ArbOS 11 is shipped via Nitro v2.2.0, which is available on Docker hub with the image tag: `offchainlabs/nitro-node:v2.2.0-f7dc9de`. This release of Nitro is a mandatory upgrade for Arbitrum One and Nova validators.

### High-level description of ArbOS 11 changes

- Addition of EVM changes made on L1 Ethereum as part of the [Shanghai upgrade](https://ethereum.org/history#shanghai), including support for the `PUSH0` opcode.
- Improvements and fixes for [retryable tickets](../../arbos/l1-to-l2-messaging.mdx) to ensure that the fee calculation to redeem retryable tickets will take into account both the infrastructure fee and the network fee. The infrastructure fee is the minimum L2 base fee only, while the network fee collects L2 congestion charges. This is important for [AnyTrust chains](../../inside-anytrust.mdx) like Arbitrum Nova because members of the Data Availability Committee (DAC) gets paid a percentage of the infrastructure fee but not the network fee. Previously, the calculations to determine the fee for redeeming retryable tickets did not consider the infrastructure fee.
- Fixes an issue where the [`ArbOwnerPublic` precompile](../../for-devs/dev-tools-and-resources/precompiles.mdx#arbownerpublic) returned the incorrect list of chain owners. This does not change the parties who are able to perform chain owner actions. As intended, only the Arbitrum DAO is able to take chain owner actions for Arbitrum One and Nova.
- Resolves an issue where the [`arbBlockHash` method](../../for-devs/dev-tools-and-resources/precompiles.mdx#arbsys) would take up all the gas when reverting. The previous incorrect behavior meant that if a transaction calls `arbBlockHash` with an out-of-range block number, then the transaction would consume all the gas when reverting.
- Addition of the [`L1RewardReceipient`](../../for-devs/dev-tools-and-resources/precompiles.mdx##arbgasinfo) and [`L1RewardRate`](../../for-devs/dev-tools-and-resources/precompiles.mdx##arbgasinfo) precompile methods to view L1 pricing parameters and make it easier to view the current chain configuration.
- Fix the `ArbOwner` precompile to disallow emitting logs in `STATICCALL` contexts, bringing this in line with how the EVM is expected to behave as `STATICCALL` invocations should never be able to emit logs. The previous incorrect behavior would mean that a log was emitted when a chain owner made a `STATICCALL` on the `ArbOwner` precompile.

### Reference links

- [Nitro v2.2.0 Release details on Github](https://github.com/OffchainLabs/nitro/releases/tag/v2.2.0)
- Original DAO proposal: [AIP: ArbOS Version 11](https://forum.arbitrum.foundation/t/aip-arbos-version-11/19696)
- [AIP: ArbOS Version 11 Snapshot Vote](https://snapshot.org/#/arbitrumfoundation.eth/proposal/0xa635e39a2c527f7a1eabf5ea22bdec6f4a265d6c69a06076e65fde0ae0a5941b)
- [Formal Tally (on-chain) vote for AIP: ArbOS Version 11](https://www.tally.xyz/gov/arbitrum/proposal/77069694702187027448745871790562515795432836429094222862498991082283032976814)
- [ArbOS 11 Audit Report by Trail of Bits](https://drive.google.com/file/d/1N3197Z7DuqBpu9qdt-GWPewe8HQakfLY/view)
