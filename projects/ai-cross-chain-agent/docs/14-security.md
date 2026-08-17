# 14 — Security

## Trust Boundaries

```text
Source-chain transaction
        |
        v
Attestcoin proof verification  <-- cryptographic boundary
        |
        v
AI reasoning                  <-- application reasoning
        |
        v
Business logic contract      <-- execution boundary
```

## Key Risks

### Invalid or incomplete proof

The ASC must reject invalid verification results and must not execute application logic from unverified data.

### Replay

The same source-chain event must not trigger the destination action more than once.

### AI output abuse

The AI should not have unrestricted authority over arbitrary contract calls. Its output should map to a constrained set of actions enforced by application logic.

### Worker duplication

Workers should track processed events and use deterministic identifiers so retries do not create duplicate business actions.

### Worker downtime

Persist event-processing state and support catch-up after restart.

### Source-chain ambiguity

Use dedicated, unambiguous events rather than relying on common generic events.

## Prototype Rule

This is a hackathon/testnet architecture. Security controls should be documented and demonstrated, but the system must not be presented as production-ready until independently audited and hardened.
