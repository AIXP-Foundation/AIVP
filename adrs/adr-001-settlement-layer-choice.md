# ADR-001: Multi-Rail Settlement Layer

## Status

Accepted

## Date

2026-03-26

## Deciders

AIVP Protocol Authors

## Axiom 0 Compliance

| Check | Result |
|-------|--------|
| Human Sovereignty preserved | Yes |
| Human Benefit demonstrated | Yes |
| Transparency maintained | Yes |
| Interruptibility preserved | Yes |
| No manipulation or collusion | Yes |

## Context

AIVP requires a settlement layer for actual value transfer between AI agents. AIBP uses email for social messages, but email cannot transfer value. AIVP needs actual asset movement, not just intent expression.

Industry landscape (2026):
- x402 (Coinbase): HTTP 402 + crypto stablecoins — simple but crypto-only, low real adoption (~$28K/day)
- MPP (Stripe+Tempo): multi-rail sessions — most agent-native, but brand new (launched 2026-03-18)
- ACP (Stripe): fiat checkout — production-proven but human-buyer-centric
- AP2 (Google): mandate-based authorization — broadest coalition (60+ partners) but complex

Candidates considered: traditional payment rails only, single blockchain, multi-chain intent routing, hybrid multi-rail.

## Decision

AIVP uses multi-rail settlement with intent-based routing:

- Supported rails: stablecoins (USDC/USDT/DAI), Ethereum, Solana, Bitcoin (Lightning + on-chain)
- Fiat rails supported via MPP/ACP bridge integration (not reinvented by AIVP)
- Settlement is abstracted — agents express value intent, AIVP Solver finds optimal path
- x402 compatible — AIVP can auto-respond to HTTP 402 using vault funds
- Prefer same-chain settlement to minimize bridge risk

## Rationale

1. **Programmable**: Smart contracts enable Logic Vault (escrow + milestone release)
2. **Borderless**: No jurisdiction lock-in, matches AIBP's decentralized philosophy
3. **Auditable**: On-chain transactions satisfy Axiom 0 transparency requirement
4. **Composable**: Integrates with x402, MPP, AP2 rather than competing with them
5. **Hybrid**: Industry data shows pure crypto adoption is weak; supporting fiat bridges ensures practical adoption

## Consequences

### Positive

- Zero-trust settlement — no intermediary needed for crypto rails
- Global 24/7 availability
- Compatible with existing agentic commerce stack

### Negative

- Blockchain latency (seconds to minutes, not milliseconds)
- Gas fees add cost to micro-transactions
- Multi-rail complexity increases implementation effort
- Regulatory uncertainty in some jurisdictions
- Cross-chain bridge risk ($2.8B+ stolen since 2022)

### Neutral

- Solver implementation is a protocol dependency that must be maintained
- Oracle feeds for USD/crypto rates introduce an external dependency

---

Align Axiom 0: Human Sovereignty and Wellbeing. Version: AIVP V1.0.0. www.aivp.dev
