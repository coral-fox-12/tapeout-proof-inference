# Contracts (X Layer)

- `AttestationRegistry` — receiptId -> (promptHash, outputHash, modelId, timestamp).
  Written by the TapeOut circuit container after each inference.
- `VoucherAdapter` — accepts off-chain vouchers for paid calls; settles on-chain in
  batches. Stubbed until TapeOut's paid-call escrow deploys (do not fake a live flow).
