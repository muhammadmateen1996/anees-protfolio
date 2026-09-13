# Project 9: Digital Transaction Fraud Detection Model

**A rule-based fraud-scoring engine for mobile wallet transactions, tuned to Pakistan's dominant social-engineering fraud pattern and validated on a labelled sample**

| | |
|---|---|
| **Domain** | Fintech Risk / Fraud Analytics / Digital Payments Security |
| **Deliverable** | `Transaction_Fraud_Detection_Model.xlsx` |
| **Skills demonstrated** | Rule-based risk scoring, statistical outlier detection (Z-scores), model validation (decile table, KS statistic, confusion matrix), fraud-pattern-specific product judgment |

---

## 1. The Real-World Problem

Pakistan's mobile wallets (JazzCash, Easypaisa, SadaPay, NayaPay, bank apps) have made digital payments part of daily life for tens of millions of people — and fraud has scaled right alongside them. The State Bank of Pakistan and the FIA's Cyber Crime Wing regularly issue public advisories about the dominant fraud pattern in this market: not sophisticated hacking, but **social engineering** — fraudsters posing as bank/telco agents, tricking victims into sharing an OTP or SIM-swapping their number, then draining the wallet through a rushed, first-time transfer to an unfamiliar beneficiary. A fraud-detection system for this market has to be built around *that* specific pattern, not around the card-present fraud patterns most off-the-shelf Western fraud tools assume.

## 2. The Solution

A rule-based fraud-scoring engine applied to 300 sample transactions, combining **six signals grounded directly in the Pakistani mobile-wallet fraud pattern**:

- **R1 — Amount Outlier**: transaction amount is a statistical outlier (Z-score > 2.5) versus that specific account's own historical spending pattern, not a fixed threshold across all accounts.
- **R2 — High Velocity**: more than 4 transactions from the account in the same day.
- **R3 — New Beneficiary + Large Amount**: a first-time recipient combined with an above-average transfer — the classic social-engineering signature.
- **R4 — Unusual Hour**: a transaction between 11pm–5am combined with an above-average amount.
- **R5 — Device Change**: the transaction originates from a new/changed device, a common account-takeover indicator.
- **R6 — Failed-Login Pattern**: 3+ failed login attempts in the prior 24 hours immediately followed by a successful transaction.

Each rule contributes weighted points to a **Risk Score**, computed live in the `Transactions` sheet for every one of the 300 sample transactions; scores above a threshold are flagged **"REVIEW."** `Model Validation` then applies the same decile/gains-table, KS-statistic, and confusion-matrix approach used in Project 7 to prove the score actually works, and `Dashboard` visualises fraud rate by risk decile and how often each individual rule fires.

## 3. Verification

As with Project 8, I recalculated the workbook's formulas independently (via the `formulas` Python engine) rather than trusting them by inspection: sampled Risk Score and Flag cells matched their expected values exactly (e.g., a score of 60 correctly flags "REVIEW" against the 40-point threshold; a score of 25 correctly stays "OK"), and the KS statistic recomputed to **39.9%** — comfortably above the ~20% threshold generally considered acceptable discrimination, and consistent between the spreadsheet formulas and an independent Python calculation of the same logic.

## 4. Key Findings

- The combined risk score rank-orders fraud well: actual fraud rate rises with risk-score decile, with a KS statistic of 39.9% — the model meaningfully separates fraudulent from legitimate transactions using only features available at transaction time.
- **Rule 3 (new beneficiary + large amount) and Rule 5 (device change) carry the highest point weights** because they map most directly onto Pakistan's dominant fraud pattern — a victim, freshly social-engineered or SIM-swapped, making a single large, rushed transfer to someone they've never paid before. Generic anomaly rules built for card-fraud markets would miss this pattern entirely.
- The precision/recall trade-off at the chosen cutoff is deliberate: a lower cutoff catches more fraud but flags more genuine customers, creating real friction — a business decision the model exposes rather than makes on its own.

## 5. Why This Project

This project shows fraud-analytics thinking adapted to a *specific* market's actual fraud pattern rather than a generic textbook approach — a distinction that matters enormously in practice and demonstrates the kind of locally-grounded, evidence-based product judgment a Chevening panel looks for in someone who understands Pakistan's financial-technology landscape from the inside. It also complements Project 7's credit-risk validation toolkit (decile tables, KS statistic, confusion matrix) applied to a different fraud/risk problem, showing the same rigor is portable across risk domains.

## 6. Recommendation for a Live System

A flagged transaction should trigger **step-up verification** (a callback, a liveness check, or a mandatory cooling-off period before a first-time large transfer completes) rather than an automatic block — blocking legitimate customers erodes trust in digital wallets faster than fraud losses do, which matters enormously for a market where financial inclusion (see Project 6) depends on customers trusting these products. This mirrors SBP/FIA public guidance directly: the single most effective consumer protection against this fraud pattern is friction and verification at the moment of a large, first-time transfer — exactly what Rule 3 targets.

## 7. Limitations & Future Work

- All 300 transactions and fraud labels are synthetic, generated so the six rules have genuine (but imperfect) predictive power — not real user data.
- A production system would add device/IP reputation data, SIM-swap registry checks (where available from telcos), and beneficiary network analysis (has this beneficiary account received flagged transfers from other victims before?) — the single strongest signal in real-world social-engineering fraud rings, which this rule set does not yet capture.
