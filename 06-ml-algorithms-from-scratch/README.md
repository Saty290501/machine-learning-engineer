# ML Algorithms from Scratch

I use small implementations to expose the mechanics hidden behind a library call. The goal is not to replace scikit-learn; it is to understand assumptions, shapes, numerical choices, complexity, and failure cases well enough to use trusted libraries responsibly.

## Implementation contract

- Keep the core implementation in NumPy; do not call an equivalent estimator inside it.
- State the input and output shapes, dtypes, and accepted edge cases.
- Separate fit-time state from prediction-time behavior.
- Add deterministic toy cases with hand-computable results.
- Compare against a trusted implementation on controlled data.
- Record time and memory growth when complexity matters.

## 1. Linear regression

Given X with N examples and D features, minimize mean squared error. Implement the closed-form least-squares solution using a stable least-squares solver, then batch gradient descent. Compare objective curves and predictions, not only coefficients; correlated features can make coefficients unstable while predictions remain similar.

Check intercept handling, constant columns, rank deficiency, feature scaling, convergence tolerance, and residual shape. A direct matrix inverse is a useful object lesson in what not to rely on for ill-conditioned data.

## 2. Logistic regression

Implement logits, a stable sigmoid, binary cross-entropy from logits, and gradient descent. Extend to multiclass softmax only after checking row-wise normalization and stable log-sum-exp. Test class imbalance, perfectly separable data, zero features, large logits, and a one-example batch.

Report probabilities and decisions separately. A threshold is not part of the learned probability model unless explicitly specified.

## 3. Naive Bayes

For Gaussian Naive Bayes, estimate per-class means and variances; for Multinomial Naive Bayes, estimate smoothed token counts. Derive log posterior scores and normalize only when actual probabilities are needed. Test unseen categories/tokens, zero counts, tiny classes, and features with zero variance. State the conditional independence assumption and compare scores with a library on a small dataset.

## 4. K-nearest neighbors

Implement distance computation, neighbor selection, and classification/regression aggregation. Compare Euclidean and Manhattan distances; feature scale changes neighborhoods. Test ties, k larger than training size, duplicates, zero-distance points, and deterministic tie-breaking. Discuss training memory O(ND) and naïve query distance O(ND), plus the limits of tree indexes in high dimensions.

## 5. K-Means

Implement initialization, assignment, centroid update, stopping criteria, and inertia. Handle an empty cluster explicitly. Run multiple initializations and show the spread in objective. Test identical points, fewer distinct points than k, and differently scaled features. Explain why inertia always favors more clusters and is not by itself proof of meaningful groups.

## 6. Decision tree split

For a candidate classification split, calculate parent impurity and weighted child impurity. Implement Gini and entropy, select the best threshold, and recurse with depth and leaf-size limits. Test a hand-crafted dataset with a known best split, constant features, ties, and pure nodes. Discuss greedy local choice and overfitting.

## 7. PCA

Center training data, compute components with SVD, project, and reconstruct. Compare the explained variance to a covariance eigendecomposition on a small, well-conditioned matrix. Test rank-deficient and constant data. Keep centering parameters from training and apply them unchanged to new samples. Explain sign ambiguity in singular vectors and why component signs do not change the subspace.

## 8. Verification protocol

For every algorithm:
1. Write the objective or algorithm in math and annotate dimensions.
2. Implement the smallest correct version with clear names.
3. Test hand-computable and edge cases.
4. Check gradients numerically if optimization is involved.
5. Compare predictions, objective, or components against a reference library.
6. Investigate disagreements before loosening tolerances.
7. Measure runtime as input size grows; do not infer complexity from one timing.
8. Document limitations and the reproduction command.

## Interview-style practice

Be able to derive linear regression and logistic regression gradients, vectorize pairwise KNN distances, explain K-Means empty clusters, compute a tree impurity reduction by hand, and describe numerical stability issues. For each, state shapes before code, complexity, edge cases, and a way to verify correctness.

## Completion evidence

- [ ] Each implementation has a derivation or algorithm sketch.
- [ ] Shape, dtype, edge-case, and finite-value checks are present.
- [ ] A trusted reference comparison passes for controlled examples.
- [ ] Complexity and known limitations are documented.
- [ ] Results can be reproduced from a clean checkout.

## References

- [NumPy documentation](https://numpy.org/doc/stable/user/)
- [scikit-learn estimator documentation](https://scikit-learn.org/stable/user_guide.html)
- [Reference interview guide that inspired the verification depth](https://github.com/jyotipmahes/ML-Interview-Prep/blob/main/MLE_Coding_Interview_Guide.ipynb)
