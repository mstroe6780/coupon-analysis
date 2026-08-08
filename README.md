# practice
Practice for AI ML Certificate

Will the Customer Accept the Coupon? 
Exploratory Data Analysis Report

# Objective: identify characteristics and driving contexts associated with coupon acceptance, with particular attention to bar coupons and an independent investigation of Coffee House coupons.

Executive Summary
Across 12,684 observations, 7,210 drivers accepted the offered coupon, for an overall acceptance rate of approximately 56.8%. Acceptance varied substantially by coupon type and by prior customer behavior. Bar coupons had a relatively low acceptance rate (41.0%), while Coffee House coupons were accepted 49.9% of the time.
The strongest pattern in both analyses was prior visitation behavior: drivers who already visited the relevant type of establishment more frequently were much more receptive to its coupon. For Coffee House coupons, driving context also mattered. Frequent Coffee House visitors with no urgent destination at 10 AM had an 81.3% acceptance rate, compared with 46.3% for all other Coffee House coupon recipients.
These results are exploratory associations rather than causal effects. We have to consider that small subgroups, survey design limitations, and a lack of unique respondent identifiers may impact the validity of our findings.

1. Data Quality and Preparation
The original dataset contains 26 variables describing driver characteristics, driving context, prior visitation behavior, coupon characteristics, and whether the coupon was accepted. Column names were standardized to improve readability and consistency.
Missing Values
•	Six variables contain missing values.
•	The car variable is more than 99% missing. Because it provides very little usable information, it was removed.
•	The other five variables with missing values — Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, and Restaurant20To50 — each have less than 2% missing data.
•	For these five variables, missing values were assigned to an "unk" category so they could be retained or excluded depending on the analysis.
•	A separate dataset excluding selected "unk" observations was created for analyses where unknown visitation frequency could affect the comparison.
Duplicate Rows
The dataset contains 74 duplicated rows. Approximately 66% of the duplicated rows involve Carry Out & Take Away coupons. Because there is no unique respondent identifier, it is not possible to determine whether these are repeated submissions or different respondents with identical survey answers. The duplicate rows were therefore retained for the initial EDA rather than removed without evidence.
Data Types and Redundancy
Most variables were initially stored as object data. Their unique values and distributions were reviewed before conversion to categorical or numeric formats. Income was treated as an ordered categorical variable so that income groups show in ascending order in tables and graphs.
•	toCoupon_GEQ5min contains only the value 1 and therefore has no variation; it was removed.
•	direction_same and direction_opp are complementary; direction_opp was removed to avoid redundant information.
•	A working copy of the original dataset was created before cleaning so the source data remained unchanged.

2. Overall Coupon Acceptance
Approximately 56.8% of all observations accepted the coupon: 7,210 accepted out of 12,684 total observations. This overall rate provides a useful benchmark for comparing coupon types and customer segments.

3. Bar Coupon Analysis
Bar coupons were accepted in 41.0% of cases, making them one of the lower-acceptance coupon categories. The analysis indicates that prior bar-going behavior is strongly associated with acceptance.
Comparison	Target Group	All Others / Comparison
Bar visits >3/month	76.9%	37.1% for ≤3/month
Bar visits >1/month and age >25	69.5%	33.4%
Bar visits >1/month, no child passenger, occupation not Farming/Fishing/Forestry	71.3%	29.5%
Bar visits >1/month, no child passenger, not widowed	71.3%	29.5%
Bar visits >1/month and under age 30	72.2%	34.5%
Cheap restaurant visits >4/month and income < $50K	45.4%	40.1%
Key Bar Findings
•	Drivers who visited bars more than three times per month accepted bar coupons at 76.9%, compared with 37.1% among drivers who visited three or fewer times per month. The high-frequency group is small (199 observations), so its estimate should be interpreted with caution.
•	Drivers over age 25 who visited bars more than once per month had a 69.5% acceptance rate, substantially above the comparison group.
•	Frequent bar visitors without child passengers also showed high acceptance. Adding occupation or marital-status restrictions produced rates around 71%, but the excluded Farming/Fishing/Forestry and widowed groups are small, limiting conclusions about those characteristics individually.
•	The inexpensive-restaurant and lower-income segment showed only a modest difference (45.4% versus 40.1%), suggesting that these characteristics are less informative for bar coupon acceptance than prior bar visitation.

