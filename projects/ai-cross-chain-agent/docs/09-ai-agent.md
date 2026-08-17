# 09 — AI Agent

## Role

The AI agent operates after the cross-chain data has been verified. Its job is application-level reasoning, not cryptographic verification.

## Input

The first prototype should normalize verified event data into a structured object such as:

```json
{
  "sourceChain": "sepolia",
  "blockNumber": 0,
  "transactionHash": "0x...",
  "event": "ApplicationEvent",
  "actor": "0x...",
  "value": "0",
  "timestamp": 0
}
```

The exact fields will be defined after the primary use case is selected.

## Processing

1. Receive verified event data.
2. Validate the expected application event shape.
3. Extract relevant fields.
4. Apply the application's decision policy.
5. Produce a structured decision.
6. Send only an allowed action to the execution layer.

## Output Shape

```json
{
  "decision": "APPROVE",
  "action": "EXECUTE",
  "confidence": 0.0,
  "reason": "..."
}
```

The final execution contract should not blindly trust free-form model output. Actions should be constrained by deterministic contract rules.

## AI vs Verification Boundary

```text
Attestcoin = proves what happened
AI         = reasons about what it means
Contract   = enforces what can happen
```
