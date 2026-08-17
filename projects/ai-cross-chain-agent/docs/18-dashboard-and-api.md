# 18 — Dashboard and API

## Dashboard goal

The UI is not just a frontend. It is the judge-facing observability surface for the entire proof-to-action pipeline.

## Main screen

Show four stages as a timeline:

1. **Source event detected**
2. **Attestation/proof ready**
3. **Verified on Creditcoin**
4. **AI decision + action**

Each stage should expose transaction hashes, block numbers, status, timestamps, and failure messages where available.

## Request detail page

Sections:

- Source transaction
- Event payload
- Attestation status
- Merkle proof status
- Continuity proof status
- ASC verification transaction
- Normalized verified facts
- AI decision
- Deterministic policy result
- Creditcoin execution transaction

## Suggested API boundaries

```text
GET  /api/health
GET  /api/requests
GET  /api/requests/:requestId
GET  /api/requests/:requestId/timeline
POST /api/demo/request
POST /api/ai/evaluate
```

These are application-level interfaces, not claims about an existing Creditcoin API. Keep Creditcoin/Proof Builder calls behind a backend service boundary.

## Status model

```text
DETECTED
  ↓
WAITING_FOR_ATTESTATION
  ↓
BUILDING_PROOF
  ↓
PROOF_READY
  ↓
SUBMITTED_TO_ASC
  ↓
VERIFIED
  ↓
AI_EVALUATED
  ↓
POLICY_APPROVED / POLICY_REJECTED
  ↓
EXECUTED / FAILED
```

## Failure visibility

Never show a generic `Something went wrong` for the main demo. Display the pipeline stage and a safe diagnostic such as `Proof Builder unavailable`, `Block not attested yet`, `ASC transaction reverted`, or `AI schema validation failed`.