4. Independent Investigation: Coffee House Coupons
Coffee House coupons account for 3,996 of the 12,684 observations (about 31.5%). Their acceptance rate is 49.9%, below the overall coupon acceptance rate. About half of Coffee House coupon recipients reported visiting Coffee Houses either never or less than once per month.
Prior Coffee House Visitation
Prior visitation was the clearest behavioral factor. Drivers who visited Coffee Houses more than once per month had a 66.0% acceptance rate, compared with 34.6% among the comparison group. This suggests that coupons are substantially more relevant to drivers who already have an established Coffee House habit.
Age
Frequent Coffee House visitors over age 25 had a 63.8% acceptance rate versus 42.7% for all others. However, this rate was slightly lower than the 66.0% rate for frequent Coffee House visitors overall, so being over 25 did not add evidence of a stronger effect.
In contrast, drivers under age 30 who visited Coffee Houses more than once per month had a 68.9% acceptance rate, compared with 43.7% for all others. The exploratory results therefore suggest that younger frequent Coffee House visitors may be especially receptive.
Occupation and Passenger Context
A segment of frequent Coffee House visitors with no child passenger and occupations other than Retired, Student, or Unemployed had a 64.4% acceptance rate, compared with 43.6% for all others. Because this rate is slightly below the 66.0% rate for frequent Coffee House visitors overall, the additional occupation/passenger restrictions do not appear to improve the segment beyond visitation frequency alone.
A separate segment of frequent Coffee House visitors with no child passenger and who were not widowed had a 66.1% acceptance rate versus 36.2% for all others. This is a large observed difference, although the widowed population is small; the result should not be interpreted as evidence that marital status itself is a major driver.
Destination and Time of Day
The strongest Coffee House segment combined prior behavior with immediate driving context. Frequent Coffee House visitors who had no urgent destination at 10 AM accepted the coupon at 81.3%, compared with 46.3% among all other Coffee House coupon recipients. The target group contained 417 observations, so the result is meaningful for EDA but represents a smaller segment of the Coffee House sample.
Income and Inexpensive-Restaurant Visits
Drivers who visited restaurants costing less than $20 more than four times per month and earned less than $50,000 had a 54.3% Coffee House coupon acceptance rate, compared with 48.9% for all others. Income below $50,000 by itself produced a similarly modest difference: 52.3% versus 47.2%. These differences are much smaller than those associated with prior Coffee House visitation and driving context.
Weather and Temperature
Weather and temperature were explored visually, but the data are unevenly distributed across conditions and temperature has only three values (30°F, 55°F, and 80°F). The current notebook does not provide sufficient evidence to conclude that weather or temperature independently improves coupon acceptance.
Technical note: the current temperature comparison uses a string value ("30") in the filter. Because the temperature field may be numeric/categorical rather than a string, that comparison should be corrected and rerun before reporting a warm-versus-cold acceptance result.

5. Conclusions
The EDA suggests that historical visitation behavior is the most consistent indicator of coupon acceptance. Drivers who already visit bars or Coffee Houses regularly are substantially more likely to accept coupons for those establishments. For Coffee House coupons, contextual flexibility also appears important: the highest observed acceptance occurred among frequent Coffee House visitors with no urgent destination at 10 AM.
Demographic factors such as income, occupation, and marital status showed smaller or less stable differences once prior visitation behavior was considered. These findings support a targeting strategy centered first on demonstrated customer behavior and then on relevant driving context.

6. Recommendations and Next Steps
1.	Target based on prior behavior. Prior visitation frequency produced the clearest differences for both bar and Coffee House coupons.
2.	Use driving context for Coffee House offers. Frequent Coffee House visitors with no urgent destination at 10 AM were the highest-acceptance segment identified in the analysis.
3.	Treat demographic findings as secondary. Income, occupation, and marital status were less consistently associated with acceptance and some comparison groups were small.
4.	Validate the strongest segments statistically. Use confidence intervals or hypothesis tests to determine whether observed differences are likely to be robust rather than sampling variation.
5.	Perform sensitivity checks. Compare results with and without the 74 duplicate rows and with unknown visitation categories excluded.
6.	Consider multivariable modeling as a future extension. A logistic regression or tree-based model could estimate the contribution of multiple factors simultaneously and help distinguish correlated characteristics.

Note
This project is exploratory and based on survey responses. The reported percentages describe associations in this sample and should not be interpreted as causal effects. Operational recommendations should be validated on new data or through controlled experiments before implementation.

