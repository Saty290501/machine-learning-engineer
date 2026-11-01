# Detailed Learning Sequence

A topic is complete here when it has both an explanation and evidence. Reading is the input; the artifact is what makes the learning inspectable.

## Stage 1 — Python for ML

**Study:** Python functions and data structures, complexity, NumPy arrays and broadcasting, pandas joins and grouping, visualization, testing, environments.

**Build:** A reusable dataset profiling tool and a tested vectorized transformation.

**Check:** Compare a small loop and vectorized version; include empty data, missing values, duplicates, and shape assertions.

## Stage 2 — Mathematics for ML

**Study:** Vectors and projections, matrix factorization, derivatives and chain rule, probability, estimation, convexity, gradient descent, floating-point stability.

**Build:** Linear regression and logistic regression loss/gradient notebooks with a finite-difference check.

**Check:** Change feature scale, learning rate, and collinearity; explain how each changes convergence or identifiability.

## Stage 3 — Data Analysis & Engineering

**Study:** Data contracts, schema validation, missingness, duplicate keys, SQL joins and windows, time-aware features, leakage, split design, pipeline fitting.

**Build:** A data audit and train/validation/test pipeline for one public dataset.

**Check:** Prove entity and temporal separation where required; verify every learned transform is fitted only on training folds.

## Stage 4 — Machine Learning

**Study:** Problem framing, baselines, linear models, nearest neighbors, Naive Bayes, trees, SVM, clustering, cross-validation, metrics, calibration.

**Build:** One controlled comparison from a simple baseline to a nonlinear model.

**Check:** Keep the split fixed; state metric and threshold rationale; inspect per-class and subgroup errors; reserve a final holdout.

## Stage 5 — Advanced Machine Learning

**Study:** Bagging and boosting, stacking, search strategies, imbalance, threshold decisions, calibration, attribution, robustness, drift.

**Build:** Improve a baseline with one justified change at a time, then write a model card.

**Check:** Use out-of-fold predictions for stacking, resample within training folds, and show variability and limitations.

## Stage 6 — Algorithms from Scratch

**Study:** Linear and logistic regression, Naive Bayes, KNN, K-Means, decision tree splits, PCA.

**Build:** Small NumPy implementations, each with an algorithm sketch, tests, and reference comparison.

**Check:** Test shapes and edge cases; verify gradients; measure complexity growth; explain where the educational implementation is intentionally limited.

## Stage 7 — Natural Language Processing

**Study:** Unicode and tokenization, lexical features, TF-IDF, text baselines, embeddings, transformer encoders, task metrics, error analysis.

**Build:** A TF-IDF baseline and a pretrained encoder comparison on the same public dataset and fixed split.

**Check:** Track vocabulary leakage, truncation, label quality, author/source overlap, per-class results, privacy, and compute.

## Deliverable template

For each project, write:

- **Question:** What prediction or analysis am I trying to make?
- **Data:** Where did it come from, what does each row mean, and what are its limits?
- **Method:** What baseline and candidate did I compare?
- **Evaluation:** Which split, metric, and threshold did I use, and why?
- **Checks:** What tests, leakage audits, or reference comparisons did I run?
- **Result:** What happened, including uncertainty or variation?
- **Failure:** Which examples or slices still fail?
- **Next:** What experiment would most reduce uncertainty?

## Completion is evidence-based

A checked box should point to a notebook, code path, report, or dated note. If the artifact is missing, the topic is still in progress. This keeps the roadmap honest and makes the repository useful to someone reviewing it.
