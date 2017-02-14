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

# SVM
- another distance metrix: cosine
- kernel = transformation
- it's all driven by dot product
- you can linearly separate your data by using a kernel.  
- How do you choose ?
  - with 3 dimension, it's pretty easy
- You can tune for c
  - c = [1, 10, 100, 1000]

- Use gridsearch to march through all of the parameters and give you the best option.
- Hyperplane = if you have more than 3 dimensions
- What determines the hyperplane
  - C, kernel, w
- few support vectors: OVERFIT!
  - just picking 2 training points and making a line.
- many support vectors: generalized.
- Outliers does not play a part. (if you're on the right side!)
  - Usually you don't have outliers at the wrong side.
- Cost?
  - Training is expensive.
  - But once you train, test is not that bad.
- You have to scale because this is still using the distance metric.
- USE standard scaler.
- Normalize beings it from 0 to 1.

# Preprocessing
- preprocessing.normalization
- only for svm: standard scaler

# Dummy variables
- add intercept for logistic regression (sklearn doesn't add it automatically!)
- knn no intercept needed
- svm - sklearn adds it automatically

## Accuracy metrix
- Confusion Matrix
- If your classes are unbalanced, do recall or precision
- F1 = harmonic mean
- Depends on your case. See which one is more important.
- Type 1 or Type 2 error:
- In logistic regression:
  - Higher threshold: More sure about positives: lower recall, higher precision.
- Each threshold is a different model.
- ROC curves
  - How good a model is the AUC
  - Sensitivity vs. 1-specificity

# Decision Trees
- Break it down to a bunch of decisions
- Prone to overfit
- How?
  - Greedy:
    - Have all combinatorics
  - Non-greedy
    - Start with a good fit.
    - Quantification ?
      - ginny: 1- (sum of probabilities of each class)^2
      - entropy: kinda do the same thing.
      - basically, make a split where you can bunch up one class as much as possible.
      - For numerical, it splits it based on the best k.
      - How to do it
        - If too little samples, don't split
        - Max depth
      - Use multiple trees  (and then avg it later)
        - How to change it (a little bit)?
        - Sample with replacement.
        - This is called tree bagging.
        - Randomly choose features.
Avoid overfit
- Tree - WILL OVERFIT
- Random forest
  - performs really well
  - not interpretative
  - Can give you the feature importance
- 
