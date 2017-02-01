# summary
- DF<sub>residuals</sub>
  - no. of observations - (p+1)
  - you need at least 3 to get an assessment of a line.
  - if you have 3 dimensional, you need 4. 3 will give you a plane.
  - Degrees of freedom: how many points beyond what's required do I have.
  - p + 1, is basically # of dimensions plus  intercept.
  - DF<sub>model</sub>: number of features not including intercept.

- R<sup>2</sup>
  - 1 - (SSE/SST)
    - SSE = sum of squared errors
      - Randomness left in the model.
    - SST = total sum of squares
      - Variation in the data.
  - if SSE is proportionally bigger than SST, it's not good.
- T-Test
  - H<sub>0</sub>: B<sub>i</sub> = 0
  - H<sub>a</sub>: B<sub>i</sub> != 0
  - Determine critical value (usually alpha = 0.5)
  - Calculate t-stat
    - B / SE
    - Lookup table to get the p value.
    - Reject or keep?
  - Intercept: Do we reject our intercept?
    - no.
    - Force line to go through the intercept.
- F-Test
  - H<sub>0</sub>: B1 = B2 = B3 = 0
    - All betas are zero
  - H<sub>a</sub>: B<sub>i</sub> != 0
    - At least one of them is 0
  - assessing the strength of the odel together.
  - You also get a P-value, if the p-value is small enough you reject the null.
- Log Likelihood
  - Another cost function to evaluate a model
  - Better if it's closer to 0

- Skew
  - |S| >= 1.9
  - negative number for negative skew
  - 3(mean - med) / std
    - of residuals
  -
Omnibus
  - Normality test
  - H<sub>0</sub>: No skew
  - If p is small, then we have to reject the null hypothesis. There is definitely a skew.
Kurtosis
  - High peak = high kurtosis.
  - Above 7 = peak not within normal distribution range.

- JB
  - Normality test.
  - Normal distribution is the null hypothesis.

- Durbin-Watson
  - autocorrelation test
  - Errors are uncorrelated

- Condition number
  - Large if there's multicollinearity
  - Not be able to solve the determinant

- AIC
  - # of parameters - 2ln(L) 
