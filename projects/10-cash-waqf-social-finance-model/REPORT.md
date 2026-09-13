# Project 10: Cash Waqf / Islamic Social Finance Impact Model

**A revolving Qard-e-Hasan (interest-free loan) fund model, in the tradition of Pakistan's Akhuwat Foundation**

| | |
|---|---|
| **Domain** | Islamic Social Finance / Development Finance / Philanthropy |
| **Deliverable** | `Cash_Waqf_Qard_Hasan_Impact_Model.xlsx` |
| **Skills demonstrated** | Revolving-fund financial modelling, social-impact quantification, Islamic finance structuring (Qard-e-Hasan, cash waqf), long-horizon sustainability analysis |

---

## 1. The Real-World Problem

Millions of low-income Pakistani households cannot get an affordable loan from either a conventional bank (no collateral, no credit history) or many microfinance institutions (interest rates on small loans are often very high once fees and mark-ups are included) — and routinely turn to informal moneylenders charging **5–10% per month**, an effective annual cost that can trap a household in debt rather than lifting it out of poverty. Pakistan's own **Akhuwat Foundation** pioneered a different model at national scale: **Qard-e-Hasan**, an interest-free loan funded by a revolving pool of donations (a form of cash waqf/philanthropic endowment), often disbursed through mosques and repaid on trust and community accountability rather than collateral — and Akhuwat has reported extraordinarily low default rates (commonly cited around 1–2%) as a result. This project builds a financial model of exactly this mechanism.

## 2. The Solution

- **`Assumptions`** sets the fund's starting corpus, annual donation inflows, average loan size, a small Shariah-permissible one-time **service fee** (cost-recovery, not interest/riba — a fixed processing charge unrelated to loan duration or profit, the same structure Akhuwat and Islamic scholars treat as permissible), the write-off rate, and operating cost per borrower.
- **`Revolving Fund Model`** rolls the fund forward for 10 years: each year it lends out its **full available corpus** (beginning balance + new donations) — a realistic assumption given Pakistan's very large unmet demand for small, affordable credit. Written-off loans are lost from the corpus; a service fee is collected to cover operating costs; the remaining principal recycles into next year's lending pool.
- **`Social Impact & Interest Saved`** translates fund activity into two impact metrics: estimated household income uplift from loan-funded activity, and the **interest burden avoided** by paying a ~5% one-time fee instead of a typical informal moneylender's rate — a distinctly Islamic-finance welfare metric that a conventional microfinance model (Project 7) does not capture.
- **`Dashboard`** visualises cumulative borrowers served, the fund's self-sustainability ratio, and cumulative interest avoided over the 10-year horizon.

## 3. Verification

I recalculated the full 10-year roll-forward independently (via the `formulas` Python engine) against a hand-built Python prototype of the same mechanics, and the two matched to the rupee at every year: Ending Corpus grows from PKR 63.7M (Year 1) to PKR 175.3M (Year 10), cumulative borrowers served reaches **20,579** by Year 10, and the Self-Sustainability Ratio holds steady at **103%** every year — confirming the fund's fee-and-recovery economics genuinely exceed its write-off losses, independent of scale.

## 4. Key Findings

- **The revolving structure is self-reinforcing**: the Self-Sustainability Ratio stays above 100% every year (service fees plus recovered principal exceed what was lent out, even after write-offs), meaning the fund grows on its own operating economics *before* counting new donations — donations accelerate growth and reach, but the fund is not dependent on them to survive. This is the central design insight behind why Akhuwat-style Qard-e-Hasan funds can scale nationally rather than staying a small, donor-dependent charity.
- **A low default rate is the model's load-bearing assumption**: with no interest income to absorb losses, sustainability depends far more heavily on keeping write-offs low than a conventional lender's model does — which is exactly why Akhuwat's mosque-based, social-collateral disbursement model is not an incidental cultural detail but the financial engine that makes interest-free lending viable at scale.
- **The interest-avoided metric is the model's most distinctive output**: borrowers pay a one-time ~5% service fee instead of what an informal moneylender would typically charge for the same loan — a large, quantifiable welfare transfer that conventional microfinance cost/benefit analysis doesn't measure, because it compares to formal-sector alternatives rather than to the informal-lender counterfactual most of these borrowers actually face.
- **The Social Value Multiplier** (cumulative welfare generated per PKR ever donated) grows from 0.85x in Year 1 to over 5x by Year 10 — illustrating why patient philanthropic capital deployed as a *revolving* fund, rather than a one-time cash grant, can be a far more capital-efficient development-finance tool over a long horizon.

## 5. Why This Project

Every other project in this portfolio works within conventional or Islamic-window *commercial* finance. This one models a third sector — Islamic social finance and waqf-based philanthropy — that is distinctively Pakistani in its scale and success (Akhuwat is one of the world's largest interest-free microfinance programmes) and directly relevant to development finance and financial inclusion. It closes the portfolio by showing the same financial-modelling toolkit used throughout applied to a mission-driven institution rather than a profit-maximising one — a natural, values-aligned note to end a Chevening-facing portfolio on.

## 6. Limitations & Future Work

- All figures are illustrative assumptions built to model the *mechanism* of a real class of institution (Akhuwat and similar Qard-e-Hasan funds), not a reproduction of any organisation's actual audited financials.
- The model assumes 100% of available corpus is deployed every year (realistic given documented excess demand) and a constant default rate; a more advanced version would let the default rate vary with the fund's growth rate (rapid scaling can strain the social-vetting process that keeps defaults low).
- Next step: model a multi-region rollout with region-specific default rates and donation inflows, to mirror how Akhuwat itself scaled from a single Lahore branch to a nationwide network.
