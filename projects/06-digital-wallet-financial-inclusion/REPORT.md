# Project 6: Digital Wallet & Financial Inclusion Analysis Dashboard

**A data-analysis dashboard asking whether Pakistan's mobile-wallet boom is actually closing the financial inclusion gap**

| | |
|---|---|
| **Domain** | Financial Inclusion / Fintech Policy / Data Analytics |
| **Deliverable** | `Digital_Wallet_Financial_Inclusion_Analysis.xlsx` |
| **Skills demonstrated** | Time-series analysis (CAGR, YoY growth), development-finance data interpretation, gender-gap analysis, dashboard design |

---

## 1. The Real-World Problem

Pakistan's branchless banking / mobile wallet sector (JazzCash, Easypaisa, SadaPay, NayaPay, and bank-led m-wallets) has been the State Bank of Pakistan's flagship financial-inclusion tool since the sector launched around 2009. SBP's quarterly Branchless Banking Statistics track headline growth in registered accounts, agents, and transaction value — numbers that get cited constantly as evidence of financial inclusion progress. Separately, the **World Bank's Global Findex survey** (2014, 2017, 2021 waves) tracks the share of adults with *any* financial account, and Pakistan's **gender gap in account ownership is among the widest in the world**. These two data threads are rarely put side by side. This project does exactly that, to ask a sharper question than "are accounts growing?": **is mobile-wallet growth actually translating into broader, more equal financial inclusion, or mostly adding more accounts to people who already had one?**

## 2. The Solution

- **`Branchless Banking Data`** — a 2016–2024 annual series of registered vs. active m-wallet accounts, agent network size, and transaction value, with YoY growth and CAGR computed by formula.
- **`Findex – Account Ownership`** — the three Global Findex waves for Pakistan, split by gender and urban/rural, with the gender gap computed explicitly rather than left implicit.
- **`NFIS Target Tracking`** — actual account-ownership progress benchmarked against SBP's own published National Financial Inclusion Strategy targets.
- **`Dashboard`** — four charts: registered-vs-active accounts, transaction value growth, the Findex gender-gap trend, and NFIS target-vs-actual.

## 3. Key Findings

- **The "activation gap" is the real story**: registered accounts grew roughly 4x from 2016–2024, but active accounts consistently sit at only 40–50% of registered accounts — the honest inclusion metric (active usage) has grown more slowly than the headline number most reporting relies on.
- **Transaction value grew ~16x over the same period** — much faster than account growth — implying existing users are transacting far more per account (deepening usage) rather than growth coming mainly from new users (widening usage). Both matter, but call for different interventions.
- **The gender gap has not closed — it has widened in absolute terms**: from 12 percentage points (2014) to 22 points (2021), even as overall ownership rose, consistent with well-documented barriers specific to women's financial inclusion in Pakistan (lower smartphone ownership, agent networks concentrated in male-dominated public spaces, uneven digital-literacy access).
- **Pakistan has consistently undershot its own NFIS targets** at every checkpoint in this analysis.

## 4. Why This Project

This is the portfolio's explicit "step back and look at the system" project — where Projects 1, 2, and 4 build individual fintech tools, this one interrogates whether the sector those tools sit inside is actually delivering on its stated development goal. That systems-level, policy-aware framing — using real (if approximated) national data to test a popular narrative rather than just accepting it — is exactly the kind of critical, evidence-based thinking Chevening looks for in a future leader engaging with Pakistan's financial-inclusion agenda.

## 5. Limitations & Future Work

- Figures are representative approximations of publicly reported orders of magnitude from SBP Branchless Banking newsletters and World Bank Global Findex releases, reconstructed for this analysis — not an exact reproduction of the official datasets (available at sbp.org.pk and worldbank.org/globalfindex).
- A next iteration would pull the actual published SBP quarterly PDFs and Findex microdata directly, and add province-level and age-cohort breakdowns where available.
- The activation-gap and gender-gap findings each deserve a dedicated root-cause study (e.g. survey data on *why* registered wallets stay dormant) beyond what aggregate statistics alone can show.
