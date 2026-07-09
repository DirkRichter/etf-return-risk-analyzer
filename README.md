# etf-return-risk-analyzer
An interactive financial tool that visualizes and compares ETFs using data-driven Return and Risk Scores. Built with HTML5 and Chart.js, it translates complex fundamental metrics, valuation multiples (PEG/PBG), and historical volatility into intuitive scatter matrices and dynamic radar profiles.

# ETF Analysis: Return vs. Risk

A dynamic, browser-based vibe-coding project designed to analyze and compare Exchange Traded Funds (ETFs) by visualizing their fundamental growth metrics, valuation ratios, and risk profiles using interactive **Chart.js** scatter and radar plots.

---

## 📊 Overview

This project fetches real-time and historical financial metrics directly from the ExtraETF API to build custom, multi-dimensional profiles for a defined list of ETFs. Rather than looking at performance or risk in isolation, it aggregates complex structural data into two core indicators: the **Return Score** and the **Risk Score**.

---

## 🧮 Score Definitions & Financial Logic

To plot ETFs in a meaningful 2D space, the application standardizes diverse financial metrics (ranging from percentages to pure valuation multiples) onto a global scale between `0.0` and `1.0` using min-max normalization.

### 1. Return Score (Y-Axis)
The **Return Score** represents the structural growth potential and recent performance momentum of the fund. It is an unweighted average of normalized values from the following vectors:
* **Fundamental Growth Forecasts:** Expected earnings growth (`portfolio_fc_exp_gewinnwachstum`), book value growth (`portfolio_fc_buchwertwachstum`), cash flow growth (`portfolio_fc_cashflowwachstum`), and revenue growth (`portfolio_fc_umsatzwachstum`).
* **Realized Performance:** Realized returns over 1 month, 6 months, and 1 year.
* **Risk-Adjusted Return:** The 1-year Sharpe Ratio, ensuring that returns generated with lower relative volatility push the score higher.

> **Interpretation:** A higher Return Score indicates an ETF whose underlying companies possess strong fundamental growth catalysts and strong technical price momentum.

### 2. Risk Score (X-Axis)
The **Risk Score** measures both the valuation risk (overpricing) and the structural volatility of the portfolio. 
* **Valuation Multiples:** Traditional value metrics including Price-to-Earnings (P/E / `kgv`), Price-to-Book (P/B / `kbv`), and Price-to-Cash-Flow (`kurs_cashflow`). 
* **Volatility:** Capital concentration (item weight) and the historical 1-year volatility.

> **Interpretation:** A higher Risk Score indicates a cluster of expensive underlying assets (high multiples) or elevated historical price fluctuations. In a classic risk-return framework, efficient portfolios should ideally sit in the **Top-Left quadrant** (High Return Score, Low Risk Score).

---

## 📈 Charts Explained

The application renders three specialized views to prevent data distortion:
1.  **Risk vs. Return:** The primary matrix mapping the overall Risk Score against the Return Score.
2.  **PEG & PBG Metrics:** A growth-adjusted valuation chart plotting the PEG ratio ($P/E \div \text{Earnings Growth}$) against the PBG ratio ($P/B \div \text{Book Value Growth}$) to identify undervalued growth assets.
3.  **P/B vs. Expected Growth:** A pure fundamental cross-sectional chart.
4.  **Spider (Radar) Charts:** Individual footprints of each ETF, showing exactly which metric (e.g., Sharpe ratio vs. volatility) drives its global score.

---

## 🚀 Getting Started

### Prerequisites
The project runs entirely in the client's browser. It uses **Chart.js**.

### Installation & Usage
1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/etf-analysis-return-risk.git](https://github.com/your-username/etf-analysis-return-risk.git)
