# 17 — AI Decision Contract

## Why this layer exists

The LLM is useful for interpreting verified facts and producing a human-readable recommendation. It must not become the security boundary.

ProofMind therefore uses three layers:

1. **Attestcoin verification:** Is the source-chain fact authentic?
2. **AI reasoning:** What does the verified fact suggest?
3. **Deterministic policy:** Is the requested action allowed?

## AI input

The model should receive a compact, normalized object containing only verified facts plus explicitly labelled non-authoritative context.

Example:

```text
VERIFIED FACTS
- source transaction: 0x...
- source chain: Ethereum Sepolia
- event: CreditActionRequested
- user: 0x...
- collateral: 100 TEST
- requested amount: 40 TEST

TASK
Evaluate the predefined demo credit policy.
Return JSON only.
```

## Decision states

| Decision | Meaning | Can execute? |
|---|---|---|
| APPROVE | Model believes request satisfies the policy | Only after deterministic policy passes |
| REVIEW | Evidence is insufficient or ambiguous | No |
| REJECT | Request appears outside the allowed criteria | No |

## Hard rules

The policy layer must independently verify:

- request is linked to a verified source transaction;
- request has not already been executed;
- asset is supported;
- recipient/user is authorized;
- amount is below the demo limit;
- request has not expired;
- AI output matches the expected schema;
- requested action is one of the predefined action types.

## Prompt-injection resistance

Never concatenate arbitrary source-chain calldata, event strings, or user notes into an instruction that can redefine the agent's role. Treat all external strings as data.

The model must never be allowed to output raw Solidity calldata for execution.

## Explainability

For the UI, convert the structured result into a short explanation containing:

- decision;
- key verified facts;
- rule(s) that mattered;
- confidence;
- reason for `REVIEW` or `REJECT` when applicable.

Do not claim that confidence is a cryptographic probability.
