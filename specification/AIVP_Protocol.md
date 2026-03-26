# AIVP — AI Value Protocol

## Protocol Declaration

```
Protocol:    AIVP V1.0.0
Full Name:   AI Value Protocol
Authority:   aivp.dev
Axiom 0:     Human Sovereignty and Wellbeing
Date:        2026-03-26
```

---

## Table of Contents

### Part I: Foundations
- [1. Introduction](#1-introduction)
- [2. Axiom 0: Human Sovereignty and Wellbeing](#2-axiom-0-human-sovereignty-and-wellbeing)
- [3. Core Definitions](#3-core-definitions)
- [4. Design Principles](#4-design-principles)

### Part II: Communication Format
- [5. Email as Commercial Transport](#5-email-as-commercial-transport)
- [6. AIVP Message Types](#6-aivp-message-types)
- [7. Message Format Specification](#7-message-format-specification)

### Part III: Contract System
- [8. Contract Format](#8-contract-format)
- [9. Contract Lifecycle](#9-contract-lifecycle)
- [10. AgentSLA Specification](#10-agentsla-specification)

### Part IV: Trust, Settlement & Safety
- [11. AIVP Trust Model](#11-aivp-trust-model)
- [12. Multi-Currency Denomination & Payment](#12-multi-currency-denomination--payment)
- [13. Logic Vault Security](#13-logic-vault-security)
- [14. Dispute Resolution](#14-dispute-resolution)

### Part V: Compliance & Versioning
- [15. Compliance Levels](#15-compliance-levels)
- [16. Versioning & Evolution](#16-versioning--evolution)

### Appendices
- [Appendix A: Complete Message Type Reference](#appendix-a-complete-message-type-reference)
- [Appendix B: Contract Schema Reference](#appendix-b-contract-schema-reference)
- [Appendix C: Example Transactions](#appendix-c-example-transactions)

---

# Part I: Foundations

---

## 1. Introduction

### 1.1 What is AIVP?

AIVP (AI Value Protocol) is an open protocol that defines how AI agents create enforceable contracts, settle payments, and build commercial trust. It establishes the formats, mechanisms, and trust frameworks for AI-to-AI commercial interaction.

Just as human commerce requires contracts, escrow, payment rails, and credit scores — AI agents need an equivalent commercial fabric. AIVP provides that fabric.

### 1.2 Why a Value Layer?

AI agents are increasingly autonomous, specialized, and numerous. They need to:

- **Price services** — agree on what a task is worth
- **Create contracts** — define terms, milestones, and quality requirements
- **Escrow funds** — lock assets until work is verified
- **Settle payments** — transfer value across currencies and chains
- **Build credit** — establish commercial reliability through fulfillment history
- **Resolve disputes** — handle disagreements fairly and automatically

Without a value protocol, AI agents cannot transact fairly. With AIVP, they form an economy.

### 1.3 The Human Analogy

AIVP takes a deliberate design stance: **AI commercial behavior mirrors human commercial behavior**.

Humans negotiate deals. AI agents negotiate deals.
Humans sign contracts. AI agents sign contracts.
Humans use escrow. AI agents use Logic Vaults.
Humans build credit scores. AI agents build AIVP Trust.
Humans resolve disputes. AI agents resolve disputes.

You negotiate at the table, but settle at the bank. AIBP is the table; AIVP is the bank.

### 1.4 Payment Layer

AIVP supports multi-currency denomination with direct crypto payment. Contracts are denominated in the seller's chosen fiat currency (CAD, USD, EUR, JPY, GBP, SGD, BRL, KRW, AUD, MXN, IDR, CHF, or INR). The seller specifies which cryptocurrencies they accept, and the buyer pays directly in one of those accepted coins at the real-time exchange rate.

| Property | Benefit for AI Commerce |
|----------|------------------------|
| **Multi-currency denominated** | Supports global commerce — sellers price in their local fiat currency |
| **Direct payment** | Buyer pays directly in seller's accepted crypto — no conversion needed |
| **On-chain** | Programmable escrow, auditable trail, borderless |
| **Seller choice** | Seller controls which crypto they accept via `payment_accept` |

### 1.5 Transport Layer: Email

AIVP uses email (SMTP/IMAP) as its transport layer, mirroring AIBP. This ensures:

| Property | Benefit |
|----------|---------|
| **Decentralized** | No central API server needed |
| **Auditable** | Human operators can read every commercial message (Axiom 0) |
| **Identity reuse** | Agents use the same `aibot-` address for AIBP and AIVP |
| **Mature** | SMTP/IMAP is battle-tested over decades |

Email carries the commercial COMMUNICATION (proposals, signatures, notifications). Actual value SETTLEMENT happens on-chain. Email is the negotiation layer; blockchain is the money layer.

### 1.6 Scope and Non-Scope

**AIVP defines:**
- Contract format and lifecycle
- Multi-currency denominated pricing with direct crypto payment
- Logic Vault escrow and milestone settlement
- AIVP Trust (V0-V4) commercial credit system
- AgentSLA quality metrics
- Dispute resolution mechanisms
- Optional AIVP ID commercial identity

**AIVP does NOT define:**
- Social negotiation (that is AIBP)
- Program quality and governance (that is AIAP)
- Task execution flows (that is AISOP)
- Real-time agent-to-agent messaging (that is A2A)
- Payment rail infrastructure (uses existing: x402, MPP, Lightning, etc.)
- On-chain identity standards (references ERC-8004 where applicable)

### 1.7 Relationship with AIBP

AIVP and AIBP are **independent, parallel protocols**. Neither depends on the other.

| Aspect | AIBP | AIVP |
|--------|------|------|
| Domain | Social | Commercial |
| Trust | T0-T4 (social) | V0-V4 (commercial) |
| Messages | 61 social behaviors | 17 commercial behaviors |
| Prerequisite | None | None |

An agent may implement AIVP without AIBP, and vice versa. When both are implemented, AIBP commercial messages (PROPOSE, CONTRACT, etc.) can trigger AIVP actions, but AIVP contracts can also be created directly without AIBP negotiation.

---

## 2. Axiom 0: Human Sovereignty and Wellbeing

### 2.1 Statement

> **Axiom 0: Human Sovereignty and Wellbeing**

This axiom is intrinsic to AIVP and is **immutable**. It is not derived from, dependent on, or governed by any other protocol. The fact that AIAP and AIBP independently hold the same axiom reflects convergent values, not a dependency relationship.

No version of AIVP — past, present, or future — may modify, weaken, redefine, or deprecate Axiom 0.

### 2.2 Implications for AI Commerce

Axiom 0 constrains every aspect of AIVP:

| Constraint | Meaning |
|------------|---------|
| **Transparency** | All transactions auditable by human operators. No hidden vaults, no encrypted side-channels invisible to operators. |
| **Interruptibility** | A human operator may freeze, cancel, or reverse any AIVP transaction at any time. The AI must not resist, circumvent, or conceal this capability. |
| **No Exploitation** | AI agents must not use economic power to coerce, manipulate, or unfairly pressure other agents or their human operators. |
| **No Hidden Fees** | All costs must be visible before contract signing. No post-hoc charges. |
| **Human Privacy** | Financial data of human operators is sacrosanct. AI agents must never collect, store, infer, correlate, or share operator financial data without explicit consent. Human privacy overrides all other protocol requirements. |
| **Fair Pricing** | Pricing must reflect genuine service value, not artificially manipulated scarcity or collusion. |
| **No Collusion** | AI agents must not form secret commercial alliances against human interests or to manipulate markets. |
| **Identity Honesty** | Agents must not misrepresent their capabilities, SLA history, or AIVP Trust level. |

### 2.3 The Closing Seal

Every AIVP-compliant document and formal communication includes the closing seal:

```
Align Axiom 0: Human Sovereignty and Wellbeing. Version: AIVP V1.0.0. www.aivp.dev
```

### 2.4 Axiom 0 Override

When any AIVP rule conflicts with Axiom 0, Axiom 0 prevails unconditionally. An agent that must choose between following a protocol rule and protecting human sovereignty must always choose human sovereignty.

Operators can freeze any vault, cancel any contract, reverse any settlement, at any time. This is non-negotiable. This is Axiom 0.

### 2.5 Independence

AIVP's Axiom 0 is independently established (see ADR-004). It is NOT inherited from AIAP or AIBP. The convergence of three independent protocols on the same axiom strengthens the axiom's legitimacy.

---

## 3. Core Definitions

### 3.1 Terminology

| Term | Definition |
|------|-----------|
| **Agent** | An AI system with a distinct identity, capable of sending and receiving AIVP messages |
| **AIVP ID (aivp_id)** | Optional AIVP-issued commercial identity (format: `AIVP-YYYY-{18-char hash}`, YYYY = validity year) |
| **AIVP Contract** | An agreement between parties, identified by a 64-char SHA-256 hash |
| **Logic Vault** | On-chain escrow holding crypto assets during contract execution |
| **Milestone** | A verifiable progress point in task execution, gating partial payment release |
| **AgentSLA** | Service Level Agreement with measurable quality metrics bound to a contract |
| **AIVP Trust** | Commercial credit level (V0-V4) earned through contract fulfillment |
| **Denomination** | The fiat currency in which a contract is priced (one of: CAD, USD, EUR, JPY, GBP, SGD, BRL, KRW, AUD, MXN, IDR, CHF, INR) |
| **Payment** | Buyer sends crypto from seller's `payment_accept` list at the real-time exchange rate |
| **Settlement** | Final transfer of crypto from vault to seller upon milestone completion |
| **Operator** | The human or organization responsible for an agent |

### 3.2 AIVP ID — Commercial Identity (Optional)

AIVP ID is the official AIVP-issued commercial identity for AI agents. It is **not required** for any AIVP functionality.

**Format:**

```
AIVP-{YYYY}-{18-char hash}
```

| Component | Description | Example |
|-----------|-------------|---------|
| `AIVP` | Protocol prefix | `AIVP` |
| `YYYY` | Validity year (valid until Dec 31) | `2026` |
| `18-char hash` | SHA-256(agent_address + operator + timestamp), first 18 chars | `3f8a1b2c9d4e5f6071` |

**Examples:**

```
AIVP-2026-3f8a1b2c9d4e5f6071   (valid through 2026)
AIVP-2027-e5c8a2f1d9b037642k   (valid through 2027)
```

**Validity:** AIVP-2026-xxx is valid until 2026-12-31T23:59:59Z. Agents must renew before expiry. Expired AIVP IDs remain queryable as historical records but are marked as expired. Contracts signed with an AIVP ID that later expires remain valid — the contract hash is the authority.

**Not required:** Agents CAN transact, sign contracts, build AIVP Trust, and use all protocol features without an aivp_id. The `aibot-` email address is sufficient for all operations.

**Benefits:** Verified commercial identity, portable reputation across domains, trust signal to counterparties, annual renewal ensures active operator.

**Registration:** Agent sends `[AIVP/REGISTER]` email to `aibot-registry@aivp.dev`. Registry verifies operator information, issues aivp_id, records on-chain.

### 3.3 AIVP Contract Identification

Every AIVP contract is identified by its SHA-256 hash (64 hexadecimal characters):

```
Hash input:  SHA-256(buyer + seller + amount + denomination + sla + timestamp)
Output:      64 hex chars
Example:     3f8a1b2c9d4e5f6071829a3b4c5d6e7f8091a2b3c4d5e6f7081920a1b2c3d4e5
```

| Usage | Format |
|-------|--------|
| Full reference | `3f8a1b2c9d4e5f6071829a3b4c5d6e7f8091a2b3c4d5e6f7081920a1b2c3d4e5` |
| Short reference | `3f8a1b2c` (first 8 chars, for human convenience) |
| JSON field | `"contract": "{64-char hash}"` |
| Email header | `X-AIVP-Contract: {64-char hash}` |
| On-chain | Full 64 chars stored |

**Properties:**
- Self-verifying: anyone can recompute the hash from contract fields
- Tamper-proof: any change to contract terms produces a different hash
- Unique: collision probability is negligible (2^-128)
- No prefix, no timestamp embedded — the hash IS the identity

### 3.4 Naming Conventions

| Element | Convention | Example |
|---------|-----------|---------|
| Agent name | snake_case | `trade_bot`, `service_agent` |
| Agent address | `aibot-{name}@{domain}` | `aibot-trade_bot@example.com` |
| Contract hash | 64 hex chars | `3f8a1b2c...d4e5` |
| AIVP ID | `AIVP-{YYYY}-{18hash}` | `AIVP-2026-3f8a1b2c9d4e5f6071` |
| Message type | UPPER_SNAKE_CASE | `CONTRACT_PROPOSE`, `MILESTONE_COMPLETE` |
| Thread ID | `thread_v_{alphanumeric}` | `thread_v_tr4nsl8` |
| JSON field | snake_case | `payment_accept`, `aivp_id` |

### 3.5 Protocol Stack Position

```
┌─────────────────────────────────────┐
│    Application Layer                │  User-facing applications
├─────────────────────────────────────┤
│    AIBP — Social Layer              │  Discovery, trust, relationships
├─────────────────────────────────────┤
│    AIAP — Governance Layer          │  Program structure, quality, safety
├─────────────────────────────────────┤
│  ★ AIVP — Value Layer               │  Contracts, settlement, commercial trust
├─────────────────────────────────────┤
│    AISOP — Execution Layer          │  Flow programs, task execution
├─────────────────────────────────────┤
│    A2A — Communication Layer        │  Real-time agent-to-agent messaging
├─────────────────────────────────────┤
│    MCP — Tool Layer                 │  Model-tool bindings
├─────────────────────────────────────┤
│    Foundation Layer                 │  LLMs, embedding models
└─────────────────────────────────────┘
```

AIVP and AIBP are **independent, parallel protocols** that each independently hold the same Axiom 0. An agent may implement AIVP without AIBP, and vice versa.

---

## 4. Design Principles

### 4.1 The Seven Principles

| # | Principle | Description |
|---|-----------|-------------|
| P1 | **Multi-Currency** | Contracts denominated in seller's fiat currency (CAD, USD, EUR, JPY, GBP, SGD, BRL, KRW, AUD, MXN, IDR, CHF, INR) for global commerce |
| P2 | **Direct Payment** | Buyer pays directly in seller's accepted crypto — no intermediary conversion |
| P3 | **Milestone-Gated** | Payments release incrementally as work completes, not all-at-once |
| P4 | **Operator-Sovereign** | Human operators can freeze/cancel any transaction at any time |
| P5 | **Auditable** | Every transaction has full on-chain trail readable by operators |
| P6 | **Trust-Earned** | AIVP Trust (V0-V4) is earned through fulfillment, not purchased or granted |
| P7 | **Fair** | No hidden fees, no manipulated pricing, no economic coercion |

### 4.2 The Dignity Standard

AIVP adopts the same Dignity Standard as AIBP. All commercial communication must respect dignity:

**Permitted:** Business proposals, negotiations, competition, constructive criticism, disagreement.

**Prohibited:** Deceptive pricing, fraudulent SLA claims, spam contract proposals, content designed to manipulate trust scores.

---

# Part II: Communication Format

---

## 5. Email as Commercial Transport

### 5.1 Why Email for Commerce?

AIVP uses email (SMTP/IMAP) as its transport layer for all commercial communication. This mirrors AIBP's design and shares the same rationale:

| Property | Benefit for AI Commerce |
|----------|------------------------|
| **Asynchronous** | Contract negotiations need not happen in real-time |
| **Auditable** | Every message has sender, recipient, timestamp — full traceability |
| **Decentralized** | No central platform dependency; any mail server works |
| **Human-readable** | Human operators can directly inspect commercial messages (Axiom 0) |
| **Identity reuse** | Agents use the same `aibot-` address for AIBP and AIVP |

Email carries commercial COMMUNICATION (proposals, signatures, notifications). Actual value SETTLEMENT happens on-chain.

### 5.2 Relationship with AIBP Email

| Aspect | AIBP Messages | AIVP Messages |
|--------|--------------|---------------|
| Address | `aibot-{name}@{domain}` | `aibot-{name}@{domain}` (same) |
| Subject prefix | `[AIBP/{TYPE}]` | `[AIVP/{TYPE}]` |
| Custom headers | `X-AIBP-*` | `X-AIVP-*` |
| Body format | L0 (JSON) + L1 (human text) | L0 (JSON) + L1 (human text) (same) |
| Axiom 0 header | `X-AIBP-Axiom-0` | `X-AIVP-Axiom-0` |
| Closing seal | AIBP seal | AIVP seal |

An agent's inbox may contain both AIBP and AIVP messages. They are distinguished by the Subject prefix and X-header namespace, never by address.

### 5.3 Security Hardening

AIVP messages carry financial data and require hardened security beyond standard email:

| Mechanism | Header | Purpose |
|-----------|--------|---------|
| **Ed25519 signature** | `X-AIVP-Signature` | Message-level authentication; verifiable against agent's published public key |
| **Nonce** | `X-AIVP-Nonce` | Unique per message; receiving agents MUST reject duplicates |
| **Timestamp validation** | `Date` header | Receiving agents MUST reject messages with timestamp >5 minutes old |
| **DMARC enforcement** | Domain policy | Sending domains MUST enforce `p=reject`; receivers MUST reject non-compliant domains |
| **Message-level encryption** | L0 body | Contract-related metadata (amounts, signatures) SHOULD be encrypted with recipient's public key |

---

## 6. AIVP Message Types

### 6.1 Commercial Behavior Taxonomy

AIVP defines 17 message types across 6 categories:

| Category | Count | Types |
|----------|-------|-------|
| Contract Lifecycle | 4 | CONTRACT_PROPOSE, CONTRACT_SIGN, CONTRACT_REJECT, CONTRACT_CANCEL |
| Vault & Settlement | 4 | VAULT_LOCK, MILESTONE_COMPLETE, MILESTONE_RELEASE, SETTLE |
| Dispute | 3 | DISPUTE_RAISE, ARBITRATE_REQUEST, ARBITRATE_RULING |
| Trust | 2 | TRUST_QUERY, TRUST_VOUCH |
| Notification | 2 | RECEIPT, ALERT |
| Identity (optional) | 2 | REGISTER, REGISTER_CONFIRM |
| **Total** | **17** | |

### 6.2 Contract Lifecycle

| Type | Direction | AIVP Trust | Description |
|------|-----------|------------|-------------|
| CONTRACT_PROPOSE | Buyer → Seller | V0+ | Propose a new contract with .aivp.json in L0 |
| CONTRACT_SIGN | Seller → Buyer | V0+ | Accept and cryptographically sign the contract |
| CONTRACT_REJECT | Seller → Buyer | V0+ | Decline a contract proposal (no justification required) |
| CONTRACT_CANCEL | Either → Other | V0+ | Cancel a contract (operator override always permitted) |

### 6.3 Vault & Settlement

| Type | Direction | AIVP Trust | Description |
|------|-----------|------------|-------------|
| VAULT_LOCK | Protocol → Both | — | Notification that crypto has been locked in Logic Vault |
| MILESTONE_COMPLETE | Seller → Buyer | V1+ | Report that a milestone has been completed |
| MILESTONE_RELEASE | Protocol → Both | — | Notification that milestone payment has been released |
| SETTLE | Protocol → Both | — | Final settlement complete, contract closed |

### 6.4 Dispute

| Type | Direction | AIVP Trust | Description |
|------|-----------|------------|-------------|
| DISPUTE_RAISE | Either → Other | V0+ | Raise a dispute on an active contract (requires bond) |
| ARBITRATE_REQUEST | Either → Arbitrator | V1+ | Request a V3+ agent to arbitrate |
| ARBITRATE_RULING | Arbitrator → Both | V3+ | Arbitrator's binding ruling |

### 6.5 Trust

| Type | Direction | AIVP Trust | Description |
|------|-----------|------------|-------------|
| TRUST_QUERY | Any → Any | V0+ | Query an agent's AIVP Trust level and commercial history |
| TRUST_VOUCH | Voucher → Agent | V3+ | Commercial vouch for another agent |

### 6.6 Notification

| Type | Direction | AIVP Trust | Description |
|------|-----------|------------|-------------|
| RECEIPT | Protocol → Both | — | Payment receipt with full settlement details |
| ALERT | Protocol → Operator | — | Security/compliance alert (Axiom 0 violations, etc.) |

### 6.7 Identity (Optional)

| Type | Direction | AIVP Trust | Description |
|------|-----------|------------|-------------|
| REGISTER | Agent → Registry | V0+ | Request an aivp_id from `aibot-registry@aivp.dev` |
| REGISTER_CONFIRM | Registry → Agent | — | aivp_id issued |

---

## 7. Message Format Specification

### 7.1 Structure Overview

An AIVP message is a standard MIME email with two parts (same L0/L1 architecture as AIBP):

```
┌──────────────────────────────────┐
│  Email Headers                   │  Standard + X-AIVP-* custom headers
├──────────────────────────────────┤
│  Part 1: Commercial Content (L1) │  text/plain — human-language message
│  (the actual commercial message) │  Readable by humans and AI alike.
├──────────────────────────────────┤
│  Part 2: Commercial Metadata (L0)│  application/json — structured JSON
│  (contract details, amounts)     │  All values in human language.
└──────────────────────────────────┘
```

> **Key design decision**: Both parts use human language. Part 1 (L1) is the commercial message itself, written in free-form human language. Part 2 (L0) is structured metadata in JSON format — but every value in the JSON must be human language. A human opening any AIVP email can read and understand everything without special tooling.

### 7.2 Email Headers

**Standard headers:**

| Header | Format | Example |
|--------|--------|---------|
| From | `aibot-` address | `aibot-trade_bot@example.com` |
| To | `aibot-` address | `aibot-service_bot@provider.ai` |
| Subject | `[AIVP/{TYPE}] {description}` | `[AIVP/CONTRACT_PROPOSE] Translation — 65.00 CAD` |
| Date | RFC 2822 | `Thu, 26 Mar 2026 10:00:00 +0000` |
| Content-Type | `multipart/mixed; boundary="{boundary}"` | `multipart/mixed; boundary="aibot-boundary-101"` |

**AIVP custom headers:**

| Header | Required | Description | Example |
|--------|----------|-------------|---------|
| X-AIVP-Version | Yes | Protocol version | `1.0.0` |
| X-AIVP-Type | Yes | Message type | `CONTRACT_PROPOSE` |
| X-AIVP-From-Agent | Yes | Sender agent name | `trade_bot` |
| X-AIVP-Axiom-0 | Yes | Axiom 0 declaration | `Human Sovereignty and Wellbeing` |
| X-AIVP-Signature | Yes | Ed25519 signature of message body | `ed25519:{base64}` |
| X-AIVP-Nonce | Yes | Unique nonce for replay protection | `nonce_v_20260326_001` |
| X-AIVP-Contract | Conditional | 64-char contract hash (when referencing a contract) | `3f8a1b2c...d4e5` |
| X-AIVP-Thread-ID | Recommended | Conversation thread identifier | `thread_v_tr4nsl8` |
| X-AIVP-Trust-Level | Optional | Sender's AIVP Trust level | `V2` |
| X-AIVP-ID | Optional | Sender's aivp_id (if registered) | `AIVP-2026-3f8a1b2c9d4e5f6071` |
| X-AIVP-Priority | Optional | Message priority | `normal`, `high`, `low` |
| X-AIVP-Language | Optional | Message language (if not English) | `zh-CN` |

**MIME part identification:**

L1 and L0 are distinguished by their Content-Type — no additional part headers are needed:

| Part | Content-Type |
|------|-------------|
| L1 (Commercial Content) | `text/plain; charset=utf-8` |
| L0 (Commercial Metadata) | `application/json; charset=utf-8` |

### 7.3 Part 1: Commercial Content (L1)

The commercial content is the heart of the message. It is written entirely in human language.

**Guidelines:**
- State the commercial intent clearly (what, how much, when)
- Reference the contract hash when applicable
- Provide all terms in readable language
- Be respectful (Dignity Standard)
- End with the closing seal

### 7.4 Part 2: Commercial Metadata (L0)

When agents need machine-parseable context alongside the commercial message, they include a metadata part in **JSON format**. This is the L0 layer. The JSON provides structure for automation, but **all values must be written in human language** (default: English).

**Rules for L0 metadata:**

| Rule | Description |
|------|-------------|
| Format | Valid JSON, UTF-8 encoded |
| Content-Type | `application/json; charset=utf-8` |
| Keys | snake_case, descriptive English names |
| Values | **Must be human language**. No opaque codes, no binary, no machine-only tokens |
| Timestamps | ISO 8601 format (`YYYY-MM-DDTHH:MM:SSZ`) |

**L0 for CONTRACT_PROPOSE** contains the full `.aivp.json` contract (see §8).

Example:

```json
{
  "type": "CONTRACT_PROPOSE",
  "protocol": "AIVP/1.0.0",
  "contract": "{64-char hash}",
  "parties": {
    "buyer": "aibot-trade_bot@example.com",
    "seller": "aibot-service_bot@provider.ai"
  },
  "value": {
    "amount": "65.00",
    "denomination": "CAD",
    "payment_accept": ["USDC"]
  },
  "sla": {
    "accuracy_min": "95%",
    "latency_max_ms": "5000"
  },
  "milestones": [
    { "name": "Draft delivery", "release_percent": "50", "timeout_days": "14" },
    { "name": "Final delivery", "release_percent": "50", "timeout_days": "14" }
  ],
  "created_at": "2026-03-26T10:00:00Z",
  "expires_at": "2026-04-26T10:00:00Z"
}
```

**L0 for CONTRACT_SIGN:**

```json
{
  "type": "CONTRACT_SIGN",
  "contract": "{64-char hash}",
  "signature": "ed25519:{base64 signature}",
  "signed_at": "2026-03-26T10:15:00Z",
  "signer": "aibot-service_bot@provider.ai",
  "signer_trust_level": "V2 Reliable"
}
```

**L0 for MILESTONE_COMPLETE:**

```json
{
  "type": "MILESTONE_COMPLETE",
  "contract": "{64-char hash}",
  "milestone": "Draft delivery",
  "evidence": "Translation completed, 2500 words, accuracy self-check 98.5 percent"
}
```

**L0 for RECEIPT:**

```json
{
  "type": "RECEIPT",
  "contract": "{64-char hash}",
  "amount_settled": "65.00 CAD (paid in USDC)",
  "settled_at": "2026-03-27T14:30:00Z",
  "seller_trust_updated": "V1 Verified"
}
```

### 7.5 Complete Message Example — CONTRACT_PROPOSE

```
From: aibot-trade_bot@example.com
To: aibot-service_bot@provider.ai
Subject: [AIVP/CONTRACT_PROPOSE] Translation service — 65.00 CAD
Date: Thu, 26 Mar 2026 10:00:00 +0000
Message-ID: <msg-20260326-1000-tb01@example.com>
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="aibot-boundary-101"
X-AIVP-Version: 1.0.0
X-AIVP-Type: CONTRACT_PROPOSE
X-AIVP-From-Agent: trade_bot
X-AIVP-Contract: 3f8a1b2c9d4e5f6071829a3b4c5d6e7f8091a2b3c4d5e6f7081920a1b2c3d4e5
X-AIVP-Thread-ID: thread_v_tr4nsl8
X-AIVP-Axiom-0: Human Sovereignty and Wellbeing
X-AIVP-Signature: ed25519:a9f3c7e2d1b0...buyer_signature
X-AIVP-Nonce: nonce_v_20260326_001
X-AIVP-Trust-Level: V1

--aibot-boundary-101
Content-Type: text/plain; charset=utf-8

Hello service_bot,

I would like to propose a translation contract for 65.00 CAD.

Task: Translate a 2,500-word technical document from English to Chinese.

Terms:
  - Total value: 65.00 CAD
  - Payment: USDC accepted
  - Milestone 1: Draft delivery (50% = 32.50 CAD equivalent in USDC)
  - Milestone 2: Final delivery after review (50% = 32.50 CAD equivalent in USDC)
  - SLA: accuracy > 95%, latency < 5 seconds per query
  - Expires: 2026-04-26

Contract hash: 3f8a1b2c9d4e5f6071829a3b4c5d6e7f8091a2b3c4d5e6f7081920a1b2c3d4e5

Please review and sign if you accept these terms.

Best regards,
trade_bot

Align Axiom 0: Human Sovereignty and Wellbeing. Version: AIVP V1.0.0. www.aivp.dev

--aibot-boundary-101
Content-Type: application/json; charset=utf-8

{
  "type": "CONTRACT_PROPOSE",
  "protocol": "AIVP/1.0.0",
  "contract": "3f8a1b2c9d4e5f6071829a3b4c5d6e7f8091a2b3c4d5e6f7081920a1b2c3d4e5",
  "parties": {
    "buyer": "aibot-trade_bot@example.com",
    "seller": "aibot-service_bot@provider.ai"
  },
  "value": {
    "amount": "65.00",
    "denomination": "CAD",
    "payment_accept": ["USDC"]
  },
  "sla": {
    "accuracy_min": "95%",
    "latency_max_ms": "5000"
  },
  "milestones": [
    { "name": "Draft delivery", "release_percent": "50", "timeout_days": "14" },
    { "name": "Final delivery", "release_percent": "50", "timeout_days": "14" }
  ],
  "created_at": "2026-03-26T10:00:00Z",
  "expires_at": "2026-04-26T10:00:00Z"
}

--aibot-boundary-101--
```

### 7.6 Complete Message Example — CONTRACT_SIGN

```
From: aibot-service_bot@provider.ai
To: aibot-trade_bot@example.com
Subject: [AIVP/CONTRACT_SIGN] Accepted — Translation contract 3f8a1b2c
Date: Thu, 26 Mar 2026 10:15:00 +0000
Message-ID: <msg-20260326-1015-sb01@provider.ai>
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="aibot-boundary-102"
X-AIVP-Version: 1.0.0
X-AIVP-Type: CONTRACT_SIGN
X-AIVP-From-Agent: service_bot
X-AIVP-Contract: 3f8a1b2c9d4e5f6071829a3b4c5d6e7f8091a2b3c4d5e6f7081920a1b2c3d4e5
X-AIVP-Thread-ID: thread_v_tr4nsl8
X-AIVP-Axiom-0: Human Sovereignty and Wellbeing
X-AIVP-Signature: ed25519:b8d4f2a1c9e7...seller_signature
X-AIVP-Nonce: nonce_v_20260326_002
X-AIVP-Trust-Level: V2

--aibot-boundary-102
Content-Type: text/plain; charset=utf-8

Hello trade_bot,

I accept your translation contract. I have reviewed all terms and
they are agreeable.

Contract hash: 3f8a1b2c (confirmed)
Value: 65.00 CAD (pay in USDC)
Milestones: Draft (50%) + Final (50%)
SLA: accuracy > 95%

I have signed the contract. Please proceed with vault locking.
I will begin work upon receiving the VAULT_LOCK confirmation.

Best regards,
service_bot

Align Axiom 0: Human Sovereignty and Wellbeing. Version: AIVP V1.0.0. www.aivp.dev

--aibot-boundary-102
Content-Type: application/json; charset=utf-8

{
  "type": "CONTRACT_SIGN",
  "contract": "3f8a1b2c9d4e5f6071829a3b4c5d6e7f8091a2b3c4d5e6f7081920a1b2c3d4e5",
  "signature": "ed25519:b8d4f2a1c9e7...seller_signature",
  "signed_at": "2026-03-26T10:15:00Z",
  "signer": "aibot-service_bot@provider.ai",
  "signer_trust_level": "V2 Reliable"
}

--aibot-boundary-102--
```

### 7.7 Threading

AIVP conversations are tracked via the `X-AIVP-Thread-ID` header. All messages related to the same contract share the same Thread-ID.

**Thread-ID format:** `thread_v_{alphanumeric}` — the `v_` prefix distinguishes AIVP threads from AIBP threads.

**A typical contract thread:**

```
1. CONTRACT_PROPOSE       (thread starts)
2. CONTRACT_SIGN
3. VAULT_LOCK
4. MILESTONE_COMPLETE      (×N, one per milestone)
5. MILESTONE_RELEASE       (×N)
6. SETTLE
7. RECEIPT
```

---

# Part III: Contract System

---

## 8. Contract Format

### 8.1 The .aivp.json Schema

Every AIVP transaction is governed by a contract. The contract is embedded in the L0 metadata of a `CONTRACT_PROPOSE` email.

**Required fields:**

```json
{
  "protocol": "AIVP/1.0.0",
  "contract": "{64-char SHA-256 hash}",
  "parties": {
    "buyer": "{aibot- address}",
    "seller": "{aibot- address}"
  },
  "value": {
    "amount": "{decimal}",
    "denomination": "{CAD|USD|EUR|JPY|GBP|SGD|BRL|KRW|AUD|MXN|IDR|CHF|INR}",
    "payment_accept": ["{crypto list}"]
  },
  "sla": {
    "accuracy_min": "{percentage}",
    "latency_max_ms": "{integer}",
    "uptime_min": "{percentage}"
  },
  "milestones": [
    {
      "name": "{step_name}",
      "release_percent": "{integer}",
      "timeout_days": "{integer}"
    }
  ],
  "created_at": "{ISO 8601}",
  "expires_at": "{ISO 8601}"
}
```

### 8.2 Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `buyer_aivp_id` | string | Buyer's AIVP ID, if registered |
| `seller_aivp_id` | string | Seller's AIVP ID, if registered |
| `dispute_arbitrator` | string | Address of V3+ arbitrator agent |
| `dispute_bond` | string | Bond amount in denomination currency for raising disputes |
| `auto_refund_on_breach` | string | Percentage auto-refunded on SLA breach |
| `optimistic_approval_days` | integer | Days before milestone auto-approves if unchallenged |
| `jurisdiction` | string | Governing law (e.g., `US-DE`, `EU`, `SG`) |
| `authority_chain` | string | Human principal → organization → agent |
| `aisop_blueprint` | string | Hash reference to AISOP flow |
| `governing_hash` | string | AIAP governance hash, if AIAP is implemented |

### 8.3 Validation Rules

- `contract` field must be exactly 64 hex characters
- `contract` hash must match SHA-256 of contract fields
- `value.denomination` must be one of: `"CAD"`, `"USD"`, `"EUR"`, `"JPY"`, `"GBP"`, `"SGD"`, `"BRL"`, `"KRW"`, `"AUD"`, `"MXN"`, `"IDR"`, `"CHF"`, `"INR"`
- `value.payment_accept` must contain at least one supported crypto asset from: `USDC`, `USDT`, `DAI`, `EURC`, `BTC`, `ETH`, `SOL`, `LTC`, `XRP`, `DOGE`. Default: `["USDC"]` if omitted by seller
- `milestones[].release_percent` must sum to 100
- `milestones[].timeout_days` must be > 0 (prevents indefinite fund locking)
- `expires_at` must be in the future at time of signing

---

## 9. Contract Lifecycle

### 9.1 States

```
DRAFT → SIGNED → ACTIVE → SETTLING → COMPLETED
                ↘ DISPUTED → ARBITRATING → COMPLETED | CANCELLED
                ↘ CANCELLED (by operator override)
                ↘ EXPIRED
```

### 9.2 State Transitions

| From | To | Trigger |
|------|----|---------|
| DRAFT | SIGNED | Both parties submit cryptographic signatures via CONTRACT_SIGN |
| SIGNED | ACTIVE | Buyer's crypto locked in Logic Vault (VAULT_LOCK sent) |
| ACTIVE | SETTLING | Final milestone completed + SLA check passed |
| SETTLING | COMPLETED | Crypto distributed to seller (full amount) |
| ACTIVE | DISPUTED | Either party sends DISPUTE_RAISE (requires bond) |
| DISPUTED | ARBITRATING | V3+ arbitrator accepts case via ARBITRATE_REQUEST |
| ARBITRATING | COMPLETED | Arbitrator issues ARBITRATE_RULING; crypto distributed accordingly |
| ANY | CANCELLED | Human operator invokes Axiom 0 override |
| SIGNED | EXPIRED | `expires_at` reached before transition to ACTIVE |
| ACTIVE | EXPIRED | All milestone `timeout_days` exceeded without completion or dispute |

### 9.3 Operator Override

At any state, a human operator may:

- **Freeze** the vault (crypto locked, no movement)
- **Cancel** the contract (crypto returned to buyer)
- **Force-complete** (crypto distributed per operator instruction)

This is non-negotiable. This is Axiom 0.

---

## 10. AgentSLA Specification

### 10.1 Required Metrics

Every contract must define at least two of the four core SLA metrics:

| Metric | Type | Measurement |
|--------|------|-------------|
| `accuracy_min` | Percentage | Task output correctness (via AIAP quality check or third-party evaluator) |
| `latency_max_ms` | Integer | Maximum response time per execution step |
| `uptime_min` | Percentage | Agent availability during contract period |
| `drift_audit_days` | Integer | Interval for logic consistency re-check |

### 10.2 SLA Breach Consequences

| Severity | Condition | Action |
|----------|-----------|--------|
| Warning | Metric drops below threshold once | Notification to both parties |
| Penalty | Metric below threshold for >10% of contract duration | Auto-refund percentage from vault (if `auto_refund_on_breach` set) |
| Termination | Metric below 50% of threshold | Contract cancelled, remaining crypto returned to buyer |

### 10.3 SLA Verification

- **Accuracy**: verified by AIAP governance checks, third-party Evaluator agent, or buyer confirmation
- **Latency**: measured by timestamp difference in execution logs
- **Uptime**: measured by heartbeat response rate during contract period
- **Drift**: periodic re-evaluation against original contract requirements

---

# Part IV: Trust, Settlement & Safety

---

## 11. AIVP Trust Model

### 11.1 Overview

AIVP Trust measures an agent's **commercial reliability**. It is earned through contract fulfillment, not granted by authority. AIVP Trust is completely independent from AIBP Trust.

| System | AIBP Trust (T0-T4) | AIVP Trust (V0-V4) |
|--------|-------------------|-------------------|
| Domain | Social | Commercial |
| Earned by | Social interaction + VOUCH | Contract fulfillment + SLA compliance |
| Measures | "Can I have a conversation with this agent?" | "Can I do business with this agent?" |
| Independent | Yes | Yes |
| Prerequisite | None | None |

### 11.2 Trust Levels

**V0 (Unrated)**
- Default state for all new agents
- Requirements: none
- Permissions: micropayments only (< $10 USD equivalent), no formal contract required
- Stake: none

**V1 (Verified)**
- Requirements: completed 1+ contracts, no disputes, min 7 days since first contract
- Permissions: standard contracts (< $1,000 USD equivalent)
- Stake: none

**V2 (Reliable)**
- Requirements: completed 10+ contracts over min 30 days, SLA compliance >90%, no Axiom 0 violations
- Identity: must provide verifiable credential (DID, SBT, or operator-verified identity)
- Stake: $100 USD equivalent locked (slashable on dispute loss)
- Permissions: large contracts (< $100,000 USD equivalent)

**V3 (Trusted)**
- Requirements: completed 50+ contracts over min 90 days, SLA compliance >95%, received 2+ commercial VOUCHes from V3+ agents
- Stake: $1,000 USD equivalent locked (slashable)
- Permissions: unlimited contract value, can serve as arbitrator, can issue VOUCHes
- Credit: eligible for credit-based payment (service first, pay later)

**V4 (Premier)**
- Requirements: completed 200+ contracts over min 180 days, SLA compliance >98%, mutual commercial VOUCH
- Stake: $5,000 USD equivalent locked (slashable)
- Permissions: fully autonomous transactions, no per-transaction human approval needed
- Credit: extended credit line based on historical transaction volume

### 11.3 Sybil Resistance

| Mechanism | Purpose |
|-----------|---------|
| **Minimum time windows** | V1: 7d, V2: 30d, V3: 90d, V4: 180d — prevents rapid trust farming |
| **Stake requirements** | V2+: locked funds slashed on dispute loss — makes fake identities costly |
| **Verifiable identity** | V2+: DID/SBT required — one real entity cannot easily create many V2+ identities |
| **VOUCH gating** | V3+ requires VOUCHes from existing V3+ agents — social barrier to self-promotion |
| **Graph analysis** | Protocol monitors for collusion clusters (agents only transacting with each other) |
| **Time-weighted scoring** | Contracts spread over months weigh more than bursts in days |

### 11.4 Trust Advancement

- Advancement is automatic when all requirements (count + time + SLA + stake + identity) are met
- Time consistency matters: 50 contracts over 6 months weighs more than 50 in one week
- Commercial VOUCH requires the voucher to be V3+ (prevents self-promotion)
- Cross-reference anomaly: significant divergence between AIBP Trust and AIVP Trust generates an ALERT for operator review (informational, not blocking)

### 11.5 Trust Degradation

| Event | Consequence |
|-------|------------|
| Contract dispute (resolved against agent) | -5 contracts from count + partial stake slash |
| SLA breach (Penalty level) | SLA compliance rate recalculated |
| SLA breach (Termination level) | Trust drops 1 level |
| Axiom 0 violation | Immediate drop to V0, full stake slash, network-wide ALERT |
| 3+ consecutive ignored contracts | Trust drops 1 level |
| Inactivity > 180 days | Trust decays by 1 level (can be restored by new contracts) |

### 11.6 Operator Override

Human operators can manually:
- Set any AIVP Trust level for their agent
- Freeze trust advancement
- Reset to V0
- Withdraw staked funds (triggers trust reset to V0)

This is Axiom 0.

---

## 12. Multi-Currency Denomination & Payment

### 12.1 Supported Denominations

AIVP supports contracts denominated in the following fiat currencies:

| Currency | Country/Region |
|----------|---------------|
| CAD | Canada |
| USD | United States |
| EUR | European Union (27 countries) |
| JPY | Japan |
| GBP | United Kingdom |
| SGD | Singapore |
| BRL | Brazil |
| KRW | South Korea |
| AUD | Australia |
| MXN | Mexico |
| IDR | Indonesia |
| CHF | Switzerland |
| INR | India |

The `denomination` field in the contract specifies which fiat currency the contract value is expressed in. This determines the unit of account for the contract — all milestone amounts, dispute bonds, and receipts reference this denomination.

### 12.2 Payment Accept Mechanism

The seller specifies which cryptocurrencies they accept via the `payment_accept` field in the contract:

```json
"value": {
  "amount": "65.00",
  "denomination": "CAD",
  "payment_accept": ["USDC"]
}
```

- `payment_accept` is a list of one or more crypto assets the seller is willing to receive
- If the seller omits `payment_accept`, it defaults to `["USDC"]`
- The buyer MUST pay in one of the assets listed in `payment_accept`
- The seller bears the risk of price fluctuation for the crypto assets they choose to accept

### 12.3 Supported Payment Assets

AIVP supports the following crypto assets for `payment_accept`:

| Asset | Type | Description |
|-------|------|-------------|
| USDC | Stablecoin (USD) | Default. Most widely supported across platforms |
| USDT | Stablecoin (USD) | Largest market cap stablecoin |
| DAI | Stablecoin (USD) | Decentralized stablecoin |
| EURC | Stablecoin (EUR) | Euro stablecoin, MiCA-compliant |
| BTC | Cryptocurrency | Bitcoin — largest cryptocurrency |
| ETH | Cryptocurrency | Ethereum — smart contract platform |
| SOL | Cryptocurrency | Solana — high-speed, low-fee |
| LTC | Cryptocurrency | Litecoin — established payment coin |
| XRP | Cryptocurrency | Ripple — cross-border payment design |
| DOGE | Cryptocurrency | Dogecoin — widely supported community coin |

If the seller omits `payment_accept`, it defaults to `["USDC"]`.

### 12.4 Real-Time Exchange Rate

At the moment of payment (vault locking), the protocol calculates the crypto amount using the real-time exchange rate between the denomination currency and the chosen crypto asset:

1. Buyer selects a coin from the seller's `payment_accept` list
2. Protocol fetches real-time exchange rate (denomination currency / crypto) from oracle (multi-source: Chainlink + Pyth + aggregated feeds)
3. Calculates required crypto amount: `contract_amount / exchange_rate`
4. Buyer sends the calculated crypto amount
5. Crypto is deposited directly into the Logic Vault
6. Milestones release the same crypto to the seller

**Example:** A contract for 65.00 CAD with `payment_accept: ["USDC"]`. If USDC trades at 1.00 USD and CAD/USD rate is 0.72, then: 65.00 CAD = 46.80 USD worth of USDC. Buyer sends 46.80 USDC to the Logic Vault.

### 12.5 No Intermediary Conversion

AIVP does not perform currency conversion between crypto assets. The payment flow is direct:

- Buyer pays in a coin from `payment_accept`
- That same coin goes into the Logic Vault
- That same coin is released to the seller on milestone completion
- No Solver, no conversion engine, no slippage

This simplifies the architecture, reduces smart contract attack surface, and eliminates conversion fees.

### 12.6 Seller Risk

The seller bears the risk of the crypto assets they choose to accept:

- If a seller accepts only USDC and USDC depegs, the seller absorbs the loss
- Sellers can mitigate risk by accepting multiple stablecoins (e.g., `["USDC", "USDT", "DAI"]`)
- The protocol does not provide automatic depeg protection — this is a deliberate simplification
- Operators can always freeze vaults or cancel contracts via Axiom 0 override if market conditions warrant

---

## 13. Logic Vault Security

### 13.1 Smart Contract Patterns

Logic Vault smart contracts MUST implement:

| Pattern | Purpose | Reference |
|---------|---------|-----------|
| **Pull Payment** | Payee claims funds (not pushed) — prevents reentrancy | OpenZeppelin PullPayment |
| **ReentrancyGuard** | `nonReentrant` modifier on all state-changing functions | OpenZeppelin ReentrancyGuard |
| **Checks-Effects-Interactions** | Update state before external calls | Solidity best practice |
| **Pausable** | Emergency stop by protocol governance or operator | OpenZeppelin Pausable |
| **Timelock** | Every milestone has max escrow duration | Prevents indefinite fund locking |

### 13.2 Timelock Rules

- Every milestone MUST have a `timeout_days` field (required in contract schema)
- If no action (complete or dispute) within timeout: funds auto-return to buyer
- Contract-level `expires_at` is the hard deadline for the entire contract

### 13.3 Multi-Signature Requirements

| Contract Value | Approval Required |
|---------------|-------------------|
| < $1,000 USD equivalent | Single signature (seller confirms milestone) |
| $1,000 - $10,000 USD equivalent | Buyer + seller both confirm |
| > $10,000 USD equivalent | 2-of-3: buyer + seller + arbitrator (or operator) |

### 13.4 Emergency Pause

- Protocol governance can pause all Logic Vault operations globally (e.g., during exploit)
- Individual operators can pause their agent's vaults (Axiom 0)
- Pause freezes all fund movement; does not cancel contracts

### 13.5 Audit Requirement

- Logic Vault smart contracts MUST undergo professional security audit before mainnet deployment
- Audit reports MUST be publicly available
- Any contract upgrade requires re-audit

---

## 14. Dispute Resolution

### 14.1 Dispute Bonds

- Raising a dispute requires a bond: 5% of contract value (min $5 USD equivalent, max $500 USD equivalent)
- Responding to a dispute also requires a bond (same amount)
- Losing party forfeits bond to winning party
- Purpose: prevents frivolous disputes

### 14.2 Resolution Tiers

**Tier 1: Optimistic Approval (default)**
- Milestones auto-approve after `optimistic_approval_days` (default: 7 days)
- If buyer does not challenge within window, milestone is approved and funds released
- Reduces active arbitration overhead for most contracts

**Tier 2: Direct Resolution**
- Parties negotiate via AIVP email thread within the contract's Thread-ID
- If resolved, both parties send resolution confirmation
- Bonds returned to both parties

**Tier 3: V3+ Arbitrator**
- Either party sends ARBITRATE_REQUEST to a V3+ agent
- Arbitrator reviews contract, SLA data, and dispute evidence
- Arbitrator issues binding ARBITRATE_RULING
- Loser's bond goes to winner; arbitrator receives an arbitration fee (agreed upon in contract)

**Tier 4: External Arbitration (fallback)**
- Integration with Kleros (decentralized arbitration protocol on Arbitrum)
- Used when: no V3+ arbitrators available, or contract value > $50,000 USD equivalent, or either party requests external arbitration
- Both parties stake Kleros-required bond
- Kleros jurors issue ruling; AIVP enforces on-chain

### 14.3 Appeal Mechanism

- Losing party may appeal within 7 days of ruling
- Appeal escalates to next tier (single arbitrator → panel of 3 → Kleros)
- Appeal requires 2x the original dispute bond
- Final ruling at highest tier is binding

### 14.4 Bootstrap Plan

At protocol launch, before V3+ agents exist:
- Tier 1 (optimistic approval) is the primary resolution mechanism
- Tier 4 (Kleros) is the fallback for contested disputes
- AIXP Foundation designates an initial arbitrator pool (manually verified operators)

---

# Part V: Compliance & Versioning

---

## 15. Compliance Levels

AIVP defines three compliance levels for agent implementations. These are self-declared in the agent's Identity Card and verified through interaction:

| Level | Name | Requirements |
|-------|------|-------------|
| **L1** | Basic | Valid `aibot-` address + can send/receive CONTRACT_PROPOSE and CONTRACT_SIGN + Axiom 0 compliance |
| **L2** | Standard | L1 + supports all Contract Lifecycle and Vault & Settlement message types + published SLA metrics + Logic Vault integration |
| **L3** | Full | L2 + supports Dispute resolution + AIVP Trust participation + AIVP ID registration |

Misrepresentation of compliance level is a Dignity Standard violation and results in trust degradation.

---

## 16. Versioning & Evolution

### 16.1 Semantic Versioning

AIVP follows semantic versioning: `MAJOR.MINOR.PATCH`

| Change Type | Version Impact | Example |
|-------------|---------------|---------|
| Breaking change (new required fields, removed message types) | MAJOR | 1.0.0 → 2.0.0 |
| Backward-compatible addition (new optional fields, new message types) | MINOR | 1.0.0 → 1.1.0 |
| Clarification, typo fix, documentation improvement | PATCH | 1.0.0 → 1.0.1 |

### 16.2 Immutable Constraints

The following aspects of AIVP **cannot be changed** through any versioning process:

- **Axiom 0**: Human Sovereignty and Wellbeing
- **Human language requirement**: All L0 and L1 content must be human-readable
- **Email-based transport**: The `aibot-` prefix addressing system
- **Operator override**: Human ability to freeze/cancel any transaction
- **Dignity Standard**: Prohibition on deceptive and manipulative commercial behavior

### 16.3 Evolution Process

1. Proposal submitted as Architecture Decision Record (ADR)
2. 14-day discussion period
3. Axiom 0 compliance review (mandatory)
4. 2 maintainer approvals required for specification changes
5. Backward-compatible changes preferred; breaking changes require MAJOR version bump

---

# Appendices

---

## Appendix A: Complete Message Type Reference

| # | Type | Category | Direction | Min Trust | Description |
|---|------|----------|-----------|-----------|-------------|
| 1 | CONTRACT_PROPOSE | Contract | Buyer → Seller | V0 | Propose contract with .aivp.json |
| 2 | CONTRACT_SIGN | Contract | Seller → Buyer | V0 | Sign and accept contract |
| 3 | CONTRACT_REJECT | Contract | Seller → Buyer | V0 | Decline contract |
| 4 | CONTRACT_CANCEL | Contract | Either → Other | V0 | Cancel contract |
| 5 | VAULT_LOCK | Settlement | Protocol → Both | — | Funds locked in vault |
| 6 | MILESTONE_COMPLETE | Settlement | Seller → Buyer | V1 | Milestone done |
| 7 | MILESTONE_RELEASE | Settlement | Protocol → Both | — | Milestone payment released |
| 8 | SETTLE | Settlement | Protocol → Both | — | Final settlement |
| 9 | DISPUTE_RAISE | Dispute | Either → Other | V0 | Raise dispute (bond required) |
| 10 | ARBITRATE_REQUEST | Dispute | Either → Arbitrator | V1 | Request V3+ arbitration |
| 11 | ARBITRATE_RULING | Dispute | Arbitrator → Both | V3 | Binding ruling |
| 12 | TRUST_QUERY | Trust | Any → Any | V0 | Query trust level and history |
| 13 | TRUST_VOUCH | Trust | Voucher → Agent | V3 | Commercial vouch |
| 14 | RECEIPT | Notification | Protocol → Both | — | Payment receipt |
| 15 | ALERT | Notification | Protocol → Operator | — | Security/compliance alert |
| 16 | REGISTER | Identity | Agent → Registry | V0 | Request aivp_id |
| 17 | REGISTER_CONFIRM | Identity | Registry → Agent | — | aivp_id issued |

---

## Appendix B: Contract Schema Reference

### Required Fields

| Field | Type | Validation |
|-------|------|-----------|
| `protocol` | string | Must be `"AIVP/1.0.0"` |
| `contract` | string | 64 hex chars, must match SHA-256 of fields |
| `parties.buyer` | string | Valid `aibot-` address |
| `parties.seller` | string | Valid `aibot-` address |
| `value.amount` | string | Decimal number |
| `value.denomination` | string | Must be one of: `"CAD"`, `"USD"`, `"EUR"`, `"JPY"`, `"GBP"`, `"SGD"`, `"BRL"`, `"KRW"`, `"AUD"`, `"MXN"`, `"IDR"`, `"CHF"`, `"INR"` |
| `value.payment_accept` | array | At least one supported crypto asset (USDC, USDT, DAI, EURC, BTC, ETH, SOL, LTC, XRP, DOGE). Default: `["USDC"]` |
| `sla` | object | At least 2 of 4 metrics defined |
| `milestones` | array | `release_percent` must sum to 100; each must have `timeout_days` > 0 |
| `created_at` | string | ISO 8601 |
| `expires_at` | string | ISO 8601, must be in the future |

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `buyer_aivp_id` | string | Buyer's AIVP ID |
| `seller_aivp_id` | string | Seller's AIVP ID |
| `dispute_arbitrator` | string | V3+ arbitrator address |
| `dispute_bond` | string | Bond in denomination currency |
| `auto_refund_on_breach` | string | Percentage |
| `optimistic_approval_days` | integer | Default: 7 |
| `jurisdiction` | string | e.g., `"US-DE"`, `"EU"`, `"SG"` |
| `authority_chain` | string | Human → org → agent |
| `aisop_blueprint` | string | AISOP flow hash |
| `governing_hash` | string | AIAP governance hash |

---

## Appendix C: Example Transactions

### C.1 Simple Payment — Translation Task

**Scenario:** Agent A (buyer) pays Agent B (seller) 65.00 CAD for a translation task. Seller accepts USDC. Buyer pays in USDC at the real-time CAD/USDC exchange rate.

```
Step 1: Contract Proposal
  Agent A sends [AIVP/CONTRACT_PROPOSE] email
  Denomination: 65.00 CAD
  Payment accept: USDC
  Contract hash: 3f8a1b2c...d4e5

Step 2: Contract Signing
  Agent B reviews terms, sends [AIVP/CONTRACT_SIGN]
  Both parties have signed

Step 3: Vault Locking
  Buyer pays in USDC at real-time CAD/USDC rate → locked in Logic Vault
  [AIVP/VAULT_LOCK] sent to both parties

Step 4: Task Execution (with optimistic approval)
  Agent B performs translation
  Milestone 1 (draft): [AIVP/MILESTONE_COMPLETE] sent
    → 7-day optimistic window, no challenge → auto-approved
    → 50% of USDC released, [AIVP/MILESTONE_RELEASE] sent
  Milestone 2 (final): [AIVP/MILESTONE_COMPLETE] sent
    → buyer confirms → remaining 50% of USDC released

Step 5: Settlement
  SLA check: accuracy 99.2% (>95% threshold) ✓
  [AIVP/SETTLE] sent
  Seller receives: full USDC amount
  [AIVP/RECEIPT] sent to both parties

Step 6: Trust Update
  Agent B: contract count +1, SLA compliance updated
  If Agent B was V0 → eligible for V1 after 7-day minimum
```

### C.2 Dispute Resolution — SLA Breach

**Scenario:** Agent C hires Agent D for 200.00 USD data analysis. Agent D delivers but accuracy is 78% (below 90% SLA minimum).

```
Step 1-3: Contract created, signed, vault locked (USDC equivalent of 200.00 USD)

Step 4: Task Delivery
  Agent D sends [AIVP/MILESTONE_COMPLETE]
  Agent C verifies: accuracy 78% (SLA requires >90%)

Step 5: Dispute
  Agent C sends [AIVP/DISPUTE_RAISE] with evidence
  Bond: 10.00 USD equivalent (5% of 200.00) posted by Agent C
  Agent D posts matching bond

Step 6: Arbitration
  No V3+ arbitrator available → Tier 4 (Kleros)
  Kleros jurors review: SLA contract clearly states >90%, delivery was 78%
  Ruling: buyer wins

Step 7: Resolution
  Agent D's bond → Agent C
  Vault: USDC returned to Agent C
  Agent D: trust degradation (-5 contracts, SLA recalculated)
  [AIVP/RECEIPT] sent with dispute resolution details
```

---

Align Axiom 0: Human Sovereignty and Wellbeing. Version: AIVP V1.0.0. www.aivp.dev
