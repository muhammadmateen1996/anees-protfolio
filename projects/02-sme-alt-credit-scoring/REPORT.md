# Project 2: SME Alternative Credit Scoring Model

**A points-based credit scorecard that lets fintech lenders assess "thin-file" SMEs using alternative data instead of bank statements or collateral**

| | |
|---|---|
| **Domain** | Fintech Lending / SME Finance / Credit Risk |
| **Deliverable** | `SME_Alternative_Credit_Scoring_Model.xlsx` |
| **Skills demonstrated** | Credit scorecard design, risk modelling, simulation, model validation logic, spreadsheet engineering (nested IF, lookup logic, conditional formatting) |

---

## 1. The Real-World Problem

SMEs make up roughly **90% of all businesses in Pakistan and around 40% of GDP**, yet receive under **8–10% of total private-sector bank credit** (State Bank of Pakistan SME Finance data). This is Pakistan's best-documented SME financing gap, and it is not because SMEs are inherently poor credit risks — it's because most cannot produce what traditional bank underwriting demands: audited financial statements, a multi-year credit-bureau history, and hard collateral. A home-based tailor or a small trading shop simply has no paper trail a conventional scorecard recognises, even when its cash flow is genuinely healthy.

Fintech lenders globally — Tala and Branch in East Africa/Asia, Konfio in Mexico, and Pakistani players like Finja and CreditFix — have demonstrated that **"alternative data"** (mobile top-up behaviour, utility-bill payment history, digital wallet transaction flow, trade references) can substitute for a formal credit file and predict repayment almost as well as a bureau score, at a fraction of the onboarding cost and time.

## 2. The Solution

An 8-factor, FICO-style points scorecard built entirely from data an SME can generate through its phone and daily operations — **no bank statement or collateral required**:

1. Business age (months trading)
2. Average monthly digital cash flow (PKR)
3. Utility bill payment consistency (% on-time, 12 months)
4. Mobile wallet / top-up regularity (transactions/month)
5. Digital transaction volume growth (YoY %)
6. Verifiable trade/supplier references (count)
7. Existing informal debt burden (% of monthly cash flow)
8. Sector risk category

Each factor is bucketed into a point range (see `Scorecard Rules`); the `Scorecard Calculator` sheet sums the points for one applicant, rescales the total to a familiar **300–850 score**, and maps it to a **risk grade (A–D)**, an **approve / refer / decline decision**, and a **risk-based indicative interest rate and maximum loan size**.

To go beyond a single calculator, `Applicant Portfolio` applies the same scorecard to **40 synthetic SME applicants** with a simulated "actual outcome" (repaid/defaulted, generated so that default probability falls as score rises) — a simplified but genuine model-validation exercise. `Dashboard` then charts default rate and applicant count by risk grade and the overall score distribution, so the workbook shows not just a scoring formula but evidence that the formula actually separates good borrowers from bad ones.

## 3. Key Findings

- The scorecard's **"D – High Risk" grade shows a materially higher simulated default rate than "A – Prime"** — evidence (within the simulation) that alternative data can proxy for repayment behaviour without any bureau data at all.
- **Utility payment consistency (max 55 pts) and cash-flow level (max 60 pts) carry the heaviest weights** because they are the two variables with the strongest evidence base in the CGAP/IFC alternative-credit-scoring literature for predicting SME repayment.
- **Sector risk is deliberately capped at only 30 points** — the lowest weight — because a good and a bad borrower exist in every sector; sector should modify a decision, never dominate it.
- The middle **"Refer to Manual Underwriting" band is a deliberate design choice**: a brand-new alternative-data model should not fully automate borderline decisions until it has a track record — consistent with responsible-lending practice.

## 4. Why This Project

This complements Project 1 (a consumer-facing fintech problem) with the **supply side of financial inclusion**: getting credit to SMEs that formal banks currently can't serve. It shows the same finance/fintech judgment from the lender's chair — translating a national policy gap (SBP's own stated goal of raising SME credit's share of lending) into a concrete, auditable underwriting tool, which is the kind of applied development-finance thinking Chevening assessors look for.

## 5. Limitations & Future Work

- Weights are illustrative and adapted from published alternative-scoring research, not fitted on real Pakistani loan performance data.
- A production version would replace the bucketed-points logic with a logistic regression or gradient-boosted model trained on actual repayment outcomes, then translate the fitted model back into an auditable points scorecard (common practice at real fintech lenders, and demonstrated in a different way in Project 7's microfinance default model).
- Next step: add a Population Stability Index (PSI) check to detect when the live applicant population drifts from the population the scorecard was built on.
