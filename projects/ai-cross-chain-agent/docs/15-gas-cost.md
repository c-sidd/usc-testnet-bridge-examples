# 15 — Gas Cost

## Verification Cost Model

The Creditcoin Attestcoin Readability documentation gives an approximate relationship between CTC verification cost and continuity proof length:

```text
CTC Cost ≈ 2.3×10^-5 + 2.9×10^-7 × continuity hash count
```

## Example: Recent Transaction

A recent transaction may require about 10 continuity hashes.

Approximate verification cost:

```text
2.59 × 10^-5 CTC
```

## Example: Older Transaction

After a longer period, sparse checkpoints can result in about 1000 continuity hashes.

Approximate verification cost:

```text
3.13 × 10^-4 CTC
```

This is more than 10x higher than the recent example.

## Other Cost Factors

### Merkle Proof Size

Merkle proof size grows modestly with the number of transactions in a block and is described as a relatively small effect compared with continuity proof length.

### Transaction Decoding

Most transaction decoding is described as negligible, but unusually large transactions can be more expensive. The documentation gives an estimated maximum decoding workload of 0.0375 CTC.

## Design Implication

When practical, the worker should request verification soon after finalization so continuity proofs remain shorter.
