# Project 5: Household Budget & Inflation-Adjusted Savings Planner

**A budgeting and long-term savings tool built specifically for Pakistan's high and volatile inflation environment**

| | |
|---|---|
| **Domain** | Personal Finance / Macroeconomics / Retirement Planning |
| **Deliverable** | `Household_Budget_Inflation_Planner.xlsx` |
| **Skills demonstrated** | Personal budgeting, time-value-of-money modelling (FV, PMT, real annuity), macroeconomic data interpretation, dashboarding |

---

## 1. The Real-World Problem

Pakistan has experienced some of the highest and most volatile inflation of any major economy in the last five years: Pakistan Bureau of Statistics (PBS) CPI data shows average annual inflation rising from roughly 8–12% (FY2019–FY2022) to a peak of around **29% in FY2023** (individual months touched close to 38% year-on-year) before cooling sharply as the State Bank of Pakistan tightened monetary policy. For an ordinary household, this means a budget that worked last year can be badly wrong this year — and "saving for retirement" or a child's education without explicitly planning for inflation quietly erodes real purchasing power. A household saving in a low-yield account can easily be **losing money in real terms even while their account balance keeps growing** — a classic "money illusion" trap.

## 2. The Solution

- **`Monthly Budget`** — a standard household budget (income vs. 9 expense categories, budgeted vs. actual) with automatic variance flags and a spending-breakdown pie chart. Actual savings is correctly modelled as the *residual* cash flow (income minus actual spending), not an independent line item, so the sheet's totals never double-count.
- **`Inflation History (PBS)`** — an 11-year representative reference series of Pakistan's annual CPI inflation, charted, feeding the rest of the workbook as the default inflation assumption.
- **`Inflation Planner`** — projects today's total annual expenses forward 1/3/5/10/20 years at an adjustable inflation rate, and computes the single most useful number in the workbook: the **real (inflation-adjusted) return needed just to preserve purchasing power** — reframing "what return am I getting?" into "am I actually ahead of inflation?"
- **`Savings Goal Calculator`** — a retirement calculator using standard time-value-of-money mechanics (future value of expenses, a real-annuity corpus calculation, and Excel's `PMT` function) to derive the monthly savings required today to fund a fully inflation-adjusted retirement.
- **`Dashboard`** — visualises the nominal vs. real value of a sample PKR 1,000,000 savings pot over 10 years, making inflation's silent erosion effect visible at a glance.

## 3. Key Findings

- At a 6% nominal return with inflation near the 10-year historical average, a household's savings pot can visibly **lose real purchasing power even as its PKR balance keeps growing** — exactly the gap the Dashboard chart is built to expose.
- FY2023's ~29% average inflation exceeded almost every conventional bank deposit rate, meaning savers in ordinary accounts were guaranteed to lose real value that year no matter how "safely" they saved.
- A fixed monthly retirement-savings amount, set once and never revisited, is dangerous in Pakistan's inflation environment — the required contribution should be re-run at least annually as actual inflation and investment returns diverge from assumptions.

## 4. Why This Project

Every one of the other nine projects in this portfolio deals with fintech or capital markets from an institutional or product angle; this one deals with the same high-inflation environment from the household's own kitchen table — the practical, lived reality a Chevening panel would recognise as the actual backdrop to Pakistan's financial-inclusion and development challenges. It also demonstrates core financial-modelling mechanics (FV, PMT, real annuities) cleanly, without needing any specialised fintech context.

## 5. Limitations & Future Work

- Inflation figures are representative approximations of publicly reported PBS/SBP trends for illustration, not the exact official series (available at pbs.gov.pk).
- The retirement calculator uses a fixed nominal monthly contribution; a more sophisticated version would let contributions grow with assumed salary inflation each year.
- Next step: link the recommended monthly savings figure directly into Project 4's risk-profiler output, so a household's budget surplus flows straight into an actual model portfolio recommendation.
