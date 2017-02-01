**4 types of supervised learning algorithm**
- Regression: numeric answers
- Classification: categorical answers
  - Breast cancer surgery data = survive/lost

## Vocab
- Target: what you want to predict
- Label: 0/1, (survived or lost)
  - Can have more than 2 (healthy/complications/lost)
- Feature: # of malignant nodes
- Examples: known info

## K nearest neighbors
- Look at the k nearest neighbor
- Voting scheme
- Results in a **KNN Decision Boundary**
- Overfit
  - K = 1
- Generalized
  - straighter boundaries
- Underfit
  - k near the #of examples
- "Lazy"
   - Doesn't bother to do a fit until you have a test data
   - Fits fast, predicts slow.
   - Higher memory to save entire data set
- Do relatively well for linearly inseparable classes
- `metric="minkowski"`
  - manhattan algorithms
- Good for small features, and distance related features.
- Multicollinearity may affect: same features would skew your result.
- Beyond 3 dimensions, KNN is not the right metric.
  - Curse of dimensionality

## Parameters : things you can change
- Regularization = alpha
- KNN = k
- RandomizedSearchCV
  - Take 10 random neighbors and check the score.
  - You can use this, and then GridSearch if you don't want things to be too slow.

# Logistic Regression
- 1 = positive, and it's the output we want to identify
- Linear Regression for classification ?
  - Can't really work
- Use logistic regression instead !
  - a.k.a. sigmoid function
- P(loss)/P(survival) = ODDS
  - logic function
  - inverse function of sigmoid
  - logit function
-

- Logistic Regression
  - Penalty
    - l2 = regularization
  - tolerance = convergence ?
  - C
    - C = 1.0
    - Inverse of alpha
    - Lower c, higher alpha, higher penalty.
    -
  - 'ovr' = one versus rest
    - or multinomial (most likely ovo)
    - Nice interprobability
    - Get probabilities
    - How certain we are.

  - See the ones that are close to 0.5 - maybe something more interesting
  - Logistic doesn't overfit in general, compared to KNN.
  - Low variance, high bias.
  - Can handle categorical really well.
  - SCALE features
  -

  
