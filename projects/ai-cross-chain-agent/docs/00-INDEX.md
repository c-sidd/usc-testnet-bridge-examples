# ProofMind Documentation Index

## Project status

This folder is the single source of truth for the ProofMind ideathon build. The implementation should follow the documents in order and must not invent a different architecture during vibe-coding.

## Read in this order

1. [01 — Idea](./01-idea.md)
2. [02 — Problem Statement](./02-problem-statement.md)
3. [03 — Solution](./03-solution.md)
4. [04 — Use Cases](./04-use-cases.md)
5. [05 — Scope and Requirements](./05-scope-and-requirements.md)
6. [06 — Architecture](./06-architecture.md)
7. [07 — System Flow](./07-system-flow.md)
8. [08 — Attestcoin Flow](./08-attestcoin-flow.md)
9. [09 — AI Agent](./09-ai-agent.md)
10. [10 — Smart Contracts](./10-smart-contracts.md)
11. [11 — Interfaces and Data Contracts](./11-interfaces-and-data-contracts.md)
12. [12 — Offchain Worker](./12-offchain-worker.md)
13. [13 — Data Flow](./13-data-flow.md)
14. [14 — Security](./14-security.md)
15. [15 — Gas Cost](./15-gas-cost.md)
16. [16 — Testnet](./16-testnet.md)
17. [17 — AI Decision Contract](./17-ai-decision-contract.md)
18. [18 — Dashboard and API](./18-dashboard-and-api.md)
19. [19 — Demo Script](./19-demo-script.md)
20. [20 — Roadmap](./20-roadmap.md)
21. [21 — Ideathon Pitch](./21-ideathon-pitch.md)
22. [22 — Antigravity Master Prompt](./22-antigravity-master-prompt.md)
23. [DECISIONS — Architecture Decisions](./DECISIONS.md)

## Source-of-truth rule

The Creditcoin documentation supplied for this project establishes the Attestcoin concepts: source-chain event contracts, Attestcoin Smart Contracts, Merkle and continuity proofs, the Block Prover Precompile, Proof Builder, offchain readability workers, testnet environments, and the SDK. Project-specific behavior is defined here.

Do not claim that AI itself proves blockchain facts. AI consumes facts after the proof pipeline has established them.

## Implementation rule

Every feature should map to:

- a requirement;
- a component;
- an input/output contract;
- a test;
- and a demo-visible result.

If a feature cannot be explained in those five terms, do not add it to the MVP.
