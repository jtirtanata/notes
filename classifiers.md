#### Pair Question

For each question below, say yes, no or somewhat for these classification algorithms: KNN, Logistic Regression, Linear SVC, SVC, Decision Tree, Random Forest and Naive Bayes.

    1) Is it interpretable?

    2) Is it inherently multi-class?
    3) Is it scalable with large number of features (in terms of execution time and quality of results)?
    4) Is it scalable with large number of data points (in terms of execution time and quality of results)?
    5) Is it good with diverse (non-homogenous) set of features?

|   |KNN|Logistic Regression|Linear SVC|SVC|Decision  Tree| Random Forest| Naive Bayes
|:-:|---|----|----|----|----|----|----|----|:-:|
|Interpretable|No|Yes|Yes|Difficult - Depends on the transformation|Yes|You get feature importance|Maybe|
|Multi class|Yes|No|No|No|Yes|Yes|Yes|
|Scalable (features)|No|Yes|Yes (Like LG)|No|No, If you cut the tree length, you might not get the features that are good. If you don't, it will overfit.|Yes|Yes|
|Scalable (data points)|No|No|Yes|No|Yes|Yes|Yes|
|Diverse features|No (It's distance related)|   |   |   |   ||No (hard to add features that are not probabilities)|
