# 08 — Attestcoin Flow

## Readability Pipeline

```text
Source-chain event
       |
       v
Block attestation
       |
       v
Proof Builder
       |
       +--> Merkle proof
       |
       +--> Continuity proof
       |
       +--> Encoded transaction
       |
       v
Attestcoin Smart Contract
       |
       v
Block Prover Precompile
       |
       v
Verified source-chain transaction
       |
       v
Application business logic
```

## Why Both Proof Types Matter

The Merkle proof establishes transaction inclusion in the relevant source-chain block. The continuity proof connects the relevant source-chain block to an attested checkpoint so the destination-chain verifier can establish the required chain history.

## Relevant Creditcoin Addresses

### Block Prover Precompile

`0x0000000000000000000000000000000000000FD2`

### ChainInfo Precompile

`0x0000000000000000000000000000000000000fd3`

These values are documented for the CC3 Attestcoin environments provided in the project research notes.

## Important UX Point

The end user should only need to perform the initial source-chain transaction in the worker-based design. The worker handles waiting, proof generation, formatting, submission, and retries in the background.
