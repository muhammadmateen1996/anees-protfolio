# Finance & Fintech Portfolio — Pakistan

A 10-project portfolio of real-world finance and fintech problems, each built as a working spreadsheet model with a full written report. Built to demonstrate applied financial analysis, modelling, and product/policy thinking across Pakistan's financial sector — banking, fintech, capital markets, Islamic finance, and development finance.

Every project follows the same shape: **a real problem → a working model (Excel/Google Sheets, formulas included, no static screenshots) → a written report** covering the problem, the methodology, the key findings, and honest limitations. Several of the more complex models (Projects 8, 9, 10) were independently recalculated with a formula-evaluation engine during development to confirm they actually compute correctly, not just look right.

## How to use this portfolio

Each `projects/NN-xxx/` folder contains:
- `REPORT.md` — the write-up: problem statement, solution design, key findings, and limitations.
- One `.xlsx` workbook — opens natively in Excel or can be imported into Google Sheets (File → Import). Yellow cells are editable inputs; every other cell is a live formula.

## The 10 Projects

| # | Project | Domain | What it does |
|---|---------|--------|---------------|
| 1 | [Remittance Corridor Cost Optimizer](projects/01-remittance-cost-optimizer) | Fintech / Payments | Compares the true cost (fee + hidden FX margin) of sending money to Pakistan from the UK, UAE, and Saudi Arabia across banks, MTOs, fintech apps, and mobile wallets, and auto-recommends the cheapest channel. |
| 2 | [SME Alternative Credit Scoring Model](projects/02-sme-alt-credit-scoring) | Fintech Lending | An 8-factor points scorecard that assesses "thin-file" SMEs using alternative data (utility payments, mobile top-ups, trade references) instead of bank statements or collateral. |
| 3 | [Shariah-Compliant Portfolio Screener & Optimizer](projects/03-shariah-portfolio-screener) | Islamic Finance / Capital Markets | Screens 15 PSX-listed stocks against AAOIFI/KMI-30-style criteria, then builds a Markowitz-optimised portfolio from the compliant universe with a 2,000-portfolio efficient-frontier simulation. |
| 4 | [Robo-Advisory Risk Profiler & Asset Allocation Tool](projects/04-robo-advisor-risk-profiler) | WealthTech | A 10-question risk questionnaire that scores capacity and tolerance separately and maps straight to a model portfolio, the way a robo-advisor onboarding flow works. |
| 5 | [Household Budget & Inflation-Adjusted Savings Planner](projects/05-household-budget-inflation-planner) | Personal Finance | A budgeting tool plus a retirement/goal calculator (FV, PMT, real annuities) built explicitly for Pakistan's high-inflation environment. |
| 6 | [Digital Wallet & Financial Inclusion Analysis](projects/06-digital-wallet-financial-inclusion) | Financial Inclusion / Policy | A data-analysis dashboard testing whether Pakistan's mobile-wallet growth is actually closing the financial inclusion and gender gap, benchmarked against SBP's own NFIS targets. |
| 7 | [Microfinance Loan Default Prediction Model](projects/07-microfinance-default-prediction) | Credit Risk / Statistics | A logistic regression fitted in Python and embedded as live spreadsheet formulas, validated with a decile/gains table, KS statistic, and confusion matrix. |
| 8 | [Fintech Startup 3-Statement Model & DCF Valuation](projects/08-fintech-startup-valuation-model) | Corporate Finance / Valuation | A fully double-entry-linked 5-year model for a hypothetical BNPL startup, valued with a Free-Cash-Flow-to-Equity DCF — the correct method for a receivables-heavy lending business, and independently verified. |
| 9 | [Digital Transaction Fraud Detection Model](projects/09-transaction-fraud-detection) | Fraud Analytics | A 6-rule risk-scoring engine tuned to Pakistan's dominant social-engineering fraud pattern, validated on 300 labelled sample transactions. |
| 10 | [Cash Waqf / Islamic Social Finance Impact Model](projects/10-cash-waqf-social-finance-model) | Islamic Social Finance | A 10-year revolving Qard-e-Hasan (interest-free loan) fund model in the tradition of Akhuwat Foundation, quantifying both financial sustainability and the interest burden avoided versus informal moneylenders. |

## Why these 10, together

The portfolio is deliberately built to cover a Pakistani finance graduate's whole landscape rather than ten variations on one idea:

- **Consumer fintech** (1, 4, 9) — payments cost, investment access, and fraud from the everyday user's side.
- **Institutional/credit risk** (2, 7) — how a lender assesses risk with and without a data history, shown at two different levels of statistical sophistication.
- **Capital markets & corporate finance** (3, 8) — Islamic equity investing and startup valuation, the two core capital-markets skillsets.
- **Policy & systems view** (6) — stepping back to ask whether the sector's growth is actually delivering its stated development goal.
- **Personal finance** (5) and **Islamic social finance** (10) — the household and the philanthropic ends of the same financial system.

Every project uses real, named Pakistani institutions, regulators, and data sources for context (State Bank of Pakistan, PSX/KMI-30, Akhuwat Foundation, Global Findex, PBS CPI) even where the underlying figures are illustrative — each report says explicitly which is which.

## A note on data

None of these projects use real customer, account, or company financial data. Where a project references real institutions or published statistics (SBP, PBS, World Bank Global Findex, PSX-listed company names), the report says so explicitly and distinguishes cited public figures from the illustrative assumptions built for the model. This is a demonstration portfolio of analytical and modelling capability, not a claim to proprietary or confidential data.
