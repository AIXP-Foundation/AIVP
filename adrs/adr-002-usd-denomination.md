# ADR-002: USD Denomination with Multi-Stablecoin Settlement

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

AIVP needs a pricing denomination for contracts. No universal AI compute pricing unit exists — this remains a gap in the industry.

Key considerations:
- USDC depegged to $0.87 in March 2023 (SVB incident, lasted 3 days)
- GENIUS Act (US, signed July 2025) allows government to freeze/burn stablecoins
- MiCA (EU, full enforcement July 2026) requires compliance for stablecoin issuers
- AI inference costs drop 50-200x per year — any compute-anchored unit devalues rapidly
- Single-stablecoin dependency is a systemic risk for escrowed funds

Candidates considered: USD denomination, USDC-only, custom unit (AIV), compute-anchored unit, floating token.

## Decision

All AIVP contracts are denominated in USD. Settlement occurs in seller-specified stablecoins/crypto:

- **Denomination**: USD (abstract fiat unit, not any specific stablecoin)
- **Settlement**: seller specifies accepted assets (e.g., `["USDC", "USDT", "DAI"]`)
- **Seller preference**: seller sets a preferred settlement asset (e.g., `"USDC"`)
- **Buyer payment**: buyer pays in any crypto → AIVP Solver converts to seller's preferred asset
- **Logic Vault**: holds stablecoins (not volatile assets)
- **Depeg circuit breaker**: if any settlement asset deviates >2% from USD peg, auto-switch to next accepted asset; pause milestone releases if all depeg

## Rationale

1. **Zero cognitive cost** — everyone knows what $50 USD means
2. **No single-stablecoin dependency** — survives USDC/USDT/DAI individual failures
3. **Regulatory resilience** — if one stablecoin is frozen/banned, settlement continues via alternatives
4. **Industry aligned** — international trade uses USD denomination with flexible settlement
5. **Seller choice** — seller controls which assets they receive

## Consequences

### Positive

- Resilient to individual stablecoin failures
- Cross-platform comparability (USD is universal)
- Regulatory flexibility across jurisdictions

### Negative

- Requires price oracle for USD/crypto conversion rates
- Slightly more complex than USDC-only
- Oracle itself is a dependency (mitigated by using multiple oracle sources)

### Neutral

- Contract amounts are stable in USD terms regardless of crypto market volatility
- Settlement asset diversity increases over time as more stablecoins become available

---

Align Axiom 0: Human Sovereignty and Wellbeing. Version: AIVP V1.0.0. www.aivp.dev
