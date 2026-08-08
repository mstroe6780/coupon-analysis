# Will the Customer Accept the Coupon?

### Exploratory Data Analysis Report  
**AI / Machine Learning Certificate — Required Assignment 5.1**

---

## Objective

Identify the **customer characteristics and driving contexts associated with coupon acceptance**, with particular attention to:

- **Bar coupons**
- An independent investigation of **Coffee House coupons**

> **Note:** This project is exploratory. The results describe associations observed in the survey data and should not be interpreted as causal effects.

---

## Key Results

| Metric | Result |
|---|---:|
| Total observations | **12,684** |
| Overall coupon acceptance | **56.8%** |
| Bar coupon acceptance | **41.0%** |
| Coffee House coupon acceptance | **49.9%** |
| Frequent Coffee House visitors | **66.0%** acceptance |
| Highest Coffee House segment | **81.3%** acceptance |

### Main Takeaway

**Prior visitation behavior was the strongest and most consistent indicator of coupon acceptance.** Drivers who already visited bars or Coffee Houses regularly were substantially more likely to accept coupons for those establishments.

For Coffee House coupons, **driving context also mattered**. Frequent Coffee House visitors with **no urgent destination at 10 AM** had an **81.3% acceptance rate**, compared with **46.3%** for all other Coffee House coupon recipients.

---

# 1. Data Quality and Preparation

The original dataset contains **26 variables** describing:

- Driver characteristics
- Driving context
- Prior visitation behavior
- Coupon characteristics
- Coupon acceptance

Column names were standardized to improve readability and consistency throughout the analysis.

## 1.1 Missing Values

Six variables contain missing values.

- The `car` variable is **more than 99% missing**. Because it provides very little usable information, it was removed.
- The following five variables each contain **less than 2% missing data**:
  - `Bar`
  - `CoffeeHouse`
  - `CarryAway`
  - `RestaurantLessThan20`
  - `Restaurant20To50`
- Missing values in these five variables were assigned to an `"unk"` category so they could be retained or excluded depending on the analysis.
- A separate dataset excluding selected `"unk"` observations was created for analyses where unknown visitation frequency could affect the comparison.

## 1.2 Duplicate Rows

The dataset contains **74 duplicated rows**.

Approximately **66% of the duplicated rows involve Carry Out & Take Away coupons**.

Because the dataset does not contain a unique respondent identifier, it is not possible to determine whether these observations represent:

- Repeated survey submissions from the same respondent, or
- Different respondents who provided identical answers

Because identical survey responses are plausible, the duplicated rows were **retained for the initial EDA rather than removed without evidence**.

## 1.3 Data Types and Redundant Variables

Most variables were initially stored as the `object` data type. Their unique values and distributions were reviewed before converting them to more appropriate categorical or numeric formats.

The `income` variable was treated as an **ordered categorical variable** so that income groups appear in their natural ascending order in tables and visualizations.

Additional data-quality findings:

- `toCoupon_GEQ5min` contains only the value `1`, so it has no variation and was removed.
- `direction_same` and `direction_opp` are complementary variables. `direction_opp` was removed to avoid redundant information.
- A working copy of the original dataset was created before cleaning so the source data remained unchanged.

---

# 2. Overall Coupon Acceptance

Approximately **56.8%** of all observations accepted the coupon:

- **Accepted:** 7,210
- **Total observations:** 12,684

This overall acceptance rate provides a useful benchmark for comparing coupon types and customer segments.

---

# 3. Bar Coupon Analysis

Bar coupons were accepted in **41.0%** of cases, making them one of the lower-acceptance coupon categories.

The strongest pattern was that **drivers who already visited bars more frequently were much more likely to accept a bar coupon**.

## 3.1 Bar Coupon Comparisons

| Comparison | Target Group | All Others / Comparison |
|---|---:|---:|
| Bar visits > 3/month | **76.9%** | 37.1% for ≤ 3/month |
| Bar visits > 1/month and age > 25 | **69.5%** | 33.4% |
| Bar visits > 1/month, no child passenger, occupation not Farming/Fishing/Forestry | **71.3%** | 29.5% |
| Bar visits > 1/month, no child passenger, not widowed | **71.3%** | 29.5% |
| Bar visits > 1/month and age < 30 | **72.2%** | 34.5% |
| Cheap restaurant visits > 4/month and income < $50K | **45.4%** | 40.1% |

## 3.2 Key Bar Findings

### Prior Bar Visitation

Drivers who visited bars **more than three times per month** accepted bar coupons at **76.9%**, compared with **37.1%** among drivers who visited bars three or fewer times per month.

This is a difference of nearly **40 percentage points**.

The high-frequency group contains only **199 observations**, however, so this estimate should be interpreted with caution.

### Age

Drivers over age 25 who visited bars more than once per month had a **69.5% acceptance rate**, substantially higher than the comparison group.

Younger frequent bar visitors also showed high acceptance. Drivers under age 30 who visited bars more than once per month had a **72.2% acceptance rate**.

### Passenger, Occupation, and Marital Status

Frequent bar visitors without child passengers also had high acceptance rates.

Adding occupation or marital-status conditions produced acceptance rates of approximately **71%**. However, the Farming/Fishing/Forestry and widowed groups are small, so these variables should not be interpreted as strong individual drivers without additional analysis.

### Restaurant Visits and Income

Drivers who frequently visited inexpensive restaurants and had incomes below $50,000 had a **45.4% acceptance rate**, compared with **40.1%** for the comparison group.

