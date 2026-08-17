# 06 — Architecture

## High-Level Architecture

```text
                         SOURCE CHAIN
                    Ethereum / Sepolia
                           |
                           | Event
                           v
                 +---------------------+
                 | Source Chain        |
                 | Smart Contract      |
                 +----------+----------+
                            |
                            v
                 +---------------------+
                 | Offchain Readability|
                 | Worker               |
                 +----------+----------+
                            |
                 wait for attestation
                            |
                            v
                 +---------------------+
                 | Proof Builder       |
                 | Merkle + Continuity |
                 +----------+----------+
                            |
                            v
                    CREDITCOIN / CC3
                 +---------------------+
                 | Attestcoin Smart    |
                 | Contract (ASC)      |
                 +----------+----------+
                            |
                            v
                 +---------------------+
                 | Block Prover        |
                 | Precompile 0xFD2    |
                 +----------+----------+
                            |
                     verified data
                            v
                 +---------------------+
                 | AI Agent            |
                 +----------+----------+
                            |
                         decision
                            v
                 +---------------------+
                 | Business Logic      |
                 | Smart Contract      |
                 +---------------------+
```

## Components

### 1. Source Chain Smart Contract

Keep source-chain logic as minimal as practical. It should emit specific, unambiguous events containing the data required by the Creditcoin application.

### 2. Offchain Readability Worker

The worker detects events, waits for attestation, requests proofs, submits the ASC transaction, retries failures, and tracks processed events.

### 3. Proof Builder

Provides the proof material required by the ASC, including Merkle and continuity proofs and encoded transaction data.

### 4. Attestcoin Smart Contract

Runs on Creditcoin. It verifies the source-chain transaction through the Block Prover Precompile and then executes or calls application business logic.

### 5. AI Agent

Consumes verified event data and performs application-level reasoning. It is not the cryptographic trust boundary.

### 6. Business Logic Contract

Contains deterministic state changes and access control. The final prototype should make clear which actions the AI can request and which checks remain on-chain.

## Architecture Pattern

For the prototype, prefer a separated pattern when it improves clarity: the ASC handles verification and calls a separate business-logic contract after successful verification.
