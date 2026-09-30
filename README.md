# Metera Cardano Vault Standard

An open, eUTxO-native vault and executor standard for Cardano that allows independent strategy pools to deploy capital across multiple DeFi protocols through standardised protocol-specific executors.

## Project status

**Under active development.** This repository documents the intended design. The vault standard is not production-ready, audited, or live on mainnet.

## Architecture overview

Each strategy is represented by an independent pool with its own canonical state UTxO and unique Pool NFT. Each pool maintains its own accounting, assets, strategy configuration, allocation state and share token supply. Global Settings hold shared protocol-level configuration.

Users submit deposits and withdrawals through order UTxOs. A batcher processes orders and coordinates validated pool state transitions. Cardano native assets represent pool identity and pool shares.

Protocol-specific executors deploy and unwind capital in external protocols, keeping protocol-specific implementation knowledge out of the core pool logic. Minswap and Liqwid are the initial reference integration targets; additional protocols can be supported through compatible executors. These are design targets, not claims of implemented integrations.

On-chain contracts are written in Aiken as implementation progresses. Off-chain components are expected to use TypeScript with Lucid and/or Mesh.

![Metera Cardano Vault Architecture](docs/assets/architecture.png)

The diagram’s older labels should be read alongside the [technical architecture](docs/architecture.md), which uses Liqwid consistently and treats Strike only as a possible future integration subject to technical compatibility verification.

## Goals

- Make managed DeFi strategies easier to build on Cardano.
- Provide reusable vault infrastructure.
- Standardise protocol integrations through executors.
- Allow wallets, protocols, asset managers and developers to build strategy products on top.

## Repository status

Contract implementations, executor interfaces, tests and off-chain components will be added progressively. The current repository contains design documentation and placeholder directories:

- `validators/`: Aiken on-chain contracts.
- `offchain/`: TypeScript transaction construction and coordination.
- `tests/`: validator, accounting and integration tests.
- `docs/`: technical architecture and supporting assets.

The standard is intended as reusable Cardano infrastructure. Exact protocol rules remain subject to specification, implementation and review.
