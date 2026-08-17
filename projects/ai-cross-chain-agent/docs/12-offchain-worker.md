# 12 — Offchain Readability Worker

## Purpose

The worker automates the second half of a cross-chain interaction so the user does not have to manually wait for attestation, build proofs, format proof data, and submit the ASC transaction.

## Worker Responsibilities

1. Monitor the source-chain contract for relevant events.
2. Store newly detected events.
3. Wait for the block containing an event to be attested on Creditcoin.
4. Request Merkle and continuity proofs from the Proof Builder.
5. Submit the proof package and encoded transaction to the ASC.
6. Observe the result.
7. Retry temporary failures.
8. Prevent duplicate processing.
9. Recover missed events after a restart.
10. Support more than one source-chain node where practical.

## Robustness Requirements

The worker should retain records of events in progress so a shutdown does not lose state. It should also be able to catch up on events missed while offline.

## Logical Flow

```text
Monitor Events
      |
      v
Event Detected
      |
      v
Wait for Attestation
      |
      +-- not ready --> wait/retry
      |
      v
Generate Proofs
      |
      +-- failure --> retry
      |
      v
Call ASC
      |
      +-- failure --> retry
      |
      v
Verified + Executed
```

## Future Option

The Creditcoin documentation describes a future model in which third-party relayers may provide readability-query submission as a service. The initial prototype should not depend on that future service; it should own the worker flow.
