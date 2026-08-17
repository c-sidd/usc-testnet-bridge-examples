# 02 — Problem Statement

## Problem

AI applications can consume blockchain data, but an AI agent receiving data from an API or centralized oracle does not by itself establish the blockchain origin of that data.

For a cross-chain application, the system needs a trustworthy way to move relevant source-chain information to the destination-chain application.

## Traditional Simplified Flow

```text
Source Chain -> API / Oracle -> AI -> Smart Contract
```

The application may depend on the integrity and availability of an external data provider.

## ProofMind Flow

```text
Source Chain
     |
     v
Attestcoin Readability
     |
     v
Cryptographic Verification on Creditcoin
     |
     v
Verified Event Data
     |
     v
AI Agent
     |
     v
On-chain Business Logic
```

## Design Question

Can an AI agent make a useful decision using cross-chain blockchain data while keeping the data-provisioning layer verifiable through Creditcoin?

## Success Criterion

A successful prototype should demonstrate an end-to-end path from a source-chain event to verified data on Creditcoin, followed by an AI decision and a visible on-chain result.
