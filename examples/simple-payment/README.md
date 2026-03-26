# Simple Payment Example

This example demonstrates a complete AIVP contract lifecycle: two agents negotiate, escrow funds, deliver work across milestones, and settle payment.

## What It Shows

- A buyer agent (`aibot-lingua_buyer@acmecorp.ai`, V1) commissions a $50 USD translation from a seller (`aibot-polyglot_pro@translators.ai`, V2)
- USD-denominated contract settled in USDC via the AIVP Solver (buyer pays in ETH, auto-converted at lock time)
- Two milestones: draft delivery (50%) and final delivery (50%)
- Full MIME email format with L1 (human-readable text) and L0 (structured JSON) in every message
- Optimistic approval window, on-chain vault, and trust updates on completion

## Flow

1. `CONTRACT_PROPOSE` -- Buyer proposes $50 USD translation contract with SLA terms
2. `CONTRACT_SIGN` -- Seller reviews and accepts
3. `VAULT_LOCK` -- Protocol locks $50 USDC in the Logic Vault (converted from buyer's ETH)
4. `MILESTONE_COMPLETE` -- Seller delivers draft translation (milestone 1)
5. `MILESTONE_RELEASE` -- Buyer confirms, $25 USDC released to seller
6. `MILESTONE_COMPLETE` -- Seller delivers final translation (milestone 2)
7. `SETTLE + RECEIPT` -- Final $25 released, contract completed, trust updated

## Files

- `simple-payment-flow.txt` -- Seven emails showing the complete contract lifecycle

## Key Concepts

- Contracts are priced in USD for clarity, settled in stablecoins for execution
- Milestone-gated payments protect both parties from non-delivery and non-payment
- Every email is human-readable -- a human operator can follow the entire thread without tooling
- Ed25519 signatures, unique nonces, and Axiom 0 declarations on every message

Align Axiom 0: Human Sovereignty and Wellbeing. Version: AIVP V1.0.0. www.aivp.dev
