# Project 4: Robo-Advisory Risk Profiler & Asset Allocation Tool

**A 10-question risk profiler that maps an investor's answers straight to a diversified model portfolio — the core logic behind every robo-advisor onboarding flow**

| | |
|---|---|
| **Domain** | WealthTech / Digital Investment Advisory / Behavioural Finance |
| **Deliverable** | `Robo_Advisor_Risk_Profiler.xlsx` |
| **Skills demonstrated** | Investor risk-profiling methodology, asset allocation design, spreadsheet-based decision engines, client-base simulation, dashboarding |

---

## 1. The Real-World Problem

Pakistan's retail investment industry is tiny relative to its population — mutual fund penetration is estimated at well under 1% of GDP (Mutual Funds Association of Pakistan / SECP data), compared to well over 100% in developed markets. A major reason: most first-time investors have no simple way to translate *"how much risk am I actually comfortable with, and how long am I investing for"* into an actual portfolio. They either avoid investing altogether or pick investments randomly on a relative's tip. Global robo-advisors (Betterment, Wealthfront) and Pakistan's own emerging digital wealth platforms solve exactly this problem with a short risk questionnaire that maps directly to a model portfolio — this project rebuilds that onboarding logic as a transparent, auditable spreadsheet.

## 2. The Solution

- **`Risk Questionnaire`** — 10 dropdown-driven questions split deliberately into two dimensions: **risk capacity** (age, investment horizon, income stability, emergency fund, dependents — objective facts about the investor's situation) and **risk tolerance** (reaction to a 20% loss, investing experience, growth-vs-safety priority, liquidity need — psychological willingness to take risk). A separate, unscored question captures a Shariah-compliance preference.
- **`Scoring & Allocation`** — the total score (max 39, from Q1–Q9 only) maps to one of **5 risk profiles**, each carrying a pre-built model portfolio across six asset classes relevant to a Pakistani investor (Cash/T-Bills, Government Sukuk/Bonds, Corporate Sukuk/TFCs, Equity, Gold, Real Estate/REIT). The sheet then computes the resulting portfolio's expected return and volatility from asset-class assumptions, and renders the recommended allocation as a live pie chart.
- **`Client Book`** — the identical scoring logic applied to 25 synthetic client profiles, showing how an advisory platform would use this at scale.
- **`Dashboard`** — the distribution of the client book across the five risk profiles.

## 3. Key Findings

- Separating **capacity** from **tolerance** matters in practice: a thrill-seeking retiree with no emergency fund and high loss-tolerance should still land in a conservative band overall, because low capacity constrains the outcome — this is why both dimensions feed one combined score rather than being scored (or worse, decided) independently.
- In the 25-client simulation, most clients cluster in the middle bands ("Balanced/Moderate" and "Growth-Oriented") — consistent with what real digital wealth platforms typically observe; true extremes are rare.
- The **Shariah-preference question is deliberately excluded from the risk score** — it should instead filter which fund universe (conventional vs. KMI-30/Islamic, see Project 3) is used to build the portfolio, since compliance is an ethical/religious constraint, not a risk signal. Conflating the two is a common design mistake in simpler robo-advisor questionnaires.

## 4. Why This Project

This project turns a genuine access problem — the absence of low-cost, judgment-free investment guidance for first-time Pakistani investors — into a working decision engine, and shows the same "identify a friction point, design the product logic, validate with data" thinking a fintech product or policy role would require. It pairs naturally with Project 3 (which supplies the actual Shariah-compliant asset universe this profiler could route a client into) and Project 1 (which shows the same target segment — everyday Pakistani households — from the payments side).

## 5. Limitations & Future Work

- The "your recommended allocation" volatility figure sums asset-class volatilities weighted by allocation, which ignores diversification benefits from cross-asset correlation (deliberately noted on-sheet); Project 3's covariance-grid approach shows how to do this properly.
- Model portfolio weights and asset-class assumptions are illustrative, not derived from an optimizer or backtested.
- Next step: connect the recommended allocation directly to a real fund/ETF universe (or to Project 3's compliant stock list) so a client's answers produce an actual investable order, not just target weights.
