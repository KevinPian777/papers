# Bertrand, Mehta & Mullainathan (QJE, 2002) Paper Analysis

## Paper Information
- **Title:** Ferreting Out Tunneling: An Application to Indian Business Groups
- **Authors:** Marianne Bertrand, Paras Mehta, Sendhil Mullainathan
- **Journal:** The Quarterly Journal of Economics (February 2002)
- **Pages:** 121-148

---

## 1) What is the Theoretical Background of This Paper?

This paper is grounded in the **Corporate Governance** and **Agency Theory** literature. It follows the "Law and Finance" research tradition established by La Porta, Lopez-de-Silanes, Shleifer, and Vishny (1999), starting from the theoretical framework that weak legal protection and lax enforcement mechanisms enable minority shareholder expropriation. In business groups, controlling shareholders control multiple publicly traded firms while having significant cash flow rights in only some of them, and this divergence between control rights and cash flow rights creates tunneling incentives as theorized by Bebchuk, Kraakman, and Triantis (2000) and Wolfenzon (1999). The paper develops a new methodology to empirically test the "tunneling" concept proposed by Johnson et al. (2000)—the practice of controlling shareholders transferring resources from firms where they have low cash flow rights to firms where they have high cash flow rights.

---

## 2) What Important Research Questions Does This Paper Answer?

This paper addresses the following key research questions:

### Main Research Questions
1. **Does tunneling actually occur in business groups?**
   - Previous research relied mainly on anecdotal evidence or cross-sectional correlations; this paper provides causal evidence of tunneling

2. **What is the magnitude of tunneling?**
   - More than **25%** of marginal profits in low-cash-flow-right firms are dissipated

3. **Through what mechanisms does tunneling occur?**
   - Primarily through manipulation of **nonoperating profits** rather than transfer pricing

4. **Where does the money flow?**
   - Approximately 61% of tunneled funds reappear in other firms within the group (especially high-cash-flow-right firms)

5. **Does the market recognize tunneling?**
   - The stock market partially recognizes and incorporates tunneling into firm valuations

---

## 3) How Were the Variables Measured and What is Their Theoretical Basis?

### Dependent Variables

| Variable | Measurement | Theoretical Basis |
|----------|-------------|-------------------|
| **Profit before DIT** | Profit before depreciation, interest, and taxes (perfₖₜᵢ) | Captures the impact of tunneling on final profits. Uses unconsolidated financial statements to exclude mechanical accounting effects |
| **Operating Profits** | Sales - Raw materials - Energy costs - Wages | Detects tunneling through transfer pricing manipulation |
| **Nonoperating Profits** | Total profit - Operating profits (residual items) | Detects tunneling through non-operational means (bad debt write-offs, interest income, extraordinary items, etc.) |

### Independent Variables

| Variable | Measurement | Theoretical Basis |
|----------|-------------|-------------------|
| **Own Shock (predₖₜ)** | Aₖₜᵢ × r̂ᵢₜ (Assets × Industry average return). Excludes the firm itself from industry average | Exogenous profit shock predicting what the firm should have earned absent tunneling. Industry shocks provide variation beyond individual firm control |
| **Group Shock (opredₖₜ)** | Σⱼ≠ₖ predⱼₜ (Sum of predicted profits of other firms in the same group) | Evidence of within-group fund transfers. If tunneling exists, firms should respond to shocks to other group firms |

### Moderating Variables

| Variable | Measurement | Theoretical Basis |
|----------|-------------|-------------------|
| **Director Equity** | Percentage of shares held by directors (%) | In India, controlling families exercise control by placing family members or associates on boards. Proxy for direct cash flow rights |
| **Other Ownership** | Minority shareholder stake (excluding directors, banks, foreigners, institutions, government, corporates, top 50 shareholders) | Size of expropriable minority shareholders. Higher levels increase tunneling incentives |
| **Cash Flow Rights Spread** | Max-Min ownership difference within group | Measures tunneling potential within the group |

### Control Variables

| Variable | Measurement | Purpose |
|----------|-------------|---------|
| **Ln Assets** | log(Total assets) | Control for firm size |
| **Year of Incorporation** | Founding year | Control for firm age |
| **Firm Fixed Effects** | Firm fixed effects | Control for unobserved firm characteristics |
| **Year Fixed Effects** | Year fixed effects | Control for common shocks over time |

### Theoretical Rationale for Measurement
- **Why industry shocks:** Provides exogenous variation beyond individual firm control, mitigating endogeneity concerns
- **Why group shocks:** Distinguishes tunneling from mere inefficient operation. If tunneling occurs, diverted funds should appear in other group firms
- **Using cash flow rights differences:** Enables prediction of tunneling direction—funds flow from low-cash-flow-right to high-cash-flow-right firms

---

## 4) Data Structure: Variables in a Single Row

### Data Overview
- **Source:** Prowess (Centre for Monitoring Indian Economy, CMIE)
- **Period:** 1989-1999
- **Observations:** Approximately 18,500 firm-year observations
- **Unit:** Firm-Year panel data

