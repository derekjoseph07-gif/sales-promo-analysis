# Rossman Promotion Impact and Demand Forecast

Analysis of Rossmann store promotions using the Kaggle Rossmann Store Sales dataset. The project tests whether promotions drive incremental sales, how the effect differs across store segments, and what that means for August 2015 demand.

## Business question

Do store promotions drive incremental sales, and does the effect vary enough by store segment to justify targeting promotional spend more selectively?

## Data

Daily store-level sales merged with store metadata: store type, assortment, competition distance and secondary promotion (Promo2) details.

## Approach

1. Cleaned and merged the sales and store tables.
2. Built a feature to flag when each store's secondary promotion was actually active on a given day, rather than just enrolled.
3. Tested the promotion effect with a hypothesis test.
4. Fitted a regression to quantify the effect while controlling for other factors.
5. Segmented the promotion effect by store type and assortment.
6. Produced two independent forecasts for August 2015.

## Findings

Promotions run on about 44% of store-days, and Promo2 on about 15%. Daily sales are right-skewed and cluster between 5k and 7k. Store type b has a higher median than the other types.

Average sales per store are 8,200 on promotion days against 5,900 on non-promotion days, a lift of roughly 38%. A t-test confirmed the difference between the two groups is statistically significant.

The regression shows a strong promotion effect, but it is uneven across segments:

- Assortment b stores respond weakly, with a lift of about 7%, compared with 36-43% for assortments a and c. This holds across all store types.
- Store type b has the highest baseline sales but the lowest proportional lift from promotions (about 18%).
- Store type b with assortment c has few store-days, and type b has far fewer stores overall, so those estimates are less reliable.

Forecasts for August 2015:

- A seasonal growth formula takes August 2014 (163M in monthly sales) and scales it by the recent growth trend, giving about 178M.
- Regression-based scenarios give a range of 207M (no promotions on any day) to 285M (promotions on every day). These are bounds, not a central forecast.

## Recommendations

Promotions should continue, since the effect on sales is positive and significant. The variation by segment suggests spend can be allocated more efficiently:

- Treat assortment b as lower priority and direct larger promotional budgets to stores carrying assortments a and c.
- Although store type b has the highest baseline revenue, types a, c and d should be prioritised for promotion allocation.

## Limitations

- The regression has an R² of about 0.19, so other unmeasured factors influence sales substantially. Further analysis is needed before any large reallocation of budget.
- The seasonal estimate (178M) is below the no-promotion scenario (207M). The gap was not investigated, and the two methods should not be treated as directly comparable.
- Segment results for small groups, such as type b with assortment c, are based on limited data.

## Tools

Python, pandas, numpy, matplotlib, seaborn, scipy, statsmodels
