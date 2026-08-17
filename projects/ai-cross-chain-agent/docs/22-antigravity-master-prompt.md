# 22 — Antigravity Master Prompt

Use this document as the implementation contract when vibe-coding ProofMind with Antigravity.

## Role

Act as a senior full-stack Web3 engineer implementing ProofMind inside this repository. Before changing code, inspect the existing examples and reuse their working Attestcoin patterns instead of creating parallel abstractions unnecessarily.

## Repository-first rule

Study these existing areas first:

- `hello-bridge/`
- `custom-contracts-bridging/`
- `bridge-offchain-worker/`
- `loan-flow/`
- `contracts/`
- `utils/`
- `.env` / environment examples
- GitHub workflows related to the examples

The current repository already contains working patterns for event polling, proof generation, gas estimation, and proof submission. Extend them carefully.

## Build order

### Phase 1 — source contract

Create the smallest source-chain contract needed for the demo. It should emit one dedicated event containing all data needed by the Creditcoin-side application.

### Phase 2 — Creditcoin contracts

Implement:

- Attestcoin Smart Contract integration boundary;
- verified-fact handling;
- deterministic policy checks;
- one bounded business action;
- replay protection;
- events for every important state transition.

Do not duplicate the protocol's native proof verification logic if the existing SDK/example already provides the correct integration path.

### Phase 3 — worker

Implement a robust worker that:

1. polls/listens for the source event;
2. persists or otherwise tracks in-progress requests;
3. waits for attestation;
4. requests the Proof Builder data;
5. submits the proof to the ASC;
6. records success/failure;
7. avoids duplicate processing;
8. retries transient failures.

### Phase 4 — verified fact service

Normalize the verified event into the stable data contract in `11-interfaces-and-data-contracts.md`.

### Phase 5 — AI

Build the AI service around structured JSON output. The model receives verified facts and returns `APPROVE`, `REVIEW`, or `REJECT` plus reason codes. Validate the model output before any policy evaluation.

### Phase 6 — policy

Implement deterministic limits in code. AI cannot bypass them and cannot generate arbitrary calldata.

### Phase 7 — dashboard

Implement the request timeline and detail page described in `18-dashboard-and-api.md`.

### Phase 8 — tests

Implement tests for every requirement before calling the MVP complete.

## Coding rules

- Prefer small files and single responsibilities.
- Keep protocol-specific code behind a clear service boundary.
- Do not hard-code secrets.
- Never commit real private keys.
- Never silently swallow proof or transaction failures.
- Validate every external input.
- Use explicit TypeScript types for cross-component data.
- Add comments where the code explains *why*, not merely *what*.
- Preserve the repository's existing formatting and package conventions.
- Do not rename existing working tutorial files without a strong reason.

## AI safety rule

The LLM may recommend a predefined action. It may not choose an arbitrary contract address, arbitrary function selector, arbitrary calldata, or unrestricted transfer amount.

## Definition of done

A feature is done only when:

- code exists;
- configuration is documented;
- happy path works on the intended testnet;
- failure path is handled;
- duplicate processing is prevented;
- logs identify the request ID;
- tests cover the critical behavior;
- the dashboard exposes the result;
- and the corresponding documentation is updated.

## Never do this

Do not replace the Attestcoin proof path with a centralized database lookup, an explorer API assertion, or an LLM claim. Those may be useful for UI enrichment, but they are not substitutes for cryptographic verification.
