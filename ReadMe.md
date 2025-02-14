## Overall Progress

1. EDA
Looked at items appearing/disappearing
    - seems to follow some curve that increases, then drops
    - items in test are all also in train

Item gaps
    - a lot of items disappear and then come back (different skews)

2. Modelling
Simple LGBM
- lag, group features
- datetime features

3. Other learning
- waves: calendarfourier for sin/cos waves
- clustering: hierarchical clustering + dendogram for automatic clustering
    - plotly treemap or anytree for visualizing already grouped data