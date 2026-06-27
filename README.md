# Business Regression Analysis- Dataset Overview
  
**Dataset:** `business_regression_data.xlsx` | 320 rows × 14 columns | 80 stores × 4 months

---

## 1. Dependent Variable

| Variable | Type | Description |
|---|---|---|
| `monthly_sales` | Numerical (continuous) | Total monthly sales revenue per store — **target variable** |

---

## 2. Potential Independent Variables

| Variable | Type | Role |
|---|---|---|
| `marketing_spend` | Numerical | Monthly marketing investment per store |
| `footfall` | Numerical | Monthly customer visit count |
| `avg_discount_pct` | Numerical | Average discount offered (proportion) |
| `staff_count` | Numerical | Number of staff employed |
| `inventory_availability_pct` | Numerical | % of SKUs in stock |
| `competitor_distance_km` | Numerical | Distance to nearest competitor store |
| `holiday_flag` | Binary (0/1) | Whether month included a holiday |
| `customer_rating` | Numerical | Average customer satisfaction score |
| `region` | Categorical | Geographic region (East/North/South/West) |
| `store_type` | Categorical | Store format (Residential/High Street/Airport/Mall) |

---

## 3. Numerical Variables

`marketing_spend`, `footfall`, `avg_discount_pct`, `staff_count`, `inventory_availability_pct`, `competitor_distance_km`, `customer_rating`, `monthly_sales`, `monthly_profit`

---

## 4. Categorical Variables

| Variable | Categories | Action Required |
|---|---|---|
| `region` | East, North, South, West | Create 3 dummy variables (drop East as reference) |
| `store_type` | Residential, High Street, Airport, Mall | Create 3 dummy variables (drop Residential as reference) |
| `holiday_flag` | 0, 1 | Already binary — use directly |

---

## 5. Variables Needing Cleaning or Transformation

| Variable | Issue | Action Taken |
|---|---|---|
| `competitor_distance_km` | 6 missing values (1.9%) | Imputed with column median |
| `customer_rating` | 8 missing values (2.5%) | Imputed with column median |
| `month` | Stored as datetime | Kept for reference only |

---

## 6. Variables Not Useful for Regression

| Variable | Reason |
|---|---|
| `store_id` | Identifier — no predictive value |
| `month` | Only 4 time points; not a true continuous predictor |
| `monthly_profit` | Downstream outcome; would cause target leakage |

---

## Summary Observations

- 320 observations across 80 stores and 4 months (Jan–Apr 2025)
- Two variables have minor missingness, resolved via median imputation
- Footfall and staff_count show the strongest raw correlations with monthly_sales (r = 0.86 and 0.81)
- Categorical variables (region, store_type) require dummy encoding before regression