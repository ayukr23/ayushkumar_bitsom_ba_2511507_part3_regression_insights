# Residual Analysis Report

**Model used:** Full Multiple Regression (R² = 0.818)  
**Residual = Actual Monthly Sales − Predicted Monthly Sales**

---

## Top 5 Stores with Largest POSITIVE Residuals

(Actual sales significantly EXCEEDED model predictions — stores outperforming expectations)

| Store ID | Month | Region | Store Type | Actual Sales | Predicted Sales | Residual |
|---|---|---|---|---|---|---|
| STR-1028 | Apr 2025 | East | Mall | ₹713,611 | ₹600,329 | **+₹113,283** |
| STR-1030 | Feb 2025 | West | Residential | ₹820,519 | ₹726,530 | **+₹93,989** |
| STR-1073 | Mar 2025 | East | Residential | ₹813,317 | ₹721,906 | **+₹91,411** |
| STR-1026 | Apr 2025 | East | Mall | ₹625,514 | ₹534,473 | **+₹91,041** |
| STR-1051 | Feb 2025 | East | Airport | ₹787,716 | ₹698,277 | **+₹89,438** |

### Business Interpretation — Positive Residuals

These stores are **outperforming** what the model expects given their footfall, staff, marketing spend, etc. Possible reasons:

- **Superior store management or local execution** (strong store managers, excellent staff training, local community ties)
- **Favourable micro-location factors** not captured in the data (e.g., anchor tenant nearby, high-footfall corridor, recently opened competitor closure)
- **Product mix advantage** — these stores may stock higher-margin or higher-demand categories not reflected in aggregate variables
- **STR-1028 and STR-1026** (both East Mall, Apr 2025) suggest East Mall stores may have a seasonal or local event advantage in April

**Recommendation:** Investigate what these stores are doing differently. Their practices could be replicated across underperforming stores.

---

## Top 5 Stores with Largest NEGATIVE Residuals

(Actual sales significantly FELL SHORT of model predictions — stores underperforming expectations)

| Store ID | Month | Region | Store Type | Actual Sales | Predicted Sales | Residual |
|---|---|---|---|---|---|---|
| STR-1017 | Mar 2025 | West | High Street | ₹685,379 | ₹851,815 | **−₹166,436** |
| STR-1023 | Feb 2025 | South | Mall | ₹627,172 | ₹762,462 | **−₹135,290** |
| STR-1012 | Jan 2025 | West | Residential | ₹595,468 | ₹721,540 | **−₹126,072** |
| STR-1007 | Feb 2025 | West | Mall | ₹800,452 | ₹911,633 | **−₹111,181** |
| STR-1014 | Jan 2025 | West | High Street | ₹463,534 | ₹558,407 | **−₹94,873** |

### Business Interpretation — Negative Residuals

These stores are **underperforming** what the model predicts. Possible reasons:

- **West region concentration:** 3 of the 5 worst residuals are West stores. This may indicate a structural issue — local economic conditions, increased competition, or operational challenges specific to the West region
- **STR-1017 (West, High Street, Mar 2025):** Largest negative residual of −₹166,436. This could reflect a store-specific incident (supply chain failure, staff turnover, local disruption)
- **STR-1023 (South, Mall, Feb 2025):** South Mall stores generally perform above average in the model; this store's underperformance warrants investigation
- **STR-1012 (West, Residential, Jan 2025):** Also shows very high marketing spend (₹138,856 — anomalously high for a Residential store) yet low sales output, suggesting marketing efficiency issues

---

## Model Bias Assessment

**Is the model over-predicting or under-predicting certain store types?**

| Pattern | Observation |
|---|---|
| West stores | 3 of 5 most negative residuals are from West — model may slightly **over-predict** West store performance |
| Mall stores | Appear in both positive and negative residuals — model captures Mall premium well on average, but individual Mall stores vary widely |
| Airport stores | STR-1051 shows strong positive residual — Airport stores may have additional revenue drivers (e.g., transit surges) not in the model |
| Residential stores | Mix of large positive (STR-1030, STR-1073) and negative (STR-1012) residuals — high variability within type |

**Overall conclusion:** The model performs well on average (R²=0.818), but West High Street stores and certain Mall stores show systematic patterns of underperformance relative to predictions. A West-region specific investigation is warranted.