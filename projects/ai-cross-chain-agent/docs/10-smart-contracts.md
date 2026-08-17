# 10 — Smart Contracts

## Contract Layers

### Source Chain Contract

Responsibilities:

- Accept the source-chain user action.
- Perform only logic that must happen on the source chain.
- Emit unambiguous events.
- Include all information that the destination application needs to consume.

### Attestcoin Smart Contract (ASC)

Responsibilities:

- Receive proof data and encoded transaction data from the worker.
- Call the Native Query Verifier / Block Prover Precompile.
- Reject invalid proofs.
- Extract the verified transaction/event information.
- Execute or call the destination business logic.

### Business Logic Contract

Responsibilities:

- Maintain application state.
- Enforce deterministic rules.
- Restrict who can call privileged functions.
- Emit application result events.

## Combined vs Separated Pattern

A simple prototype can combine ASC and business logic. A more complex application should separate verification from business logic for modularity.

## Replay Protection

The destination application must prevent the same source-chain event from causing the business action more than once. The worker should also track processed events, while the ASC/business-logic layer should enforce its own safety boundary.

## Development Rule

No production deployment should be inferred from the tutorial material. The Creditcoin documentation explicitly describes the example infrastructure as educational.
