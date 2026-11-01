# Machine Learning Engineer

**A focused route from useful Python to careful machine learning and NLP.**

I’m building this repository as a working study record: each topic should leave me with something I can explain, implement, evaluate, and improve. It is deliberately limited to seven sections. The rest of my learning areas can live in separate repositories when I am ready to build them properly.

> **Status:** In progress  
> **Approach:** Learn the idea → make a small implementation → test it → write down what I learned

## The seven sections

| Section | What I want to get good at |
|---|---|
| [00 · Roadmap](00-roadmap/README.md) | A clear sequence and evidence for progress |
| [01 · Python for ML](01-python-for-ml/README.md) | Readable Python, NumPy, pandas, testing, and packaging |
| [02 · Mathematics for ML](02-mathematics-for-ml/README.md) | The linear algebra, calculus, probability, and optimization behind models |
| [03 · Data Analysis & Engineering](03-data-analysis-engineering/README.md) | Turning raw data into trustworthy, leakage-safe datasets |
| [04 · Machine Learning](04-machine-learning/README.md) | Framing problems, choosing baselines, and evaluating models honestly |
| [05 · Advanced Machine Learning](05-advanced-machine-learning/README.md) | Ensembles, tuning, interpretation, imbalance, and robustness |
| [06 · Algorithms from Scratch](06-ml-algorithms-from-scratch/README.md) | Making the mechanics visible with small NumPy implementations |
| [07 · Natural Language Processing](07-natural-language-processing/README.md) | Moving from text features to modern NLP models and error analysis |

## How I work through a topic

I start with a question the model is supposed to answer. Then I write down the data assumptions, build the simplest baseline that could work, and choose a metric that matches the cost of being wrong. Only after that do I add complexity.

For each substantial topic, I aim to keep four pieces of evidence together:

1. A short explanation in my own words.
2. A reproducible implementation or experiment.
3. Tests or checks for edge cases and data leakage.
4. Results, limitations, and the next question I would investigate.

## Repository map

```text
machine-learning-engineer/
├── 00-roadmap/
├── 01-python-for-ml/
├── 02-mathematics-for-ml/
├── 03-data-analysis-engineering/
├── 04-machine-learning/
├── 05-advanced-machine-learning/
├── 06-ml-algorithms-from-scratch/
├── 07-natural-language-processing/
├── resources/
├── tests/
└── .github/
```

## Reading shelf

The [resource notes](resources/README.md) are curated around this exact scope. The [book plan](resources/books.md) gives my preferred order, which chapters I intend to focus on, and what I want each book to help me answer.

## Principles I want the work to show

- Start with a baseline and keep the test set untouched until the end.
- Treat data quality and leakage checks as part of modeling.
- Explain why a metric fits the problem; do not report a score without context.
- Compare a hand-built algorithm with a trusted implementation on controlled cases.
- Keep claims proportional to the code and evidence actually in the repository.

## Connect

- GitHub: [@Saty290501](https://github.com/Saty290501)
- Portfolio: [satyenchaudhari.github.io](https://satyenchaudhari.github.io)
