# Machine Learning

> **Purpose:** Make a measured prediction for a defined use case. Model choice comes after the target, data split, baseline, and cost of errors are understood.

## Learning outcomes

- Translate a vague request into a prediction task and evaluation plan.
- Build honest baselines and compare models under one fixed protocol.
- Explain generalization, regularization, and the main supervised algorithms.
- Select metrics and thresholds from the actual error costs.
- Inspect calibration, subgroup errors, and failure cases.

## 1. Frame the task

Specify the prediction unit, target, prediction time, population, and action driven by the prediction. Decide whether the task is regression, binary or multiclass classification, ranking, clustering, or dimensionality reduction. Identify what errors cost and whether the prediction changes the process that creates future data.

Build a baseline before tuning: mean or median for regression, majority class, a simple rule, or a linear model. A complex model is only useful if it beats a relevant baseline under a trustworthy evaluation.

## 2. Supervised models

### Linear and logistic regression

Linear regression models a continuous response from a weighted sum of features. Learn least squares, residual analysis, assumptions, outlier sensitivity, and regularization. Logistic regression maps logits to class probabilities; interpret coefficients only with feature scale, encoding, and confounding in mind.

### Nearest neighbors and Naive Bayes

KNN predicts from nearby training examples. Distance scale, irrelevant features, dimensionality, and choice of k matter. Naive Bayes applies Bayes' rule with simplified conditional likelihood assumptions; it is fast and can be a strong text baseline.

### Decision trees and support vector machines

Decision trees split feature space by impurity reduction and capture nonlinear interactions but can overfit. SVMs maximize a margin; kernels extend the boundary but make scale and hyperparameter choices important. Understand support vectors and the cost parameter rather than treating the estimator as a black box.

## 3. Unsupervised learning

K-Means minimizes within-cluster squared distance and is sensitive to scale, initialization, and non-spherical clusters. DBSCAN groups dense regions and marks some points as noise, with behavior shaped by distance and density settings. PCA compresses correlated features into orthogonal directions of variance; it is not a supervised feature selector.

Clustering labels have no inherent ground-truth meaning. Evaluate stability, domain usefulness, and sensitivity to distance and preprocessing rather than declaring one score to prove the clusters are real.

## 4. Generalization and evaluation

Separate training, validation, and test roles. Cross-validation estimates performance across folds; the split scheme must match temporal and group structure. Use pipelines so preprocessing is refit independently in each fold.

Understand underfitting, overfitting, bias-variance intuition, learning curves, and regularization. Watch for leakage in feature construction, duplicate entities, and iterative validation reuse. Record the protocol before running candidates.

## 5. Metrics, thresholds, and calibration

For regression, know MAE, MSE/RMSE, and R-squared; each has a different interpretation and sensitivity to outliers. For classification, know confusion matrix, precision, recall, F1, ROC-AUC, and PR-AUC. Accuracy can be misleading when classes are imbalanced.

Ranking metrics assess ordering; calibration assesses whether predicted probabilities match observed frequencies. A model can rank well but be poorly calibrated. Select a decision threshold using validation data and the cost of false positives and false negatives. State whether a metric is micro, macro, or weighted for multiclass tasks.

## 6. Baseline-to-model workflow

1. Write the task and split contract.
2. Inspect labels, prevalence, and leakage risks.
3. Establish a simple baseline.
4. Fit preprocessing and model in one pipeline.
5. Choose a metric and validation design before comparing candidates.
6. Tune on validation data, then lock choices.
7. Evaluate once on the final holdout.
8. Inspect subgroup metrics and representative errors.
9. Record limitations and reproduction details.

## Practical project: a defensible comparison

Choose one public dataset, define a use case, and compare a simple baseline, linear model, and one nonlinear estimator. Keep the split fixed. Report metric definitions, confidence or variability across folds when appropriate, training cost, and the errors each model makes. Do not claim causality from predictive importance.

## Questions to answer

- Why can accuracy improve while the model becomes less useful?
- What does cross-validation estimate, and what does it not guarantee?
- Why must scaling occur inside a pipeline?
- What does changing a decision threshold do to precision and recall?
- Why is feature importance not a causal effect?
- When would a time split be more honest than shuffled cross-validation?

## Completion evidence

- [ ] A written problem and split definition precedes modeling.
- [ ] Every candidate is compared to a baseline on the same protocol.
- [ ] Metric and threshold choices match the decision costs.
- [ ] I inspected subgroup behavior and meaningful failure cases.
- [ ] The final score comes from a holdout not used for tuning.

## References

- [An Introduction to Statistical Learning (Python edition)](https://www.statlearning.com/)
- [scikit-learn User Guide](https://scikit-learn.org/stable/user_guide.html)
- [Stanford CS229 notes](https://cs229.stanford.edu/)
