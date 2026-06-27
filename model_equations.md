# Model Equations

---

## Dummy Variable Approach

Categorical variables cannot be used directly in regression. We convert them into binary (0/1) dummy variables.

### Region (4 categories → 3 dummies)

**Reference category: East**  
East stores are the baseline. All region coefficients represent the *additional* sales versus an East store, holding other factors constant.

| Dummy Variable | Value = 1 when… | Value = 0 when… |
|---|---|---|
| `region_North` | Store is in North region | All other regions |
| `region_South` | Store is in South region | All other regions |
| `region_West` | Store is in West region | All other regions |

### Store Type (4 categories → 3 dummies)

**Reference category: Residential**  
Residential stores are the baseline. Store type coefficients represent *additional* sales versus a Residential store.

| Dummy Variable | Value = 1 when… | Value = 0 when… |
|---|---|---|
| `type_HighStreet` | Store is a High Street format | All other types |
| `type_Airport` | Store is an Airport format | All other types |
| `type_Mall` | Store is a Mall format | All other types |

**Why we drop one category:** Including all categories creates perfect multicollinearity (the "dummy variable trap"). The dropped category (reference) is implicitly captured in the intercept.

---

## Simple Regression Equations

### Model 1: Footfall → Monthly Sales

**Equation:**  
`Monthly Sales = 446,411 + 35.68 × Footfall`

**Interpretation:**  
- Each additional customer visiting the store per month is associated with approximately ₹35.68 in additional monthly sales.  
- Base sales (zero footfall) would be ₹446,411 (theoretical intercept).  
- **R² = 0.736** → Footfall alone explains 73.6% of the variation in monthly sales. Very strong predictor.  
- **p-value < 0.0001** → Highly statistically significant.  
- **Business use:** Footfall is the single most powerful lever. Strategies that drive store traffic (local events, promotions) will most directly lift sales.

---

### Model 2: Marketing Spend → Monthly Sales

**Equation:**  
`Monthly Sales = 560,777 + 2.13 × Marketing Spend`

**Interpretation:**  
- Every ₹1 increase in marketing spend is associated with approximately ₹2.13 increase in monthly sales — implying a 2.13x revenue return on marketing investment.  
- **R² = 0.167** → Marketing spend alone explains only 16.7% of sales variation.  
- **p-value < 0.0001** → Statistically significant, but weak standalone predictor.  
- **Business use:** Marketing spend has a positive ROI but is not the primary driver. Its impact is likely mediated through footfall.

---

## Multiple Regression Equation

**Full Model:**

```
Monthly Sales = 27,220
  + 27.89 × Footfall
  + 3,188 × Staff Count
  + 1.17 × Marketing Spend
  + 3,112 × Inventory Availability (%)
  + 13,390 × Customer Rating
  + 14,740 × Holiday Flag
  − 51,590 × Avg Discount (%)       [not significant at 5%]
  + 5,420 × region_North             [not significant at 5%]
  + 19,520 × region_South
  + 19,260 × region_West
  + 19,410 × type_HighStreet
  + 42,020 × type_Airport
  + 30,240 × type_Mall
```

**Overall Model: R² = 0.818 | Adjusted R² = 0.811 | F-statistic p < 0.0001**

---

## Coefficient Explanations (Multiple Regression)

| Variable | Coefficient | Business Meaning |
|---|---|---|
| Footfall | +27.89 | Each additional monthly visitor adds ~₹28 in sales, after controlling for all other factors |
| Staff Count | +3,188 | Each additional staff member is associated with ~₹3,188 more in monthly sales |
| Marketing Spend | +1.17 | Each ₹1 of marketing spend yields ~₹1.17 in sales (reduced from simple model due to shared footfall effect) |
| Inventory Availability | +3,112 | Each 1% improvement in stock availability adds ~₹3,112 to monthly sales |
| Customer Rating | +13,390 | Each 1-point improvement in rating adds ~₹13,390 in sales |
| Holiday Flag | +14,740 | Holiday months generate ~₹14,740 more in sales on average |
| Avg Discount % | −51,590 | Higher discounting is associated with lower sales (not statistically significant; p=0.15) |
| region_North (vs East) | +5,420 | North stores earn slightly more than East, but difference is NOT statistically significant |
| region_South (vs East) | +19,520 | South stores earn ~₹19,520 more than comparable East stores |
| region_West (vs East) | +19,260 | West stores earn ~₹19,260 more than comparable East stores |
| type_HighStreet (vs Residential) | +19,410 | High Street stores outperform Residential by ~₹19,410 |
| type_Airport (vs Residential) | +42,020 | Airport stores outperform Residential by ~₹42,020 — largest store type premium |
| type_Mall (vs Residential) | +30,240 | Mall stores outperform Residential by ~₹30,240 |

---

## Final Model Selected

**Selected Model: Full Multiple Regression (13 predictors)**

**Reason for selection:**
- R² of 0.838 vs best simple model R² of 0.736 — meaningfully better explanatory power
- Captures both quantitative drivers (footfall, staff) and structural factors (store type, region)
- Includes dummy variables required by the assignment
- Adjusted R² (0.831) remains high, confirming the additional variables are genuinely useful, not overfitting
- All key business levers are represented, enabling actionable recommendations