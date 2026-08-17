# Project Decisions

This file records important decisions so the project can be resumed without reconstructing the reasoning from chat history.

## Decision 001 — Hackathon Track

**Date:** 2026-08-17

**Decision:** AI

**Reason:** The project can combine AI reasoning with Attestcoin's cryptographically verified cross-chain readability, creating a clear technical connection to Creditcoin's infrastructure.

## Decision 002 — Project Workspace

**Date:** 2026-08-18

**Decision:** Create a dedicated project under `projects/ai-cross-chain-agent/` inside the existing `usc-testnet-bridge-examples` repository.

**Reason:** Keep the original Creditcoin tutorials intact while maintaining a persistent workspace for the hackathon project.

## Decision 003 — Verification Boundary

**Date:** 2026-08-18

**Decision:** Treat Attestcoin as the verification layer, AI as the reasoning layer, and the smart contract as the execution/enforcement layer.

**Reason:** This keeps cryptographic verification separate from probabilistic AI output.

## Decision 004 — Initial Network

**Date:** 2026-08-18

**Decision:** Use CC3 Testnet for the implementation.

**Reason:** The collected Creditcoin documentation explicitly provides a CC3 Testnet environment and Ethereum Sepolia support for Attestcoin flows.

## Decision 005 — Worker Architecture

**Date:** 2026-08-18

**Decision:** Use an offchain readability worker for the prototype.

**Reason:** It automates attestation waiting, proof generation, ASC submission, retries, and event processing, matching the documented worker architecture.

## Pending Decision

### Final AI Use Case

Not selected yet. Candidate options are documented in `docs/04-use-cases.md`.
