# Learning roadmap

A small, evidence-led path through the seven sections in this repository. I want each step to make the next one easier, not to collect a long list of topics.

## Sequence

| Step | Focus | Evidence I want to leave behind |
|---|---|---|
| 1 | Python for ML | Reusable functions, data transformations, tests, and a reproducible environment |
| 2 | Mathematics for ML | Derivations and visual explanations tied to model behavior |
| 3 | Data analysis & engineering | A data profile, explicit assumptions, and a leakage review |
| 4 | Machine learning | A baseline-to-candidate comparison with a fixed evaluation protocol |
| 5 | Advanced machine learning | A justified ensemble or tuning experiment plus error and subgroup analysis |
| 6 | Algorithms from scratch | Small NumPy implementations checked against trusted libraries |
| 7 | Natural language processing | A classical text baseline, a stronger model, and an honest error review |

## My weekly loop

1. Choose one question narrow enough to answer in a few focused sessions.
2. Read the relevant chapter or documentation and summarize the idea without copying its wording.
3. Build the smallest experiment that can test the idea.
4. Record the baseline before changing the model.
5. Inspect errors and edge cases, then write down what surprised me.
6. Commit the result with reproduction steps.

## Completion evidence

I mark a topic complete only when someone else can see:

- what problem I was trying to solve;
- what data and assumptions I used;
- how to reproduce the result;
- how I checked correctness and leakage;
- what the metric says, and what it does not say;
- which limitations remain.

A notebook that ran once is a useful start, not completion.
