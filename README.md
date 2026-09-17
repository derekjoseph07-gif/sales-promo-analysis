# FMCG Promotion Impact & Demand Forecast

## Business Question
Are Rossmann's store promotions actually driving incremental sales, and does
the effect vary enough by store segment to recommend targeting promotional
spend more selectively?

## Data
Rossmann Store Sales dataset (Kaggle) — daily sales data merged with store-level
metadata (type, assortment, competition distance, secondary promotion details).

## Approach
Cleaned and merged sales and store data, engineered a feature to correctly flag
when each store's secondary promotion was actually active, ran a hypothesis
test to confirm the promo effect, built a regression to quantify it while
controlling for other factors, segmented the effect by store type and
assortment, and built two independent forecasts for near-term demand.

## EDA Summary
- Promo run 44% of the time, Promo2 15% of the time
- Daily Sales — right skewed, clustering between 5k-7k
- Store type b has a higher median than others
- Promo v Non-Promo — 8200 vs 5900

## Results
1. Promos are found to be run 44% of the time from the Train data. During Non Promo v Promo periods, there is a lift to 8200 from 5900 sales per store, which is a ~38% lift.
2. Hypothesis t-test testing was done to show there is a statistically meaningful difference in Non Promo v Promo periods.
3. After a regression model was run, it was shown Promo has a strong effect on sales, but the effect is not similar. Assortment b stores respond weakly to Promos (only ~7% lift, vs 36-43% for Assortment a and c). Store type B has the highest base revenues but lowest proportional increment during Promos.
4. A hand-built formula for seasonal growth forecast showed 178 mil sales for Aug 2015, where the base is taken as Aug 2014 which had 163 mil (monthly total, scaled up by recent growth trend).
5. Regression-based prediction is used to calculate extremes — zero promotional activity on all days vs full month promotional activities run — and the range is 207 mil to 285 mil for Aug 2015.

**Additional notes:**
- Store b, Assortment c has a small sample of store-days — in total, type b has a much smaller number of stores overall
- Type B has the smallest relative promo lift (18%) and the highest baseline sales
- Assortment b shows a weaker promotional response (7% lift) than Assortment a or c (36-43% lift), across all store types

## Recommendations
There is a confirmed and significant positive effect of the promo being run, and it should be continued to increase sales. However, the varying response by assortment and store types suggests that the budget can be used more efficiently. Assortment b should be a low priority, while channeling larger budgets for stores carrying assortment a & c. Similarly, while store type b has a higher baseline revenue, store types a, c, d should be given higher priority in promotion allocations.

**Note:** These recommendations are based on a linear regression with an R² of ~0.19, meaning other unmeasured factors also meaningfully influence sales — further analysis would strengthen confidence before large-scale budget reallocation.

## Tools
Python, pandas, numpy, matplotlib, seaborn, scipy, statsmodels

## Notes
This was completed as a self-directed project while transitioning into data
analytics from a background in retail/consumer sales — as a first step in
building applied statistical and analytical skills rather than a finished,
expert analysis.
