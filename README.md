# Merkle Airdrop Extravaganza

Here is the best way to airdrop your tokens. In this repository, we will cover the method of airdropping using _Merkle Proof_. This is the cheapest way you can airdrop yor token. This mechanism uses a hash tree named _Merkle Tree_, that verifies the claimers identity using the _Merkle proof_ process.

- [Merkle Airdrop Extravaganza](#merkle-airdrop-extravaganza)
- [Getting Started](#getting-started)
  - [Requirements](#requirements)
  - [Quickstart](#quickstart)
- [Usage](#usage)
  - [Pre-deploy: Generate merkle proofs](#pre-deploy-generate-merkle-proofs)
- [Formatting](#formatting)
- [Thank you!](#thank-you)

# Getting Started

## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)`

To get started, we are assuming you're working with vanilla `foundry` and not `foundry-zksync` to start.

## Quickstart

```bash
git clone https://github.com/ciara/merkle-airdrop
cd merkle-airdrop
make # or forge install && forge build if you don't have make
```

# Usage

## Pre-deploy: Generate merkle proofs

We are going to generate merkle proofs for an array of addresses to airdrop funds to. If you'd like to work with the default addresses and proofs already created in this repo, skip to [deploy](#deploy)

If you'd like to work with a different array of addresses (the `whitelist` list in `GenerateInput.s.sol`), you will need to follow the following:

First, the array of addresses to airdrop to needs to be updated in `GenerateInput.s.sol. To generate the input file and then the merkle root and proofs, run the following:

Using make:

```bash
make merkle
```

Or using the commands directly:

```bash
forge script script/GenerateInput.s.sol:GenerateInput && forge script script/MakeMerkle.s.sol:MakeMerkle
```

Then, retrieve the `root` (there may be more than 1, but they will all be the same) from `script/target/output.json` and paste it in the `Makefile` as `ROOT` (for zkSync deployments) and update `s_merkleRoot` in `DeployMerkleAirdrop.s.sol` for Ethereum/Anvil deployments.

# Formatting

To run code formatting:

```
forge fmt
```

# Thank you!

If you appreciated this, please follow [Cyfrin Updraft!](https://x.com/CyfrinUpdraft)
