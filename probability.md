# Discrete Probability
- Variables are independent

## Variance
- For every outcome, take the probability of that outcome, the v
- Expected value

## Conditional Probability
- If independent, you simply multiply everything.
- Coin toss:  P(H) * P(T|H) = 0
  - Probability of getting a head *and* getting a tail
  - P(A ∩ B) = P(B) * P(A|B)

### Monte Carlo Problem
- 3 doors, select 1, a door is revealed. Should you switch ?
  - Initially, 2/3 chance in empty door.
  -
- Variation 1: Door opened can be empty or not empty.
- Variation 2:
- In the variations, it doesn't matter wif you switch, the probabilities are the same.
- For the original question, it's better to switch.
- Try to break this down with Bayesian Theorem

# Evaluation
- How good is a prediction?
  - Null Hypothesis:
  - Probability function for number of correct predictions
  - What's a reasonable threshold? 5%
  - Before we start the experiment, **A/B Testing**, we usually pick a cutoff  

**Confidence Level**
- That cutoff.
- Usually 95% or 99%

**Determining Sample Size**
- Choose a Confidence Interval.
- Given the population number, you can get a number calculated for the sample size you need for the confidence interval and level that you want.
- You can also go the other way. With the sample size, you can calculate what you confidence interval or not.

**Binomial Distribution**
- Python has a library.
```
from scipy.stats import binom
print binom.ppf(0.95,100,0.5)
# 58
```

- Predicting mean
- **Balance** or **Bias**
