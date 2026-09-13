# Project 7: Microfinance Loan Default Risk Prediction Model

**A logistic-regression credit-risk model for microfinance lending, with its fitted coefficients embedded directly as live spreadsheet formulas**

| | |
|---|---|
| **Domain** | Microfinance / Credit Risk Modelling / Statistics |
| **Deliverable** | `Microfinance_Default_Prediction_Model.xlsx` |
| **Skills demonstrated** | Logistic regression, model validation (decile/gains table, KS statistic, confusion matrix), translating a fitted statistical model into an auditable spreadsheet, credit-risk interpretation |

---

## 1. The Real-World Problem

Microfinance institutions in Pakistan — Akhuwat, Kashf Foundation, FINCA Pakistan, the National Rural Support Programme (NRSP) Microfinance Bank, and others — extend small, often uncollateralised loans to low-income borrowers with no access to conventional banking. Because loan sizes are small and volumes are high, an MFI cannot afford a manual credit-committee review for every applicant the way a commercial bank does for a large corporate loan. It needs a fast, statistically grounded, and auditable way to estimate default risk from a handful of application-time variables — and, just as importantly, a way to **prove the model actually works** before relying on it.

## 2. The Solution

A logistic regression — the industry-standard technique for binary credit-risk prediction, and the same core method behind real Basel-style probability-of-default models — fitted on 200 synthetic microfinance loans using 8 predictors: loan amount, loan term, borrower age, monthly income, number of dependents, prior loans completed, a group/joint-liability lending flag, and a guarantor-present flag.

The model was fitted **offline in Python (scikit-learn)** on standardised inputs, and the fitted coefficients were then embedded directly as **live Excel formulas** — `score = intercept + Σ(coefficient × standardised value)`, `probability = 1/(1+EXP(-score))` — so every one of the 200 loans' predicted default probability recalculates inside the spreadsheet itself, with no hidden black-box step between the statistics and the workbook.

Beyond scoring, `Model Validation` runs the model through the checks a real credit-risk team would demand before trusting it:
- A **decile (gains) table** — loans ranked into 10 equal groups by predicted probability, with the *actual* default rate compared per group (a well-behaved model shows this rising monotonically).
- The **Kolmogorov-Smirnov (KS) statistic**, the standard measure of a scorecard's ability to separate good from bad borrowers.
- A **confusion matrix and accuracy/precision/recall** at a chosen probability cutoff (30%).

## 3. Key Findings

- The model rank-orders risk well: actual default rate rises close to monotonically from the lowest-risk decile to the highest, with a KS statistic comfortably above the ~20% threshold generally considered acceptable discrimination for a credit scorecard.
- **Monthly income and loan amount are the two strongest predictors** of default risk, and they point in mutually reinforcing directions (higher income lowers risk, a larger loan raises it) — consistent with the well-established microfinance finding that affordability relative to income matters more than almost any other single factor.
- **Group/joint-liability lending and a guarantor's presence both measurably reduce predicted default risk** — a quantified confirmation of the core insight behind the Grameen-style group-lending model: social collateral can substitute for financial collateral.
- At the chosen 30% cutoff, the confusion matrix shows the trade-off an MFI actually has to manage: catching more true defaulters (recall) always costs some false rejections of good borrowers (precision) — a policy choice, not a purely statistical one.

## 4. Why This Project

Paired with Project 2, this shows both ends of a real credit-risk model's lifecycle: Project 2 is an expert-judgment points scorecard suited to a brand-new alternative-data product with no repayment history yet; this project shows what happens once real outcomes exist — fitting an actual statistical model and *validating it properly* rather than just presenting a score. That validation discipline (decile tables, KS statistics, confusion matrices) is what separates a real credit-risk practice from a spreadsheet that merely looks plausible, and demonstrates a level of technical rigor relevant to both fintech risk teams and development-finance institutions funding microfinance at scale.

## 5. Limitations & Future Work

- All 200 loan records and outcomes are synthetic, generated from a known statistical process for this exercise — not real borrower data, and the model is validated in-sample rather than on a held-out test set.
- A production version would (a) hold out a genuine test sample, (b) re-fit periodically as new repayment outcomes arrive, and (c) monitor for population drift the same way Project 2's extension notes suggest.
- Next step: benchmark the logistic regression against a gradient-boosted tree model on the same data to quantify how much (if any) additional discriminatory power a more complex model buys over the fully auditable logistic version — a real trade-off MFIs and regulators weigh explicitly.
