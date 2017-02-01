# Model Evaluation
- Need to choose between machine learning models
- Estimate how a model will predict out-of-sample data
- Split train and test data, to avoid **overfit**

## Cross Validated Regression
- Problems with training and testing the model on the same data set: overfit. **Cross validation** is needed to evaluate our model. What htis means is to train our model based on 1 set of data, and evaluate it with a separate random test set.

## Train/Test Split
  - Has a test, train, split function.

```python
# Split the data into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)
# Fit the model against the training data
lr.fit(X_train, y_train)
# Evaluate the model against the testing data
lr.score(X_test, y_test)
```

- Code turns around 30% of the data to test data.

## K-Fold Cross Validation
- Steps:
  1. Split data to K equal partitions (K is usually 10)
  - At each iteration: turn 1 fold to test data, and the union of the other folds as train data.
  - Calculate training accuracy.
- Average **training** performance becomes the estimate of out-of-sample performance.
- **Benefits**:
  - More reliable for out-of-performance than train and split
  - can be used for selecting **tuning parameters**
- Drawbacks: computationally expensive.  

```python
from sklearn.cross_validation import cross_val_score
# 10-fold cross-validation with our fake data
reg = LinearRegression()
scores = cross_val_score(reg, X, y, cv=10, scoring='mean_squared_error')

# scores output is negative, a sklearn quirk bc mse is used to min. optimization func.
print(-scores)
```
