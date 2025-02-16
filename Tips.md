From https://www.youtube.com/watch?v=XBJ2f68LuO4

1. General Advice

- Start with simple model, iterate fast

2. Feature Importance
- Start spamming features
- Don't try to eliminate low ranked features, instead look at high value ones
- Add noise variable to see how it is ranked

- Later on, delete bad features, keep and transform good features

3. Feature Engineering
- How to tell if new feature is good?
- Use RandomizedKFold
    - 3 bags of 3-fold is better than 5-fold

- Powerful feature: feature X - avg. feature X over a group
    - note that group could be categorical, or numerical discretized
    - ex. for 2 sigma competition, they found Technical Indicators - avg. indicator val for that day
- Try features together
    - feature 1: avg. feature X over a group
    - feature 2: feature X - avg. feature X over a group
    - might need to also know what the mean is, not just how it compares to the mean

4. Outliers (in Y var)

- 1. keep outliers --> baseline score
- 2. winsorize outliers (make less extreme)
- 3. remove outliers > x (search for x using cross-val)

- make sure that added features are not just randomly helping with an outlier

5. Additional Tips

- create dif. models with different subsets of models --> then blend
- okay to let models overfit when bagging (ensembling)
- lot of features --> use small feature fraction lgbm hyperparameter (makes trees less correlated)

- use NN baseline --> remove feature to see if it was doing FE with it
- when replacing null values (with an avg. or something), add bool isNull column

- use linear model to capture linear trends --> feed into lgbm