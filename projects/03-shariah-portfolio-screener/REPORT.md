# Project 3: Shariah-Compliant Portfolio Screener & Optimizer

**A transparent AAOIFI-style Islamic stock screen for the Pakistan Stock Exchange, combined with a mean-variance portfolio optimizer**

| | |
|---|---|
| **Domain** | Islamic Finance / Capital Markets / Portfolio Management |
| **Deliverable** | `Shariah_Portfolio_Screener_Optimizer.xlsx` |
| **Skills demonstrated** | Islamic finance screening methodology, Modern Portfolio Theory (Markowitz), Monte Carlo simulation, matrix/covariance math in spreadsheets, financial data visualisation |

---

## 1. The Real-World Problem

Pakistan is a 96%+ Muslim-majority country, and a large share of retail savers avoid the stock market entirely because they are unsure which listed companies are actually Shariah-compliant. The Pakistan Stock Exchange addresses part of this with the **KMI-30 Islamic index** (screened with Al Meezan Investment Management under AAOIFI-style rules), but there is no simple, self-serve tool that shows an individual investor **why** a stock passes or fails — and even the official indices stop at screening; they do not help an investor go the next step and **build a properly diversified portfolio** from the compliant list.

## 2. The Solution

A two-stage workbook that mirrors how an Islamic asset manager actually works:

### Stage 1 — Screening (`Shariah Screening`)
15 PSX-listed companies across sectors are tested against **five AAOIFI/KMI-30-style criteria**, each computed with a formula rather than typed in by hand:

1. **Core Business Activity** — not primarily conventional banking/insurance, alcohol, tobacco, gambling, or arms (binary Halal flag).
2. **Debt / Total Assets < 37%**
3. **Non-Compliant Investments / Assets < 33%**
4. **Non-Compliant Income / Revenue < 5%**
5. **Illiquid Assets / Total Assets > 25%** (so the share represents a real asset-backed business, not a proxy for trading cash/debt)

A stock must pass all five to be marked **COMPLIANT**. Conventional banks (MCB Bank, Bank Alfalah) correctly fail on debt and interest income; Pakistan Tobacco Company fails purely on the business-activity test despite conservative balance-sheet ratios — a deliberate illustration that the qualitative screen can override otherwise healthy financial ratios, exactly as AAOIFI intends.

### Stage 2 — Portfolio Construction (`Compliant Universe` → `Portfolio Optimizer` → `Dashboard`)
Six of the screened-compliant stocks are carried into a **mean-variance (Markowitz) optimizer**: an editable weight column (must sum to 100%), a full 6×6 correlation/covariance assumption table, and a **matrix-free portfolio-variance calculation** (a weighted covariance grid summed with plain `SUM`/`SUMPRODUCT`, so it works in any version of Excel or Google Sheets without array-entered formulas). Live outputs: portfolio expected return, risk (standard deviation) and Sharpe ratio.

The `Dashboard` sheet runs a **2,000-portfolio Monte Carlo simulation** to plot the efficient frontier, then compares three concrete scenarios — Equal Weight, Minimum Variance, and Maximum Sharpe — with their exact optimal weights.

## 3. Key Findings

- Conventional banks fail as expected on debt/interest-income tests; this is a useful sanity check that the screening logic mirrors real Islamic-index behaviour.
- Hub Power Company (a capital-intensive utility) sits close to the debt threshold — a well-known "edge case" sector in Islamic screening, which is why AAOIFI/Meezan re-run these ratios annually rather than once.
- Among the six optimizer stocks, **Systems Limited (IT services)** has both the highest expected return and the lowest correlation to the cement/fertilizer names — it is the main diversifier pulling the Maximum-Sharpe portfolio's risk down versus an equal-weighted mix.
- The **Minimum-Variance portfolio leans on Nestle Pakistan and Fauji Fertilizer**, the two lowest-volatility, moderately-correlated names — precisely what mean-variance theory predicts.

## 4. Why This Project

This combines two things a Pakistani Islamic retail investor currently has to do separately — verify Shariah compliance, then build a diversified portfolio — into one transparent, auditable spreadsheet. It demonstrates both **technical finance skill (Markowitz optimization, correlation/covariance mechanics)** and **domain-specific Islamic-finance literacy**, a combination directly relevant to Pakistan's large Islamic banking and asset-management sector — one of the fastest-growing segments of the country's financial system and a natural fit for a Chevening candidate interested in inclusive/ethical finance.

## 5. Limitations & Future Work

- Financial ratios and return/volatility assumptions are illustrative, sector-representative estimates for demonstration, not the companies' actual audited figures or live market data.
- A production tool would pull real ratios from annual reports/PSX financial statements and live prices from a market-data API, and would re-run the screen quarterly (as Meezan does for KMI-30).
- The optimizer is long-only and unconstrained beyond weights summing to 100%; a next iteration could add per-stock maximum-weight constraints and zakat/purification-of-income tracking on the small non-compliant income each stock earns.
