# 19 — Demo Script

## Target demo length

Aim for 3–5 minutes. The demo should show the technology, not a long setup process.

## Scene 1 — Problem (20–30 seconds)

Explain that an AI agent can reason about financial information, but a cross-chain application needs a trustworthy way to establish that the underlying blockchain event really happened.

## Scene 2 — Source-chain action (30 seconds)

Perform one controlled demo transaction on the source chain. Point out the dedicated event and its request ID.

## Scene 3 — Attestcoin pipeline (60–90 seconds)

Show the worker detecting the event, waiting for attestation, requesting the proof, and submitting the proof to the ASC.

Call out that the ASC verifies the proof synchronously through the Block Prover Precompile before accepting the source-chain fact.

## Scene 4 — AI reasoning (30–45 seconds)

Show the normalized verified facts entering the AI layer. Show the structured decision and the short explanation.

Say explicitly:

> The AI is not our oracle. Attestcoin establishes the fact; the AI reasons over that verified fact.

## Scene 5 — Deterministic execution (30–45 seconds)

Show the policy layer and the predefined smart-contract action. Show the resulting Creditcoin transaction.

## Scene 6 — Audit trail (20–30 seconds)

Open the request timeline and show source transaction → proof → verification → AI decision → execution.

## Judge takeaway

The strongest final sentence is:

> ProofMind combines cryptographic cross-chain verification, AI reasoning, and deterministic smart-contract enforcement so an AI agent can act on blockchain facts without being trusted as the source of truth.

## Demo fallback

If live proof generation is temporarily slow, the UI should show the real request status instead of faking a successful verification. A pre-recorded successful run can be used as a backup, but the architecture and transaction references should remain inspectable.
