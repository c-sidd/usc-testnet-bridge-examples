# 03 — Solution

## Overview

ProofMind uses Creditcoin's Attestcoin Protocol Readability as the verification layer between a source blockchain and an AI-driven application on Creditcoin.

## Solution Components

### Source Chain

A source-chain smart contract emits explicit events containing the data that the destination application needs.

### Readability Worker

An off-chain worker monitors the source chain, waits for the relevant block to be attested, obtains proofs from the Proof Builder, and submits the proof package to the Attestcoin Smart Contract.

### Attestcoin Smart Contract

The ASC receives Merkle and continuity proofs plus encoded transaction data. It verifies the source-chain data synchronously using the Block Prover Precompile and then exposes the verified information to the application's business logic.

### AI Agent

The AI agent consumes the verified event information, evaluates the application-specific conditions, and produces a decision or recommendation.

### Business Logic

A Creditcoin smart contract applies the allowed action after the verification/decision flow. The final execution rules should remain deterministic and enforceable on-chain.

## Key Principle

**Verify first, reason second, execute last.**

The AI should not be responsible for proving that a source-chain event occurred. Attestcoin performs the blockchain verification; the AI performs application-level reasoning.
