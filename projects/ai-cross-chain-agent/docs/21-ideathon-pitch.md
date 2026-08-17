# 21 — Ideathon Pitch

## Project

**ProofMind**

## Track

**AI**

## One-Liner

> AI agents that act on cryptographically verified cross-chain data.

## Problem

AI agents can reason about data, but cross-chain applications still need a trustworthy way to establish that the underlying blockchain event actually occurred.

## Solution

ProofMind uses Creditcoin's Attestcoin Protocol to verify source-chain transaction data before passing it to an AI agent. The agent reasons over the verified data and can request a constrained on-chain action.

## Why Creditcoin

Creditcoin provides the Attestcoin Readability infrastructure used in the prototype: source-chain attestation, proof generation, and synchronous on-chain verification through the Block Prover Precompile.

## Demo Story

```text
1. User performs action on Ethereum Sepolia.
2. Source contract emits a specific event.
3. Worker detects it.
4. Worker waits for attestation.
5. Worker obtains proofs.
6. ASC verifies the source transaction on Creditcoin.
7. AI receives the verified event.
8. AI makes the application decision.
9. Creditcoin contract executes the allowed action.
10. Dashboard shows the full trace.
```

## Differentiator

The project separates three concerns:

- **Proof:** Attestcoin establishes the source-chain fact.
- **Reasoning:** AI interprets the verified fact.
- **Enforcement:** Smart contracts constrain and execute the action.

## Pitch Status

This document is a working draft. Update it after the final use case and MVP are selected.
