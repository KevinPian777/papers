# Faccio, Morck & Yavuz (JFE, 2021) Paper Analysis

## Paper Information
- **Title:** Business Groups and the Incorporation of Firm-Specific Shocks into Stock Prices
- **Authors:** Mara Faccio (Purdue University), Randall Morck (University of Alberta & NBER), M. Deniz Yavuz (Purdue University)
- **Journal:** Journal of Financial Economics 139 (2021), pp. 852-871
- **JEL Classification:** G14, G15, G32, G34, M41

---

## 1) What is the Theoretical Background of This Paper?

This paper is grounded in the **Stock Market Informativeness** literature, utilizing Grossman (1976)'s concept that stock markets incorporate firm-specific information into prices, and Bond et al. (2012)'s theory that stock prices provide feedback to managers and capital providers. From the **Business Groups** literature, it draws on Khanna & Yafeh (2005, 2007)'s work on intra-group risk sharing and internal market functions, Hoshi et al. (1990, 1991)'s studies on Japanese corporate groups, and Gopalan et al. (2007)'s research on financial support in Indian business groups. The paper also synthesizes Johnson et al. (2000)'s tunneling concept, Bertrand et al. (2002)'s empirical tunneling research, Morck et al. (2000)'s stock price synchronicity in emerging markets, and Jin & Myers (2006)'s R² studies.

---

## 2) What Important Research Questions Does This Paper Answer?

This paper addresses the following key research questions:

### Main Research Questions
1. **Do business groups dampen the incorporation of firm-specific information into stock prices?**
   - Do investor expectations of intra-group risk sharing and resource transfers weaken the stock price impact of individual shocks?

2. **How do group-affiliated firms' stock prices respond to commodity price shocks?**
   - Are idiosyncratic returns of affiliated firms less sensitive to commodity shocks than unaffiliated firms?

3. **Does within-group risk sharing actually occur?**
   - Does a commodity shock to one affiliate affect the stock prices of other affiliates?

4. **Does business group prevalence explain cross-country differences in stock price synchronicity?**
   - Do stock prices move more synchronously in countries with more group-affiliated firms?

5. **What are the implications for capital allocation efficiency?**
   - How does reduced stock price informativeness affect economic growth?

---

## 3) How Were the Variables Measured and What is Their Theoretical Basis?

### Dependent Variable

| Variable | Measurement | Theoretical Basis |
|----------|-------------|-------------------|
| **Firm-specific stock return shocks (εᵢ,ₜ)** | Residuals from international CAPM regression using domestic market returns, US market returns, and exchange rate returns as explanatory variables (including 2-week leads/lags) | Jin & Myers (2006) methodology. Extracts firm-specific shocks unexplained by market factors |

### Key Independent Variables

| Variable | Measurement | Theoretical Basis |
|----------|-------------|-------------------|
| **Idiosyncratic commodity price shocks (εc,m,t)** | Residuals from regressing commodity returns on domestic and US market returns | Country-specific adjusted commodity shocks. Observable by all investors and unaffected by ex-post actions (tunneling, etc.) |
| **Group affiliation (Gᵢ,ₜ)** | Dummy variable: 1 if controlling shareholder is corporation, individual controls other firms, or firm controls other firms | La Porta et al. (1999) 20% ownership threshold. Excludes government-owned firms |

### Industry-Commodity Matching Methods

| Method | Description | Advantages/Disadvantages |
|--------|-------------|--------------------------|
| **Statistical Method** | Estimates industry-level commodity sensitivity using US small firm sample | Captures all channels (supply/demand), risk of spurious matches |
| **Constrained Statistical** | Statistical method + requires direct input-output relationship | Mitigates noise-driven matches, reduces sample by 74% |
| **BEA Method** | Direct matching based on Bureau of Economic Analysis input-output tables | No noise, misses indirect channels |

### Control Variables