This relatively small difference suggests that **income and inexpensive-restaurant visitation are less informative for bar coupon acceptance than prior bar-going behavior**.

---

# 4. Independent Investigation: Coffee House Coupons

Coffee House coupons account for **3,996 of the 12,684 observations**, or approximately **31.5%** of all coupons.

The Coffee House coupon acceptance rate is **49.9%**, which is below the overall coupon acceptance rate of 56.8%.

About half of Coffee House coupon recipients reported visiting Coffee Houses either **never** or **less than once per month**.

---

## 4.1 Prior Coffee House Visitation

Prior Coffee House visitation was the clearest behavioral factor.

Drivers who visited Coffee Houses **more than once per month** had an acceptance rate of:

- **66.0%** for frequent visitors
- **34.6%** for the comparison group

This suggests that Coffee House coupons are substantially more relevant to drivers who already have an established Coffee House habit.

---

## 4.2 Age

Frequent Coffee House visitors over age 25 had a **63.8% acceptance rate**, compared with **42.7%** for all others.

However, this is slightly below the **66.0% acceptance rate for frequent Coffee House visitors overall**, suggesting that being over 25 does not add a stronger effect beyond prior visitation.

In contrast, drivers **under age 30** who visited Coffee Houses more than once per month had a **68.9% acceptance rate**, compared with **43.7%** for all others.

This exploratory result suggests that **younger frequent Coffee House visitors may be particularly receptive to Coffee House coupons**.

---

## 4.3 Occupation and Passenger Context

Frequent Coffee House visitors who:

- Did **not** have a child passenger, and
- Were **not Retired, Students, or Unemployed**

had a **64.4% acceptance rate**, compared with **43.6%** for all others.

Because 64.4% is slightly below the 66.0% acceptance rate for frequent Coffee House visitors overall, these additional occupation and passenger conditions do not appear to improve the segment beyond visitation frequency alone.

A separate segment of frequent Coffee House visitors who had **no child passenger and were not widowed** had a **66.1% acceptance rate**, compared with **36.2%** for all others.

Although the difference is large, the widowed population is small. Therefore, the result should **not** be interpreted as evidence that marital status itself is a major driver.

---

## 4.4 Destination and Time of Day

Driving context produced the strongest Coffee House segment in the analysis.

Frequent Coffee House visitors who:

- Had **no urgent destination**, and
- Were driving at **10 AM**

had an acceptance rate of **81.3%**.

The acceptance rate among all other Coffee House coupon recipients was **46.3%**.

> **Strongest observed Coffee House segment: 81.3% acceptance**

The target group contained **417 observations**, so it represents a smaller portion of the Coffee House sample and should be interpreted accordingly.

---

## 4.5 Income and Inexpensive-Restaurant Visits

Drivers who:

- Visited restaurants costing less than $20 more than four times per month, and
- Had annual incomes below $50,000

had a **54.3% Coffee House coupon acceptance rate**, compared with **48.9%** for all others.

Income below $50,000 alone showed a similarly modest difference:

- **52.3%** for the lower-income group
- **47.2%** for all others

These differences are much smaller than those associated with **prior Coffee House visitation and driving context**.

---

## 4.6 Weather and Temperature

Weather and temperature were also explored.

However:

- Observations are unevenly distributed across weather conditions.
- Temperature contains only three values: **30°F, 55°F, and 80°F**.
- The available analysis does not provide enough evidence to conclude that either weather or temperature independently improves coupon acceptance.

```

# 5. Conclusions

The exploratory analysis suggests that **historical visitation behavior is the most consistent indicator of coupon acceptance**.

Drivers who already visit bars or Coffee Houses regularly are substantially more likely to accept coupons for those establishments.

For Coffee House coupons, **contextual flexibility also appears important**. The highest observed acceptance occurred among frequent Coffee House visitors who had **no urgent destination at 10 AM**.

Demographic factors such as income, occupation, and marital status showed **smaller or less stable differences** once prior visitation behavior was considered.

### Overall Conclusion

> **Customer behavior appears to be more informative than broad demographic characteristics when identifying drivers who are likely to accept a coupon.**

A practical targeting strategy would therefore prioritize:

**Prior customer behavior → Driving context → Demographics**

---

# 6. Recommendations and Next Steps

1. **Target based on prior behavior.**  
   Prior visitation frequency produced the clearest differences for both Bar and Coffee House coupons.

2. **Use driving context for Coffee House offers.**  
   Frequent Coffee House visitors with no urgent destination at 10 AM were the highest-acceptance segment identified.

3. **Treat demographic findings as secondary.**  
   Income, occupation, and marital status were less consistently associated with acceptance, and some comparison groups were small.

4. **Validate the strongest segments statistically.**  
   Confidence intervals or hypothesis tests could help determine whether observed differences are robust rather than due to sampling variation.

5. **Perform sensitivity checks.**  
   Compare results:
   - With and without the 74 duplicated rows
   - With unknown visitation categories included and excluded

6. **Consider multivariable modeling as a future extension.**  
   Logistic regression or a tree-based model could estimate the contribution of multiple factors simultaneously and help distinguish correlated characteristics.

---

## Final Note

This project is based on survey responses and exploratory data analysis. The reported percentages describe **associations within this sample** and should not be interpreted as causal effects.

Operational recommendations should be validated using new data or controlled experiments before implementation.
