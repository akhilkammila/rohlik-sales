# Notes from Others notebooks

## Own Starter Notebook

Attempted very simple lagged sales by unique id LGBM --> 22 submission score
How did starter lagged feature notebook do so much better?

## 1. Starter Lagged Features, MAE 20.75
Notebook: https://www.kaggle.com/code/hiarsl/starter-notebook-with-lagged-features-lb-20-25#Modeling 

1. Added new holidays
Added Easter, Mothers Day, Holy Saturday as holidays (by warehouse)

2. Added interesting holiday features
- days to next holiday
- days to next shops closed
- day before/after shops closed
- long weekend (multiple holidays in a row)

3. Static features
- datetime features
- discount sums, max
- interactions (division) of total orders, sell price, and discount

4. Predicted on y**(1/8), mae
In reality, it is probably better to Sqrt y --> MSE loss as per
https://www.kaggle.com/competitions/rohlik-sales-forecasting-challenge-v2/discussion/563064

Because the target follows the tweedie distribution (many close-to-0s)

## 2. 3rd Place Simpler Notebook, MAE 17.8

1. Count + discount features
- max discount
- num. of items with same common name for that warehouse
- discount avg. for this item-warehouse
- number of warehouses this item is in, for a given day

2. Combined features
- number of days in last 28 with any sales (this just uses whether the row is there or not, so no leakage)
- price scaled (in terms of std. from mean for that same item)
- price detrended (price scaled - avg. price scaled for that day over ALL items)
- median total orders for a warehouse (each point smoothed with ewm)
    - rolling last 14d
    - ewm 56

3. Holiday features (similar to prev notebook)
- days since last holiday, day to next holiday (per warehouse)

4. Historical sales features
- last sales ema: uses exponential moving average to effectively do rolling sales for 14d, ignoring NA values


General Tip - Shap Importance
- look at shap partial dependence plot
- shows shap importance (how feature val. impacts prediction), but hued by other var