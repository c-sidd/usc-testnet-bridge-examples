# 13 — Data Flow

## End-to-End Data

```text
User transaction
      |
      v
Source-chain event
      |
      v
Block + transaction identification
      |
      v
Attestation
      |
      v
Merkle proof + continuity proof + encoded transaction
      |
      v
ASC verification
      |
      v
Verified event fields
      |
      v
AI input normalization
      |
      v
AI decision
      |
      v
Execution request
      |
      v
Creditcoin state update
```

## Event Design

Source-chain events should be:

- Specific to the action they represent.
- Easy for the worker to filter.
- Unambiguous.
- Complete enough that the destination contract does not need to infer missing data.

Avoid using generic events as the trigger for cross-chain functionality when a dedicated event can make the intent explicit.

## Traceability

The system should retain, where available:

- Source-chain transaction hash.
- Source-chain block number.
- Event identifier.
- Proof request status.
- ASC transaction hash.
- Verification status.
- AI decision identifier.
- Destination execution transaction hash.

These fields will make the demo and debugging process much easier.
