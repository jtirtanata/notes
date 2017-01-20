# Libraries
1. statsmodels
  - best at regressions
3. scikit-learn
  - machine learning package
  - linear regression

## Seeing correlation
- ***seaborn***
  - If some of the variables are highly correlated, it could suggest *multicollinearity*. This is something to watch out as it can **destabilize** our model.
  - See which variables are correlated with the **target variable Y**
  - `sns.pairplot(df, size= 1.2, aspect=1.5)`
- ***pandas***
  - `df.corr()`
  - it will give the correlations between the different variables
- ***statsmodels***
  - package:   
    - `import statsmodels.api as sm`
    - `import statsmodels.formula.api as smf`
  - **patsy** can make your **feature matrix** (X) and **target vector** (y)
    - `y, X = patsy.dmatrices('Y ~ X1 + X2 + X3 + X4 + X5 + X6', data=df, return_type="dataframe")`
  - Create a model: `model = sm.OLS(y, X)`
    - You can also make a model immediately, cutting out the previous step.
    - `model = smf.ols('Y ~ X1 + X2 + X3 + X4 + X5 + X6', data=df)`
  - Fit the model: `model.fit()`
  - Print summary: `model.summary()`
  - What to do?
    - R<sup>2</sup>: represents the estimated percentage of the variance in our target variable Y that can be explained by our regression model
    - Adjusted R<sup>2</sup> adjusts for overfitting. Penalize large coefficients.
    - Table of coefficients found by the regression. Along with the standard error of each coefficient.
    - Look for a low P value
      - The t-scores are values that the coefficients score in the Student's T Distribution and the P(|t|) field represents the probability of finding such a t-score if the actual value of the coefficient were 0.
      - Measures our degree of belief that the coefficient for each variable should be zero. - Thus, the lowest P-values represent the most likely predictors to be impacting the response.
    - Final column returns a 95% Confidence Interval for the value of each coefficient.
- ***sklearn***
  - Can pull the summary variables individually
  - Don't get a nice summary like Patsy
  - sklearn is very rich, lots of things that we can use.
  - `predict()` will predict the target variable based on the sample of independent variables

## Residuals
- Plot residuals using statsmodels: `fit2.reside.plot(style='o', figsize=(12,8))`
  - This is pulling in from seaborn



### Pickling for these models
- pandas df
  - `df.to_pickle(<path>)`
- statsmodels
  - `fit2.save(<path>)`
- sklearn
  - `import joblib.dump`

## Polynomial Regression
- statsmodels is decent for linear models, but **scikit-learn** provides for all sorts of models and algorithms.
- Common interface for scikit models:
  - `fit()`: fit a model to training data
  - `score()`: score the performance of the model given a sample data with known dependent variables
  - `predict`: predict target variables based on a sample of independent variables.
- Def: Model our response variables as any function of our predictor variables
- built-in options for converting predictor variables to polynomial functions :
  - `PolynomialFeatures`
    - class to manipulate incoming predictors into nth-order polynomials of those features.
  - `make_pipeline` function: string together a pipeline of operations that is able to first transform our linear features into polynomial features and then run a linear regression against the resulting polynomial features.
```
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
```
- Steps:
 1. Use PolynomialFeatures(n) to create a generator of n degree polynomials
 - Feed this generator to make_pipeline along with a LinearRegression object.
    - resulting model object that has the same fit(), score(), predict(), etc functions
  - Call fit() on our new object to fit a n degree polynomial regression
 - Plot results

- predict the # degree
  - Higher degree - can be overfit.
    - Overfit: getting another training set will produce a different value

## What to do with missing values
- groupby and replace the mean with those groups?

## Dummy variables
- Patsy allows us to work with dummy variables
  - Problem because it's not a number
  - Transform each text to a number
  - **The Dummy Variable Trap** 1 column is dropped so that we don't have Multicollinearity

# Theory
## LMS Algorithm
- Approach: choose θ to minimize J(θ). Start with an initial guess for θ and repeatedly change θ until we converge to a value θ that minimizes J(θ)
- **learning rate**: denoted by α

### Stochastic gradient descent
- Update parameters according to a single training example only.
- This is faster, because batch gradient descent has to scan through the entire training set before it can take a single step.