### Composition of a Single Row (Observation)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│              One Row = One Firm's Observation in a Specific Year             │
├─────────────────────────────────────────────────────────────────────────────┤
│  Identification Variables                                                    │
│  ├─ Firm ID: Unique firm identifier                                         │
│  ├─ Year: Observation year (1989-1999)                                      │
│  ├─ Group ID: Group identifier (blank if Stand-alone)                       │
│  └─ Industry Code: One of 134 industry classifications                      │
├─────────────────────────────────────────────────────────────────────────────┤
│  Financial Variables (in 1995 Rs. crore, 1 crore = 10 million rupees)       │
│  ├─ Total Assets: (Mean 131.80, Group 252.76, Stand-alone 49.69)           │
│  ├─ Total Sales: (Mean 94.39)                                               │
│  ├─ Profit before DIT: (Mean 16.84)                                         │
│  ├─ Operating Profits                                                       │
│  ├─ Nonoperating Profits                                                    │
│  └─ Market Valuation: (for q ratio calculation)                             │
├─────────────────────────────────────────────────────────────────────────────┤
│  Ownership Structure Variables (%, available for ~60% publicly traded)      │
│  ├─ Director Equity: (Mean: Group 7.45%, Stand-alone 22.99%)               │
│  ├─ Other Ownership: (Mean: Group 27.57%, Stand-alone 31.48%)              │
│  ├─ Foreign Ownership                                                       │
│  ├─ Institutional Ownership                                                 │
│  └─ Government Ownership                                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│  Constructed Variables                                                       │
│  ├─ Group Dummy: Group affiliation (1=Group, 0=Stand-alone)                │
│  ├─ Own Shock (predₖₜ): Predicted profit = Assets × Industry avg return    │
│  ├─ Group Shock (opredₖₜ): Sum of other group firms' predicted profits     │
│  ├─ Director Equity Spread: Max-Min director equity within group           │
│  ├─ Other Ownership Spread: Max-Min other ownership within group           │
│  ├─ Firm Q: Firm-level market premium (extracted from fixed effects)       │
│  └─ Group Q: Group-level market premium                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│  Firm Characteristics                                                        │
│  ├─ Year of Incorporation: (Mean: Group 1967, Stand-alone 1979)            │
│  └─ Ln Assets: log(Total assets)                                            │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Sample Breakdown
| Category | Observations | Characteristics |
|----------|-------------|-----------------|
| Total | ~18,500 | - |
| Group Firms | ~7,500 | Affiliated with groups averaging 15 firms |
| Stand-alone Firms | ~11,000 | Not affiliated with any group |

---

## 5) What Position Does This Paper Occupy in the Overall Research Program?

### Academic Position

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    Corporate Governance Research Program                     │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  [Theoretical Foundations]                                                   │
│  • Berle & Means (1934): Separation of ownership and control                │
│  • Jensen & Meckling (1976): Agency costs                                   │
│                    ↓                                                        │
│  [Law and Finance]                                                          │
│  • La Porta et al. (1997, 1998, 1999): Legal protection and financial dev. │
│  • Ownership concentration in countries with weak investor protection       │
│                    ↓                                                        │
│  [Tunneling Theory]                                                         │
│  • Johnson et al. (2000): "Tunneling" concept formalized                   │
│  • Bebchuk et al. (2000): Agency cost model of pyramid structures          │
│  • Wolfenzon (1999): Theory of pyramidal ownership                         │
│                    ↓                                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │  ★ Bertrand, Mehta & Mullainathan (2002) ★                         │    │
│  │  • First systematic empirical study of tunneling                    │    │
│  │  • Develops identification strategy using industry shocks           │    │
│  │  • Measures magnitude and mechanisms of tunneling                   │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                    ↓                                                        │
│  [Subsequent Research]                                                       │
│  • Claessens et al. (2002): East Asian business groups                     │
│  • Bae et al. (2002): Korean chaebol M&A and tunneling                     │
│  • Cheung et al. (2006): Hong Kong related-party transactions              │
│  • Atanasov et al. (2010): Bulgarian privatization and tunneling           │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Key Contributions of This Paper

1. **Methodological Innovation**
   - Develops a **general methodology** for measuring tunneling
   - Uses industry shocks as exogenous variation to address endogeneity
   - Methodology applicable to other countries/contexts

2. **Empirical Contributions**
   - First **causal evidence** that tunneling actually occurs
   - Identifies the **magnitude** (over 25% of marginal profits) and **mechanism** (nonoperating profit manipulation)
   - Systematic analysis beyond anecdotal evidence

3. **Policy Implications**
   - Demonstrates importance of regulating related-party transactions
   - Highlights need for legal/institutional reforms to protect minority shareholders
   - Links to India's Kumar Mangalam Committee corporate governance recommendations

4. **Impact on Subsequent Research**
   - Became a **standard reference** for emerging market corporate governance research
   - Foundation for business group, pyramid structure, and family firm research
   - Starting point for tunneling/propping research

### Summary of Position in Research Program

This paper serves as the **empirical validation of tunneling** within the "Law and Finance" research tradition. By systematically measuring and documenting the theoretically predicted expropriation of minority shareholders by controlling shareholders for the first time, it provides an empirical foundation for academic discourse and policy reform regarding corporate governance and investor protection.

---

## Summary of Key Findings

| Prediction | Finding | Implication |
|------------|---------|-------------|
| Group firms less sensitive to own shock | ✓ 30% less sensitive | Profits are being diverted |
| Low-cash-flow-right firms even less sensitive | ✓ Confirmed | Lower ownership leads to more diversion |
| Group firms respond to other firms' shocks | ✓ Confirmed | Funds move within group |
| More sensitive to low-cash-flow-right firms' shocks | ✓ Confirmed | Flow from low to high ownership firms |
| High-cash-flow-right firms less responsive | ✓ Confirmed | These firms are fund recipients |
