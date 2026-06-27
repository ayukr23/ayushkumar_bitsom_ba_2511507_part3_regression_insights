# Model Comparison Report

---

## Models Evaluated

| Model Name | Type | Dependent Variable | Key Predictors |
|---|---|---|---|
| Simple Model 1 | Simple Linear | monthly_sales | footfall |
| Simple Model 2 | Simple Linear | monthly_sales | marketing_spend |
| Multiple Regression | Multiple Linear | monthly_sales | footfall, staff_count, marketing_spend, inventory_availability_pct, customer_rating, holiday_flag, avg_discount_pct, region dummies, store_type dummies |

---

## Comparison Table

| Metric | Simple Model 1 (Footfall) | Simple Model 2 (Marketing) | Multiple Regression |
|---|---|---|---|
| **R-squared** | 0.736 | 0.167 | **0.838** |
| **Adj. R-squared** | — | — | **0.831** |
| **Intercept** | 446,411 | 560,777 | 27,220 |
| **Significant Variables** | footfall (p<0.001) | marketing_spend (p<0.001) | footfall, staff_count, marketing_spend, inventory_availability_pct, customer_rating, holiday_flag, region_South, region_West, type_HighStreet, type_Airport, type_Mall |
| **Insignificant Variables** | — | — | avg_discount_pct (p=0.15), region_North (p=0.44) |
| **F-statistic p-value** | <0.001 | <0.001 | <0.001 |

---


## Significant Variables (Multiple Regression, p < 0.05)

| Variable | Coefficient | p-value | Direction |
|---|---|---|---|
| footfall | +27.89 | <0.001 | Positive |
| marketing_spend | +1.17 | <0.001 | Positive |
| staff_count | +3,188 | 0.010 | Positive |
| inventory_availability_pct | +3,112 | <0.001 | Positive |
| customer_rating | +13,390 | 0.005 | Positive |
| holiday_flag | +14,740 | 0.024 | Positive |
| region_South | +19,520 | 0.006 | Positive |
| region_West | +19,260 | 0.002 | Positive |
| type_HighStreet | +19,410 | 0.001 | Positive |
| type_Airport | +42,020 | <0.001 | Positive |
| type_Mall | +30,240 | <0.001 | Positive |

---

## Business Usefulness

### Simple Model 1 — Footfall
**Useful for:** Quick store-level traffic monitoring. Strong standalone predictor.  
**Limitation:** Cannot distinguish *why* footfall differs across stores or how management actions affect it.

### Simple Model 2 — Marketing Spend
**Useful for:** Understanding marketing ROI in isolation (2.13x return).  
**Limitation:** Very weak standalone predictor (R²=0.167). Marketing likely drives sales *through* footfall, not independently.

### Multiple Regression (Recommended Model)
**Useful for:** Comprehensive decision-making — covers traffic, staffing, inventory, location type, and regional effects. Answers *which levers to pull* and by *how much*.  
**Best suited for:** Leadership strategy sessions, budget allocation, store prioritisation, and regional planning.

---

## Limitations of All Models

1. **Causation vs. Correlation:** Higher footfall may cause higher sales, but stores in better locations *naturally* attract more customers. We cannot prove causality from regression alone.

2. **Omitted Variables:** Factors like store size (sq ft), local population density, parking availability, and competitor pricing are not in the dataset. These likely explain some residual variance.

3. **Time Span:** Only 4 months of data (Jan–Apr 2025). Seasonal patterns beyond this window are not captured.

4. **Cross-Store Heterogeneity:** Each store has unique characteristics. Pooling all stores may mask store-level dynamics that a store-fixed-effects model would capture.

5. **avg_discount_pct is Insignificant:** Discounting strategy shows no statistically significant relationship with sales in this dataset — it may be confounded by product mix or store type.

6. **Region North vs East:** No statistically significant difference was found, suggesting North and East stores perform similarly once other factors are controlled.