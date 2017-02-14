
- tmock : to run long experiments
- parallelize to make it fun faster.
- GPU from amazon
- alexnet is publicly available
- standard practice is to grab a neural net that is well known.
- neural net is a good function estimator
- interpretability:

## How to train a Multilayer Perceptron (MLP)
- softmax regression: classification model that learns to map an input vector x to a probability distribution p(y|x) where y is a categorical value with k different values.  
  - in other words, mapping X to P(y|X)
  - train this by maximizing log likelihood:
In statistics, a likelihood function (often simply the likelihood) is a function of the parameters of a statistical model given data. Likelihood functions play a key role in statistical inference, especially methods of estimating a parameter from a set of statistics.
  - this is logistic regression that can have multiple classes
- Multilayer perception model
  - assumption: the relationship between inputs and outputs can be represented by a composition of several simpler functions.
  - each function is thought of another layer in processing

# pylearn2

## Getting data in
- You need to write a python wrapper class !
- 
## Getting predictions
