# DECISIONS — ProofMind Architecture Decisions

## ADR-001 — AI is not the oracle

**Decision:** The AI layer may interpret verified facts but never establishes blockchain truth.

**Reason:** The project's strongest technical differentiator is the separation between cryptographic verification and probabilistic reasoning.

## ADR-002 — Use dedicated source-chain events

**Decision:** Cross-chain actions should be triggered by specific events rather than generic events such as a standard token transfer.

**Reason:** The worker needs an unambiguous event to monitor and the ASC needs all required data.

## ADR-003 — Worker handles asynchronous protocol steps

**Decision:** The offchain worker owns event monitoring, attestation waiting, proof acquisition, retries, and ASC submission.

**Reason:** This removes protocol complexity from the user experience and follows the Attestcoin readability-worker pattern described in the supplied documentation.

## ADR-004 — Policy is deterministic

**Decision:** AI output is passed through deterministic rules before execution.

**Reason:** A model should never be the authorization boundary for an on-chain financial action.

## ADR-005 — Bounded actions only

**Decision:** The MVP exposes a small allowlist of business actions.

**Reason:** This makes the demo auditable and materially reduces the blast radius of an AI or integration failure.

## ADR-006 — Testnet first

**Decision:** The ideathon implementation targets the documented Creditcoin CC3 testnet environment and Ethereum Sepolia for the source-chain demo.

**Reason:** The supplied Creditcoin environment documentation identifies Ethereum Sepolia as a supported testnet chain and provides CC3 testnet infrastructure.

## ADR-007 — Reuse existing repository patterns

**Decision:** Extend the existing USC/Attestcoin examples instead of rewriting their proof-generation and worker mechanisms from scratch.

**Reason:** The repository already contains tutorial implementations and CI workflows that provide the fastest path to a reliable demo.
