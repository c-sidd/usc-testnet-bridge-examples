# 07 — System Flow

## End-to-End Flow

1. A user submits a transaction on the source chain.
2. The source-chain contract performs required logic and emits a specific event.
3. The offchain worker detects the event.
4. The worker waits until the containing block is attested on Creditcoin.
5. The worker requests Merkle and continuity proofs from the Proof Builder.
6. The worker calls the Attestcoin Smart Contract with the proof package and encoded transaction data.
7. The ASC verifies the proofs synchronously using the Block Prover Precompile.
8. The verified event data becomes available to the dApp's application logic.
9. The AI agent evaluates the verified data.
10. The application produces a decision.
11. The allowed business action is executed through the Creditcoin smart-contract layer.
12. The UI can display verification and execution status.

## State Machine

```text
DETECTED
   |
   v
WAITING_FOR_ATTESTATION
   |
   v
PROOF_REQUESTED
   |
   +---- failure ---> RETRY_PROOF
   |
   v
ASC_SUBMITTED
   |
   +---- failure ---> RETRY_ASC
   |
   v
VERIFIED
   |
   v
AI_DECISION
   |
   v
EXECUTED
```

## Failure Handling

The worker must retain enough state to recover from shutdowns, avoid duplicate submissions, and retry temporary failures. Exact retry strategy will be defined during implementation.
