# OLS Regression results
- look at Adj. R-squared, AIC, BIC.
- Gets a goodness of fit

**AIC**
- AIC is a way to compare our models.
- We want it to be low.
- Sum of our squared errors.
- AIC increases if number of parameters goes up.

**Adjusted R<sup>2</sup>**
- Penalized with higher K as well

**Cost function**
- Magnitude of Betas ?
- High number of Betas or large betas will be a penalty

Diagnostics: **Ridge Regression**
- Underfitting: high cost, low beta score
- Just right: low, low
- Overfitting: low, high
- Lambda: making the beta values for the RHS
  - *sklearn calls it alpha*
- J<sub>cv</sub> and J<sub>train</sub> will start to diverge if you overfit

**Lasso**: Feature elimination  
**Ridge**: Strength of features

# Steps
1. Scale your features  
```
from sklearn import preprocessing
X_sc = preprocessing.scale(X)
```

  - This turns mean = 0, var = 1
- log(10) alphas
- You can make k-folds, and take the means of the MSE
