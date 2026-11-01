# Advanced Machine Learning

> **Purpose:** Improve a model without fooling myself about the evidence. More tuning, more features, and more elaborate ensembles each create new ways to overfit or misread results.

## Learning outcomes

- Explain bagging, boosting, stacking, and the assumptions behind them.
- Tune models with a compute budget and an untouched evaluation set.
- Diagnose imbalance, threshold, calibration, and subgroup issues.
- Interpret model behavior with methods that match the question.
- Test robustness, uncertainty, and temporal stability.

## 1. Ensembles

### Bagging and random forests

Bagging fits models on resampled data and averages predictions to reduce variance. Random forests also randomize feature consideration at splits to decorrelate trees. Study bootstrap samples, out-of-bag estimates, depth, leaf size, feature subsampling, and class weighting. Feature importance can be biased toward high-cardinality or correlated variables.

### Boosting

Boosting adds learners sequentially to correct residual errors or optimize a differentiable objective. Compare gradient boosting with XGBoost, LightGBM, and CatBoost through their objectives, regularization, sampling, missing-value behavior, and categorical handling. Understand learning rate, number of trees, depth or leaves, minimum child constraints, and early stopping.

Early stopping is model selection. Its validation set must not be reused as a final test. Compare training and validation curves and check whether gains persist across folds or time periods.

### Stacking and blending

Stacking trains a meta-model on out-of-fold predictions from base learners. If the meta-model sees in-sample base predictions, leakage can make the ensemble appear much stronger than it is. Blending uses a holdout to combine predictions and spends some data for that purpose. State the data flow explicitly.

## 2. Hyperparameter search

Start with a baseline and a short hypothesis about which parameters matter. Random search often explores broad spaces more efficiently than a dense grid. Bayesian optimization can prioritize promising trials but adds assumptions and overhead. Use sensible ranges, fixed validation design, and a compute budget.

Track parameters, code version, data version, fold scores, runtime, and failures. Tune only on training/validation folds. Repeatedly choosing among many candidates increases selection bias. Prefer a stable, simpler model when a tiny score gain does not survive resampling.

## 3. Imbalanced classification and decisions

Inspect prevalence by split, time, and subgroup. Compare class weights, resampling, and threshold tuning; resampling must happen within each training fold. Never balance validation or test data if deployment prevalence is naturally imbalanced.

Use PR curves when positive-class retrieval matters, while remembering PR-AUC changes with prevalence. Choose thresholds from the operational cost, capacity, and review budget. Report confusion matrices at the selected threshold and examine how many examples would trigger action.

## 4. Calibration and uncertainty

Calibration asks whether predictions assigned probability p occur approximately p fraction of the time. Inspect reliability diagrams and Brier or log loss; distinguish ranking from probability quality. Platt scaling and isotonic regression are learned transformations and must use validation data or cross-fitting.

Uncertainty estimates may reflect model uncertainty, sample variability, or label ambiguity. Ensembles and bootstrap approaches can reveal instability but do not automatically cover distribution shift. State the population and assumptions under which an uncertainty interval is meaningful.

## 5. Interpretation and feature diagnostics

Permutation importance measures score change after disrupting a feature, but correlated features can substitute for one another. Partial dependence averages predictions over feature values and can create unrealistic combinations when features are dependent. Individual conditional expectation shows per-example curves but can still extrapolate.

SHAP values allocate a prediction difference relative to a background distribution under a specific attribution framework. Explain the background choice and what the values do not mean. None of these methods establishes causal effect. Always pair global summaries with local examples and data checks.

## 6. Robustness, fairness, and drift

Evaluate by meaningful slices: time, geography, acquisition channel, class, and groups relevant to use. Check both sample size and uncertainty; tiny slices have noisy estimates. Test missing features, plausible perturbations, category shifts, and threshold sensitivity.

Monitor input distributions, missingness, prediction distributions, delayed labels, calibration, and outcome metrics. Input drift does not prove performance degraded; performance drift requires labels or a justified proxy. Document who is represented, who is missing, and how the model can fail.

## Project: controlled model improvement

Use a fixed split to compare a linear baseline, random forest, and boosted trees. Then add one change at a time: class weighting, threshold selection, calibration, or interpretation. Record validation selection, final holdout result, variability, runtime, and a failure slice. The result should show what improved and what trade-off came with it.

## Common traps

- Tuning the test set through repeated informal experiments.
- Oversampling before cross-validation.
- Building stacking features from in-sample predictions.
- Treating a feature attribution as a causal explanation.
- Optimizing one aggregate score while a subgroup collapses.
- Reporting input drift as proof that accuracy has changed.
- Keeping a large ensemble for an unstable marginal gain.

## Completion evidence

- [ ] The search has a budget and a recorded selection protocol.
- [ ] Resampling and calibration happen inside valid folds.
- [ ] Thresholds are chosen from decision costs, not convention.
- [ ] Attributions are explained with their assumptions.
- [ ] Robustness and subgroup results include sample sizes and limits.

## References

- [The Elements of Statistical Learning](https://hastie.su.domains/ElemStatLearn/)
- [scikit-learn model evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html)
- [XGBoost documentation](https://xgboost.readthedocs.io/)
- [SHAP documentation](https://shap.readthedocs.io/)
