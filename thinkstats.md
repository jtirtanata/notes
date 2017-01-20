# Chapter 2
## Distributions
### Histogram
- A histogram can give us clues to
  - *central tendency*: Do the values tend to cluster around a particular point?
  - *modes*: Is there more than one cluster?
  - *spread*: How much variability is there?
  - *tails*
  - *outliers*: Are there extreme values far from the mode?
## Variance
- Describes the variability or spread of a distribution.
## Effect size
- Summary statistic to describe the size of an effect.
- One way to describe the difference is the difference in the means.
- **Cohen's D**: compare the difference between the groups to the variability within the groups. It is defined: d = (x1 − x2)/s
  - Where x1 and x2 are the means of the groops and s is the pooled standard deviation.
  - Pooled standard deviation is calculated by multiplying the variance with a fraction that represents the number of samples or the group over the number of total samples.
# Chapter 3
## Probability mass functions
- Like a histogram, but maps each value to its probability. The probability is a frequency expressed as a fraction of the sample size, n.
- Probability is frequency divided by n. This is also called normalization.
## Actual vs Biased distribution

# Chapter 5
## Normal distribution
- Also called Gaussian distribution
- Normal distribution is characterized by two params: mean and standard distribution
- `scipy.stats.norm` represents its cdf.
- Mean and Median is 0

## Normal Probability Plot
- Simple transformations to test if the distribution is a good fit for the model doesn't exist for the normal distribution (unlike exponential dist.).
- You can use a normal probability plot:
  - Sort the values in the samples
  - From the standard normal distribution (mean = 0, s = 1), generate a random sample with the same size as the sample.
  - Plot the sorted values from the sample vs. the random values.
  - If the distribution is normal, the result is a straight line with mean = intercept and s = slope.

## Lognormal
- Same as CDF of normal distribution, but CDF of lognormal of x = CDF of (log x)
- There are formulas for the mean and std

## Pareto distribution
-  Was used to describe the distribution of wealth.

## Why Model?
- Many real world phenomena can be modeled with analytic distribution
- It is a form of data compression. A small set of params can summarize a large set of data.
- Important to remember that models are imperfect. There are always differences in the real world and the mathematical model.

# Chapter 6
## PDFs
- derivative of CDF
- = λe^(−λx)
- pmf vs pdf: pmf is used for discrete distributions. It assigns a probability to each point in the sample space. Pdf is for continuous distribution.
- Pdf is an *absract* class, so it can't be instantiated. You have to inherit from it and provide definitions for Density and GetLinsSpace.

## Kernel Density Estimation
- Takes a sample and finds an appropriation for PDF

## How the functions are connected
- PMF = probability for a discrete set of values
- PMF -> CDF = Compute differences in cumulative probabilities
- PDF is the derivative of a continuous CDF.
- PDF maps from values to probability densities. Thus, to *get a probability* you have to integrate.
- From discrete to continuous - you can apply smoothing. To smooth ,you assume that the data comes from a continuous distribution (like exponential or normal). Or kernel density estimation.
- To discretize (opposite of smoothing), you can use numerical integration.

## Hist implementation
- Hist and Pmf inherit from \_DictWrapper. The values is mapped to their frequencies.
- Incrementing adds 1 to the frequency value.

## PMF implementation
- Hist and PMF are the same, except that PMF maps to floating-point probabilities rather than integer frequencies. To instantiate pmf, you will normalize the list of values.

## CDF implementation
- CDF maps values to cumulative probabilities.
- Implemented using two sorted lists. One is the sorted list of values, and the other one is the corresponding frequencies. Dividing by the total frequency yields the cumulative probability.

## Moments
- Formula is to add all of the values times to the power of k, divided by the number of samples. The result is the kth moment.

## Skewness
- Skewness can be measured by calculating the standardized moment. Moment is needed to calculate this value.
