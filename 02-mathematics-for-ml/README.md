# Mathematics for Machine Learning

> **Purpose:** Connect equations to model behavior. I want to know what each object means, which assumptions a formula makes, and how finite precision affects the computation.

## Learning outcomes

- Read dimensions in a formula and map them to code.
- Derive gradients for common losses instead of memorizing them.
- Use probability and statistics to reason about uncertainty and evaluation.
- Explain why optimization converges, stalls, or becomes unstable.
- Recognize when conditioning makes a valid method unreliable.

## 1. Linear algebra

Treat each feature row as a point in R^D. A dot product measures alignment; a norm measures magnitude. Matrix multiplication composes linear maps. If X is N by D and w is D, Xw is one prediction per row. Write dimensions before transposing or broadcasting.

Study rank, column and null spaces, orthogonality, projections, and least squares geometry. Collinear columns mean coefficients may not be unique even when predictions are. The L1 norm can create sparse coefficients; L2 shrinks them smoothly. Scaling matters because penalties act on coefficient magnitudes.

For singular value decomposition, X = U Sigma V-transpose. It exposes rank and dominant directions, including for rectangular matrices. PCA finds high-variance directions in centered data. Scaling changes the geometry, while high retained variance does not guarantee target relevance. Compare covariance eigendecomposition with SVD.

## 2. Calculus and gradients

Study derivatives, partial derivatives, gradients, Jacobians, and the chain rule. The gradient points toward greatest local increase; gradient descent steps against it.

For mean squared error, J(w) = (1 / 2N) ||Xw - y|| squared, and gradient = X-transpose (Xw - y) / N. Derive this from the residual and matrix differential; the one-half cancels the derivative's factor of two.

For logistic regression, let z = Xw + b, p = sigmoid(z), and use binary cross-entropy. Derive gradient = X-transpose (p-y) / N. Use logits or a stable log-sum-exp expression rather than logging probabilities rounded to zero. Verify each analytic gradient against central finite differences on a tiny dataset.

## 3. Probability

Know conditional probability, independence, Bayes' rule, and base rates. A strong likelihood ratio does not guarantee a high posterior when the event is rare. This matters in fraud and screening problems.

Understand expectation, variance, covariance, Bernoulli, binomial, Gaussian, categorical, and multinomial distributions. Distinguish population from sample. Independence is stronger than zero correlation except under additional assumptions. Naive Bayes makes a conditional independence assumption; classification can still work when the assumption is imperfect.

Learn sampling variation, standard errors, bootstrap intuition, and confidence intervals. Separate statistical uncertainty from data-quality uncertainty. Do not interpret a computed confidence interval as a probability about a fixed parameter.

## 4. Statistics and inference

Study estimators, bias, variance, consistency, likelihood, maximum likelihood, and regularization as a preference for certain solutions. Distinguish predictive association from causal effect; confounding means an observed relationship can change when other variables are considered.

Repeated tuning against one validation set adapts to that set. A test set used repeatedly is no longer an untouched final check. Report sample size and uncertainty when differences are small. Consider subgroup performance and the data-generating process, not just a global average.

## 5. Optimization

For parameters theta, gradient descent updates theta by subtracting learning rate times the gradient. A small rate progresses slowly; a large rate can overshoot or diverge. Batch, stochastic, and mini-batch methods trade gradient noise against computation and memory.

Study momentum and Adam as update rules with state and hyperparameters. They do not remove the need to scale inputs, inspect loss curves, or define stopping criteria. Convexity means no suboptimal local minima but does not guarantee good conditioning. The Hessian describes local curvature; very different curvature across directions causes slow zig-zagging.

## 6. Numerical computing

Floating point has limited precision. Study round-off, cancellation, overflow, underflow, conditioning, and stable summation. A stable sigmoid branches on the sign of its input. Stable log-sum-exp subtracts the maximum before exponentiation. Do not add arbitrary epsilon everywhere; identify which quantity may be zero and how adjustment changes the objective.

Check losses, gradients, probabilities, and parameters for finite values. Use double precision when validating a lower-precision path. Compare a numerically unstable formula with a stable equivalent at extreme inputs.

## Derivation and experiment sequence

1. Derive linear regression gradient on paper and annotate every shape.
2. Implement the loss and gradient with matrix operations.
3. Compare analytic gradient with central differences: [J(w+h e_i)-J(w-h e_i)]/(2h).
4. Plot loss under several learning rates on a synthetic problem.
5. Show how duplicated features affect least squares and regularization.
6. Reproduce PCA with SVD and covariance eigenvectors; compare subspaces.

## Questions to answer

- Why can X-transpose-X be singular, and why may QR/SVD least squares be more stable?
- What changes when features are standardized before L1 or L2 regularization?
- How can a model be calibrated but have weak ranking performance?
- Why might a gradient have the wrong shape and still execute?
- How do sampling uncertainty and distribution shift differ?

## Completion evidence

- [ ] I annotate dimensions in derivations and matching code.
- [ ] I verified two gradients numerically.
- [ ] I explain one assumption behind each distribution or estimator used.
- [ ] I demonstrated an optimization failure by changing scale or learning rate.
- [ ] I identify numerical risks before they create silent metric errors.

## References

- [Mathematics for Machine Learning](https://mml-book.github.io/)
- [MIT 18.06 Linear Algebra](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/)
- [An Introduction to Statistical Learning](https://www.statlearning.com/)
