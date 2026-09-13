# Project 8: Fintech Startup 3-Statement Model & DCF Valuation

**A fully linked 5-year financial model and equity valuation for "PaySetu," a hypothetical Pakistani BNPL/digital-lending startup**

| | |
|---|---|
| **Domain** | Corporate Finance / Startup Valuation / Financial Modelling |
| **Deliverable** | `Fintech_Startup_3Statement_DCF_Model.xlsx` |
| **Skills demonstrated** | 3-statement financial modelling, double-entry integrity, DCF valuation, CAPM/cost of capital, sensitivity analysis, judgment about *which* valuation method fits the business |

---

## 1. The Real-World Problem

Every fintech lender or BNPL (buy-now-pay-later) startup faces a structural challenge that makes it fundamentally different from a typical SaaS or e-commerce business: to grow revenue, it must fund a growing book of customer receivables on its own balance sheet. That consumes far more cash than an ordinary working-capital cycle, and if a founder or analyst doesn't model it explicitly, they will badly misjudge how much funding the business actually needs, when it needs it, and — critically — how to value it correctly. Naively applying a textbook DCF to a lending business is a common and serious mistake.

## 2. The Solution

A fully linked **3-statement model** (Income Statement, Balance Sheet, Cash Flow Statement) for a hypothetical Pakistani BNPL startup, "PaySetu," built bottom-up from operating drivers (active users, GMV per user, take rate, cost of funds) rather than top-down assumed growth rates:

- **`Assumptions`** centralises every input so the whole model reruns from one place.
- **`Income Statement`** charges funding cost on the **receivables balance** (not total GMV) at an annual cost-of-funds rate — the economically correct way to cost a short-tenor lending book.
- **`Balance Sheet`** funds receivables mostly through an **asset-backed "warehouse" debt facility** (an 85% advance rate, the standard BNPL financing structure), with equity funding the operating loss and a cash buffer rather than the receivables themselves. All three statements are properly double-entry linked — the **Balance-Sheet CHECK row (Total Assets − Total Liabilities − Total Equity) computes to exactly zero every year, verified independently** (see Section 3), proving the model isn't hand-plugged.
- **`Cash Flow Statement`** reconciles Net Income to the cash landing on the balance sheet.
- **`DCF Valuation`** deliberately values the business using **Free Cash Flow to Equity (FCFE)**, discounted at the **Cost of Equity** (via CAPM), instead of a standard unlevered-FCF/WACC DCF — explained in detail below.
- **`Sensitivity`** shows the resulting equity value across a grid of Cost-of-Equity and terminal-growth assumptions.

### Why FCFE, not a standard unlevered DCF
A standard DCF discounts unlevered free cash flow — which implicitly treats the receivables build-up as funded by the firm's blended capital — at WACC. For a lending business, this **double-penalises** the model: receivables growth is already matched-funded by the warehouse debt facility, so subtracting the full receivables increase from unlevered FCF (which assumes no debt funding) understates cash flow so badly it produces a **negative, nonsensical enterprise value** for a genuinely valuable, growing lender (confirmed while building this model — see Section 3). The standard practice for valuing lending fintechs is to discount **FCFE**, which nets the debt-funded portion of receivables growth against the matching debt draw, directly at the cost of equity — arriving at a sensible equity value without that distortion.

## 3. Verification (this model was actually recalculated, not just formula-typed)

Because this workbook's integrity is the whole point, I recalculated every formula independently using a Python Excel-formula engine (the `formulas` package) rather than trusting the formulas by inspection alone:

- **Balance-Sheet CHECK row = 0** (to floating-point precision, ~1e-7) in all five years — the model's core integrity test passes.
- **DCF Equity Value = PKR ~1,331 million (₨133.14/share on a 10M-share illustrative cap table)** — recalculated independently and matched an independent hand-built Python model of the same logic to the rupee.
- The **naive unlevered-FCF/WACC version was also built and tested during development** and produced a negative enterprise value, exactly the failure mode described above — concrete evidence for why the FCFE approach was the right call, not just an assumption.
- The **Sensitivity grid** was checked cell-by-cell: equity value rises with terminal growth and falls as the cost of equity rises, in the correct direction across every row and column.

## 4. Key Findings

- The model shows a classic fintech J-curve: EBITDA is negative in Years 1–2, turns positive in Year 3, and scales to a healthy margin by Year 5 as fixed tech/G&A costs spread over a much larger revenue base.
- PaySetu needs its equity injections early (Years 1–2) to survive the J-curve, but needs no further equity beyond Year 3 once EBITDA turns positive and the warehouse facility can fund further receivables growth on its own — a genuinely useful output for a founder deciding how much to raise and when.
- Equity value is considerably more sensitive to the terminal-growth assumption than to the cost of equity within a plausible range — a reminder that the terminal-value assumption deserves the most scrutiny in any DCF.

## 5. Why This Project

This is the portfolio's core "hard finance skills" showpiece: a properly double-entry-linked 3-statement model is the single most-tested skill in investment banking and corporate finance interviews, and the FCFE-vs-unlevered-FCF judgment call shows the kind of business-model-aware thinking that separates a mechanically correct model from a genuinely useful one — directly relevant to Pakistan's fast-growing fintech lending sector (a natural funding target for exactly this kind of analysis).

## 6. Limitations & Future Work

- PaySetu and all its figures are entirely hypothetical, built for this exercise.
- Cost-of-capital inputs (risk-free rate, equity risk premium, cost of debt) are illustrative estimates consistent with Pakistan's historically high interest-rate environment, not live market data.
- Next step: add a monthly (rather than annual) cash-runway view for Years 1–2, since that is the period where timing — not just annual totals — determines whether the company survives to its next funding round.
