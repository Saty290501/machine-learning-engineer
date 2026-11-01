# Learning Roadmap

This roadmap turns the repository into a sequence of study and evidence. The goal is not to tick every box quickly; it is to build enough understanding that I can explain a decision and reproduce the result.

## Before I start

Set up Python, Git, an isolated environment, Jupyter, NumPy, pandas, Matplotlib, and pytest. Create a small project with a README and a command that reproduces one result. Keep experiments in version control, but do not commit secrets or private datasets.

## The sequence

| Stage | Focus | Exit evidence |
|---|---|---|
| 1 | [Python for ML](../01-python-for-ml/README.md) | Tested data transformation and shape-aware NumPy exercise |
| 2 | [Mathematics for ML](../02-mathematics-for-ml/README.md) | Written gradient derivations, finite-difference check, optimization plot |
| 3 | [Data Analysis & Engineering](../03-data-analysis-engineering/README.md) | Data contract, profiling report, leakage-safe split and pipeline |
| 4 | [Machine Learning](../04-machine-learning/README.md) | Baseline comparison with justified metric and final holdout |
| 5 | [Advanced Machine Learning](../05-advanced-machine-learning/README.md) | Controlled model improvement with calibration or subgroup analysis |
| 6 | [Algorithms from Scratch](../06-ml-algorithms-from-scratch/README.md) | Small NumPy implementation verified against a trusted library |
| 7 | [Natural Language Processing](../07-natural-language-processing/README.md) | TF-IDF baseline, encoder comparison, per-class errors |

The order is a default, not a gate. Linear algebra and Python practice can run alongside the first stages. Algorithms from scratch becomes more useful after the corresponding model has been studied conceptually.

## Milestones

### Milestone A — Reliable Python

I can work with arrays and tables, write clear functions, test edge cases, and reproduce an analysis from a clean environment.

### Milestone B — Mathematical fluency

I can explain the geometry and probability behind simple models, derive gradients, check them numerically, and recognize unstable calculations.

### Milestone C — Trustworthy data and evaluation

I can define the prediction point, target, and split; audit joins and leakage; and build preprocessing that is fit only on training data.

### Milestone D — Model judgment

I can compare a baseline with candidate models, explain why a metric fits, inspect errors, and avoid overclaiming from a single score.

### Milestone E — Depth and communication

I can make an implementation or experiment reproducible, compare it to a reference, explain failure cases, and write concise technical notes.

## Weekly study loop

1. Pick one narrow question from a section.
2. Read a primary source or textbook chapter.
3. Reproduce one derivation, example, or small experiment.
4. Change an assumption and observe what breaks.
5. Write the result, checks, limitations, and next step in my own words.

A good weekly artifact is small enough to finish and complete enough that I can rerun it later.

## Final project standard

Every substantial project should state:

- The task, prediction unit, target, and intended population.
- Data provenance, license, schema, and cleaning decisions.
- Split design and why it reflects the use case.
- Baseline, metric definitions, and model selection protocol.
- Reproduction instructions, environment, and random seeds.
- Error analysis, subgroup limits, compute cost, and known failure modes.

## Progress log

Use dated entries with links to work rather than claiming mastery from reading alone.

| Date | Topic | Artifact | What changed in my understanding | Next step |
|---|---|---|---|---|
| YYYY-MM-DD | Example: logistic regression | Link to notebook or code | One concrete observation | One follow-up experiment |

## Out of scope for this repository

This repository currently stays with the seven sections listed in the root README. Topics such as deep learning as a separate track, computer vision, generative AI, RAG, agents, system design, and MLOps can become separate repositories when I am ready to give them the same level of care.
