# ProofMind

## AI Agents + Cryptographically Verified Cross-Chain Data

**Hackathon Track:** AI

ProofMind is the working project for an AI application built around Creditcoin's Attestcoin Protocol. The goal is to let an AI agent reason about source-chain events that have been cryptographically verified through Attestcoin Readability, and then use that verified information to inform or trigger on-chain business logic.

> **Status:** Project documentation and architecture phase.

## Core Idea

```text
Source Chain
    |
    | transaction + event
    v
Source Chain Contract
    |
    v
Offchain Readability Worker
    |
    | wait for attestation
    v
Proof Builder
    |
    | Merkle + continuity proofs
    v
Attestcoin Smart Contract (Creditcoin)
    |
    | on-chain verification
    v
Verified Cross-Chain Data
    |
    v
AI Agent
    |
    | decision
    v
Business Logic Contract
```

## Repository Documentation

- [01 - Idea](./docs/01-idea.md)
- [02 - Problem Statement](./docs/02-problem-statement.md)
- [03 - Solution](./docs/03-solution.md)
- [04 - Use Cases](./docs/04-use-cases.md)
- [05 - Features](./docs/05-features.md)
- [06 - Architecture](./docs/06-architecture.md)
- [07 - System Flow](./docs/07-system-flow.md)
- [08 - Attestcoin Flow](./docs/08-attestcoin-flow.md)
- [09 - AI Agent](./docs/09-ai-agent.md)
- [10 - Smart Contracts](./docs/10-smart-contracts.md)
- [11 - Source Chain](./docs/11-source-chain.md)
- [12 - Offchain Worker](./docs/12-offchain-worker.md)
- [13 - Data Flow](./docs/13-data-flow.md)
- [14 - Security](./docs/14-security.md)
- [15 - Gas Cost](./docs/15-gas-cost.md)
- [16 - Testnet](./docs/16-testnet.md)
- [17 - API Reference](./docs/17-api-reference.md)
- [18 - Database](./docs/18-database.md)
- [19 - Frontend](./docs/19-frontend.md)
- [20 - Roadmap](./docs/20-roadmap.md)
- [21 - Ideathon Pitch](./docs/21-ideathon-pitch.md)
- [Project Decisions](./DECISIONS.md)

## Development Principle

This directory is the source of truth for the hackathon project. Update the documentation whenever an architecture, technology, contract, flow, or scope decision changes.

## Creditcoin References

The implementation is based on the Attestcoin Protocol concepts documented in the Creditcoin documentation and the existing tutorial repository structure in this repository.
