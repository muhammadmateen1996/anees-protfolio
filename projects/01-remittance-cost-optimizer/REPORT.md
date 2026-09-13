# Project 1: Remittance Corridor Cost Optimizer

**A decision-support tool that finds the cheapest way to send money to Pakistan**

| | |
|---|---|
| **Domain** | Fintech / Financial Inclusion / International Payments |
| **Deliverable** | `Remittance_Cost_Optimizer.xlsx` (Excel & Google Sheets compatible) |
| **Skills demonstrated** | Financial modelling, spreadsheet engineering (VLOOKUP/INDEX/RANK.EQ), market research, data visualisation, consumer-finance & public-policy analysis |

---

## 1. The Real-World Problem

Pakistan is one of the world's top remittance-receiving countries. According to the **State Bank of Pakistan (SBP)**, workers' remittances reached roughly **USD 30 billion in FY2024**, equivalent to close to 8% of GDP — a lifeline for millions of households and a major source of foreign-exchange stability for the country.

Yet the **World Bank's Remittance Prices Worldwide (RPW)** database has repeatedly flagged South Asian corridors — and Pakistan's in particular — as more expensive than the G20's own 3% cost target set under the UN Sustainable Development Goal 10.c. Senders routinely pay:

- A **visible transfer fee**, which is what most comparison shopping stops at, and
- An **invisible FX margin** — the spread a provider adds on top of the mid-market exchange rate — which is usually the *larger* cost component but is almost never disclosed clearly.

Because the FX margin is hidden, most overseas Pakistani workers pick a channel out of habit (usually a bank or the first Western Union branch they find) rather than by comparing total cost. This has two consequences worth solving for:

1. **Individual harm** — a household can lose hundreds of dollars a year in avoidable fees and poor exchange rates.
2. **A national policy problem** — because informal *hundi/hawala* channels are cost-competitive (near-zero fee, close to mid-market FX), an estimated 30–40% of flows are believed to bypass the formal banking system entirely, which means they're unregulated, offer senders no consumer protection, and go undocumented for GDP, tax, and monetary-policy purposes.

## 2. The Solution

An interactive Excel/Google Sheets workbook that lets a sender pick a corridor (UK, UAE, or Saudi Arabia → Pakistan — the three largest by volume) and an amount, and instantly ranks **seven real channel types** — bank wire, two Money Transfer Operators, two fintech apps, a mobile-wallet transfer, and the informal hundi channel — by **true total cost (fee + FX margin)**, not just the advertised fee.

### How it works
- **`Corridor Data`** holds the underlying assumptions (21 rows: 7 channels × 3 corridors) built from publicly disclosed provider pricing pages and the World Bank RPW fee-plus-margin methodology.
- **`Calculator`** is the interactive front end: a dropdown (data validation) selects the corridor, a cell takes the amount, and `VLOOKUP` + `INDEX` pull the matching 7-channel block, compute `Total Cost = Fixed Fee + %Fee×Amount + FX Margin%×Amount`, and use `RANK.EQ`/`MATCH` to auto-recommend the cheapest formal channel and quantify potential annual savings from switching.
- **`Dashboard`** visualises (a) average total cost by channel type across all corridors and (b) how cost-as-a-percentage shrinks as the amount sent grows (economies of scale), driven by two native Excel charts.
- **`Insights`** distils the findings into consumer and policy recommendations.

## 3. Key Findings

- **Fintech apps (Wise) beat banks and MTOs on total cost** for any transfer above roughly GBP/AED/SAR 250–300, purely because their FX margin (0.3–0.5%) is a fraction of what banks and MTOs charge (1.5–3.2%) — even when the bank's advertised fee looks like "free."
- **Banks are the most expensive formal option** across all three corridors once the hidden FX margin is added back in, despite being the channel most senders default to.
- **Small transfers behave differently**: under ~GBP 100, fixed fees dominate, so a fee-free mobile-wallet transfer can beat a fintech app that has a flat fee to amortise.
- The **cost gap between formal and informal channels is the real driver of hundi/hawala usage** — closing it (specifically the FX margin, not just the fee) is the policy lever that matters.

## 4. Why This Project

This project takes a problem the friend has lived experience of (a finance graduate with family or community members who send/receive remittances) and turns it into a quantifiable, extensible model — exactly the kind of "identify a development-relevant problem, build an evidence-based tool" work that demonstrates the analytical and policy-relevant thinking Chevening looks for in a future leader from Pakistan's financial sector.

## 5. Limitations & Future Work

- Fee/FX-margin figures are representative assumptions for an academic project, not live quotes; production use would require a live FX-rate API (e.g. exchangerate.host) and a provider fee feed.
- The model currently compares like-for-like cash-to-bank/wallet delivery; it does not yet model cash-pickup-specific pricing tiers or promotional first-transfer discounts.
- Next step: turn the calculator into a lightweight public web app (already prototyped as a spreadsheet) so it can be shared directly with remittance-sending communities.
