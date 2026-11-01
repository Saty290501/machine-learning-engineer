# ML Algorithms from Scratch

I use these implementations to expose the mechanics hidden behind a library call. The goal is not to replace scikit-learn; it is to understand the inputs, assumptions, numerical choices, and failure cases well enough to use libraries responsibly.

## Algorithms in scope

- [ ] Linear regression with a closed-form solution and batch gradient descent.
- [ ] Logistic regression with a numerically stable sigmoid and binary cross-entropy.
- [ ] Gaussian and Multinomial Naive Bayes, with the feature assumptions made explicit.
- [ ] K-nearest neighbors with configurable distance and a clear scaling requirement.
- [ ] K-Means with initialization, convergence criteria, and sensitivity checks.
- [ ] Decision-tree splits using Gini impurity or entropy.
- [ ] PCA with covariance eigendecomposition or singular value decomposition.

## Implementation rules

- Keep the core math in NumPy; use no equivalent estimator for the implementation itself.
- Check shapes, dtypes, empty inputs, constant features, and numerical extremes.
- Compare predictions or objective values with a trusted library on small, controlled data.
- Record time and memory growth where the algorithm's complexity matters.
- Separate a bug in my code from a limitation of the method.

## First comparisons

| Implementation | Reference check |
|---|---|
| Linear regression | scikit-learn coefficients and predictions on a well-conditioned dataset |
| Logistic regression | decision scores, probabilities, and loss after convergence |
| Naive Bayes | class likelihoods on a tiny hand-counted example |
| KNN | neighbor indices and predictions with and without scaling |
| K-Means | inertia and cluster assignments across several initializations |
| Decision tree | chosen split and impurity reduction on a toy dataset |
| PCA | explained variance and reconstruction error |

## Completion evidence

- [ ] Derivation or algorithm sketch in my own words
- [ ] Implementation with shape and numerical checks
- [ ] Comparison against a trusted reference
- [ ] Complexity and known limitations noted
- [ ] Reproduction command and expected output documented