| Variable | Measurement | Theoretical Basis |
|----------|-------------|-------------------|
| **Diversification** | Industry concentration Herfindahl index × (-1) | Diversified firms less sensitive to single commodity shocks |
| **Leverage** | Total debt / Total assets | More leveraged firms more sensitive to shocks |
| **Hedging activity** | Dummy for derivative/hedging financial disclosure | Hedging firms less sensitive to commodity shocks |
| **Firm size** | log(Market cap) or log(Total assets) | Larger firms hedge more actively (Nance et al., 1993) |
| **R&D activity** | R&D expenses / Total assets | R&D-intensive firms depend on future growth, less sensitive to current shocks |

---

## 4) Data Structure: Variables in a Single Row

### Data Overview
- **Sources:** Worldscope (1993-2009), Thomson Reuters Ownership (2005-2012), Datastream Asset-4 (2002-2013)
- **Period:** 1993-2013 (21 years)
- **Observations:** 390,186 firm-years, approximately 5,767,175 firm-week observations
- **Unit:** Firm-week panel data
- **Countries:** 43 economies (including US, excluding government-owned firms)

### Composition of a Single Row (Observation)

```
┌─────────────────────────────────────────────────────────────────────────────┐
│              One Row = One Firm's Observation in a Specific Week            │
├─────────────────────────────────────────────────────────────────────────────┤
│  Identification Variables                                                   │
│  ├─ Firm ID: Unique firm identifier                                        │
│  ├─ Week: Observation week (Wednesday-to-Wednesday)                        │
│  ├─ Country Code: One of 43 countries                                      │
│  ├─ Industry Code: Fama-French 30 industry classification                  │
│  └─ Matched Commodity: Commodity matched to industry (e.g., crude oil)     │
├─────────────────────────────────────────────────────────────────────────────┤
│  Dependent Variable                                                         │
│  └─ εᵢ,ₜ: Firm-specific stock return shock (international CAPM residual)   │
├─────────────────────────────────────────────────────────────────────────────┤
│  Key Independent Variables                                                  │
│  ├─ εc(j),m,t: Country-industry specific idiosyncratic commodity shock     │
│  │             (sign-adjusted)                                              │
│  └─ Gᵢ,ₜ: Group affiliation dummy (1=affiliated, 0=unaffiliated)           │
├─────────────────────────────────────────────────────────────────────────────┤
│  Interaction Variable                                                       │
│  └─ εc(j),m,t × Gᵢ,ₜ: Commodity shock × Group affiliation                  │
│                       (key variable of interest)                            │
├─────────────────────────────────────────────────────────────────────────────┤
│  Control Variables (annually measured, prior fiscal year-end)               │
│  ├─ Diversification: -1 × Industry sales Herfindahl index                  │
│  ├─ Leverage: Total debt / Total assets                                    │
│  ├─ Hedging activity: Derivative disclosure dummy                          │
│  ├─ log(Market cap): Firm size                                             │
│  ├─ log(Total assets): Alternative size measure                            │
│  └─ R&D activity: R&D expenses / Total assets                              │
├─────────────────────────────────────────────────────────────────────────────┤
│  Fixed Effects                                                              │
│  └─ Industry × Country fixed effects: Different values each week in        │
│     Fama-MacBeth regressions                                               │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Sample Composition

| Category | Observations | Characteristics |
|----------|--------------|-----------------|
| Total firm-years | 390,186 | 55,671 unique firms |
| Group-affiliated | 108,086 (28%) | Corporate control, individual multi-control, subsidiary holding |
| Unaffiliated | 282,100 (72%) | Including investment fund-controlled |

### Group Affiliation by Selected Countries

| Country | Group Affiliation Rate | Country | Group Affiliation Rate |
|---------|------------------------|---------|------------------------|
| Chile | 70% | United States | 11% |
| Italy | 56% | United Kingdom | 15% |
| Hong Kong | 55% | Canada | 16% |
| Japan | 31% | Taiwan | 8% |

---

## 5) What Position Does This Paper Occupy in the Overall Research Program?

### Academic Position

```
┌─────────────────────────────────────────────────────────────────────────────┐
│               Stock Price Informativeness & Business Group Research         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  [Stock Price Informativeness Literature]                                   │
│  • Grossman (1976): Information incorporation function of stock prices     │
│  • Tobin (1984): Stock prices and capital allocation efficiency            │
│  • Bond et al. (2012): Real effects of financial markets                   │
│                    ↓                                                        │
│  [Stock Price Synchronicity Literature]                                     │
│  • Morck et al. (2000): Stock price synchronicity in emerging markets      │
│  • Jin & Myers (2006): R² around the world                                 │
│  • Wurgler (2000): Capital allocation efficiency                           │
│                    ↓                                                        │
│  [Business Group Literature]                                                │
│  • Khanna & Yafeh (2007): Internal markets of business groups              │
│  • Gopalan et al. (2007): Financial support in Indian groups               │
│  • Bertrand et al. (2002): Tunneling in Indian business groups             │
│                    ↓                                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │  ★ Faccio, Morck & Yavuz (2021) ★                                  │    │
│  │  • Business groups dampen firm-specific information incorporation  │    │
│  │  • Causal inference using global commodity shocks                  │    │
│  │  • Partially explains cross-country synchronicity differences      │    │
│  │  • Links to middle-income trap and capital allocation efficiency   │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                    ↓                                                        │
│  [Policy Implications]                                                      │
│  • Business groups create feedback effect weakening stock informativeness  │
│  • New explanation for middle-income trap                                  │
│  • Links capital allocation efficiency to economic growth                  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Key Contributions of This Paper

