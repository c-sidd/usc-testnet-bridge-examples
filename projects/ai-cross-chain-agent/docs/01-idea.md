# 01 — Project Idea

## Project Name

**ProofMind**

## One-Line Idea

AI agents that reason about cryptographically verified cross-chain blockchain data and use the result to inform or trigger on-chain actions.

## Core Concept

ProofMind combines three capabilities:

1. **Cross-chain readability** through Creditcoin Attestcoin Protocol.
2. **AI reasoning** over verified blockchain events.
3. **On-chain execution** through smart-contract business logic.

The important design principle is that the AI is not treated as the source of truth. The source-chain transaction is first proven and verified through the Attestcoin flow. The AI then operates on the verified result.

## Why This Idea

The AI track is a strong fit because Attestcoin Readability is specifically designed to provision data from a source chain such as Ethereum to a dApp on Creditcoin. The project can demonstrate how verified cross-chain state can become an input to an autonomous AI-driven application.

## Current Scope

The exact application use case is intentionally kept flexible during the architecture phase. Candidate use cases are documented in [04 — Use Cases](./04-use-cases.md). One concrete use case will be selected before implementation begins.

## Non-Goals for the Initial Version

- Building a general-purpose AI model.
- Supporting every blockchain.
- Building production-grade infrastructure.
- Treating an off-chain API response as cryptographic proof.

The first goal is a reliable end-to-end testnet demonstration.
