# Machine Learning Engineer

**A focused, evidence-led path from Python and data foundations to classical ML, algorithms from scratch, and NLP.**

I’m building this repository as a working study record. Each section is meant to help me explain the idea, implement or apply it, evaluate it honestly, and show what I learned. The scope is intentionally limited to the seven sections below; other areas can live in separate repositories later.

## Learning path

| # | Section | What the guide covers |
|---|---|---|
| 00 | [Roadmap](00-roadmap/README.md) | Prerequisites, study sequence, milestones, and evidence of progress |
| 01 | [Python for ML](01-python-for-ml/README.md) | Core Python, complexity, NumPy shapes, pandas, visualization, tests, reproducibility |
| 02 | [Mathematics for ML](02-mathematics-for-ml/README.md) | Linear algebra, gradients, probability, statistics, optimization, numerical stability |
| 03 | [Data Analysis & Engineering](03-data-analysis-engineering/README.md) | Data contracts, profiling, SQL, leakage, feature pipelines, honest splits |
| 04 | [Machine Learning](04-machine-learning/README.md) | Problem framing, baselines, core models, generalization, metrics, evaluation |
| 05 | [Advanced Machine Learning](05-advanced-machine-learning/README.md) | Ensembles, tuning, imbalance, calibration, interpretation, robustness, drift |
| 06 | [Algorithms from Scratch](06-ml-algorithms-from-scratch/README.md) | NumPy implementations, derivations, numerical checks, complexity, reference comparisons |
| 07 | [Natural Language Processing](07-natural-language-processing/README.md) | Text inspection, TF-IDF, tokenization, transformers, evaluation, error analysis |

## How I study each topic

For every substantial topic, I try to leave a trail another person can follow:

1. **Question and assumptions:** What problem is being solved? What must be true of the data?
2. **Explanation:** What is the central idea, in my own words?
3. **Working evidence:** A derivation, small implementation, experiment, or analysis.
4. **Checks:** Tests, baselines, leakage checks, numerical checks, or reference comparisons.
5. **Reflection:** What failed, what trade-off appeared, and what I would investigate next.

A score without a split definition, metric meaning, and comparison baseline is not enough. A from-scratch implementation without edge-case checks is not enough either.

## Repository principles

- Start with a simple baseline and define the evaluation protocol before tuning.
- Fit preprocessing only on training folds; keep final test data out of model selection.
- Write down dimensions and data assumptions before implementing equations.
- Choose metrics from the errors that matter in the intended use.
- Compare educational implementations with trusted libraries on controlled examples.
- Keep claims proportional to the code and evidence actually present here.

## Resources

The [reading shelf](resources/README.md) links books, courses, documentation, and papers aligned to this scope. The [book plan](resources/books.md) suggests an order and explains what I want each book to help me answer.

## Connect

- GitHub: [@Saty290501](https://github.com/Saty290501)
- Portfolio: [satyenchaudhari.github.io](https://satyenchaudhari.github.io)