1. **Methodological Innovation**
   - Identification strategy using global commodity price shocks
   - Comparison of affiliated/unaffiliated firm responses to identical shocks
   - Difference-in-difference (DID) analysis using successful/failed acquisition attempts

2. **Empirical Findings**
   - Group-affiliated firms' stock prices are **approximately 40% less sensitive** to commodity shocks
   - Sensitivity increases when affiliated firms become unaffiliated, decreases in reverse
   - Commodity shocks to other affiliates affect own stock price (evidence of risk sharing)

3. **Economic Implications**
   - Business groups can be both **cause and consequence** of reduced stock price informativeness
   - Higher stock price synchronicity in countries with greater group prevalence
   - Reduced capital allocation efficiency → possible middle-income trap

4. **Causal Identification**
   - Mitigates selection bias by comparing exogenously failed vs. successful acquisition attempts
   - Controls endogeneity through before/after comparison of group affiliation status changes

### Paper's Limitations

- Group identification relies on 20% ownership threshold, potentially misclassifying some affiliates as unaffiliated
- Analysis limited to commodity-sensitive industries
- Unobservable firm characteristics may affect results

---

## Summary of Key Findings

### Main Regression Results

| Regression | Method | Affiliated × Commodity Shock Coefficient | Interpretation |
|------------|--------|------------------------------------------|----------------|
| Baseline | Statistical matching | -2.46*** | Affiliated firms 40% less sensitive than unaffiliated |
| With fixed effects | Statistical matching | -1.84** | Significant after controlling for industry-country FE |
| BEA matching | Input-output tables | -1.90** | Consistent results with alternative matching method |

### Difference-in-Difference Results

| Treatment Type | Treated Firm Change | Control Firm Change | DID Estimate |
|----------------|---------------------|---------------------|--------------|
| Unaffiliated → Affiliated | -3.96*** | -0.19 | -3.76** |
| Affiliated → Unaffiliated | +2.88* | -0.45 | +3.33* |
| Exogenously failed bid comparison | -4.38** | +2.28** | -6.65*** |

### Country-Level R² Analysis

- Stock price synchronicity (R²) is significantly higher in countries with greater group affiliation prevalence (p=0.09)
- Group-affiliated firms exhibit significantly higher R² than unaffiliated firms
