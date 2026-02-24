# offchain-attestations

Public registry of off-chain EAS attestations published by the [b1e55ed](https://github.com/P-U-C/b1e55ed) contributor system.

## What is this?

When a contributor registers in b1e55ed with `--attest`, the system:
1. Creates a signed off-chain EAS attestation (EIP-712, zero gas)
2. Automatically publishes it here as a GitHub Issue

Each issue contains the full signed attestation object and can be independently verified.

## Verification

Each attestation issue contains:
- `uid` — deterministic UID derived from the signature
- `attester` — the signing address
- `signature` — recoverable EIP-712 signature
- `eip712` — full typed data for signature recovery

To verify, recover the signer from the EIP-712 typed data and check it matches `attester`.

Reference implementation: [`engine/integrations/eas.py`](https://github.com/P-U-C/b1e55ed/blob/develop/engine/integrations/eas.py) — `EASClient.verify_offchain_attestation()`

## Query

Browse attestations: [Issues tab](../../issues?label=attestation)

Filter by label:
- `attestation` — all attestations
- `offchain` — all off-chain signed objects
