# 11 — Interfaces and Data Contracts

This document defines the boundaries between ProofMind components. Keep these shapes stable even if the implementation language changes.

## 1. Source event

Conceptual event:

```solidity
event CreditActionRequested(
    bytes32 indexed requestId,
    address indexed user,
    uint256 amount,
    uint256 collateralValue,
    bytes32 assetId
);
```

The exact event should be finalized with the source-chain contract. The important requirement is that the event is dedicated to the cross-chain action and contains all data needed by the destination application.

## 2. Worker event record

```json
{
  "requestId": "0x...",
  "sourceChainKey": 1,
  "sourceTxHash": "0x...",
  "sourceBlockNumber": 0,
  "sourceContract": "0x...",
  "eventName": "CreditActionRequested",
  "detectedAt": "ISO-8601",
  "status": "DETECTED"
}
```

## 3. Proof result

```json
{
  "requestId": "0x...",
  "sourceTxHash": "0x...",
  "chainKey": 1,
  "blockHeight": 0,
  "merkleProof": [],
  "continuityProof": [],
  "encodedTransaction": "0x..."
}
```

The actual SDK/Proof Builder response must be used when implementing this object. Do not fabricate field names for a real API request.

## 4. Verified fact

```json
{
  "requestId": "0x...",
  "sourceTxHash": "0x...",
  "sourceChainKey": 1,
  "eventType": "CreditActionRequested",
  "subject": "0x...",
  "amount": "1000000000000000000",
  "asset": "TEST",
  "verified": true,
  "verifiedBy": "attestcoin-asc",
  "verifiedAtBlock": 0
}
```

This is the only class of blockchain-derived information that the AI decision layer should consume.

## 5. AI decision

The model should return machine-readable output:

```json
{
  "decision": "APPROVE",
  "confidence": 0.87,
  "reasonCodes": ["COLLATERAL_PRESENT", "AMOUNT_WITHIN_LIMIT"],
  "factsUsed": ["0x..."],
  "requestedAction": {
    "actionType": "CREATE_CREDIT_ACTION",
    "amount": "..."
  }
}
```

The application must validate this structure before it reaches the policy layer.

## 6. Policy result

```json
{
  "allowed": true,
  "reason": "AI recommendation satisfies deterministic policy",
  "maxAllowedAmount": "...",
  "expiresAt": "ISO-8601"
}
```

## Interface principle

**AI output is advisory; policy output is authoritative; smart-contract verification is the final execution boundary.**
