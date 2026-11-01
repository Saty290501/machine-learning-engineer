# Natural Language Processing

I want to understand the text before reaching for a large model. This section moves from inspectable features to contextual representations, with evaluation and error analysis at every step.

## Topics

- [ ] Text normalization, Unicode, tokenization, and the limits of language-independent preprocessing.
- [ ] Bag of Words, n-grams, sparse matrices, and TF-IDF.
- [ ] Naive Bayes and logistic-regression text baselines.
- [ ] Word and sentence representations: what they retain and what they blur.
- [ ] Transformer encoders, tokenization, and fine-tuning a pretrained model for a focused task.
- [ ] Classification and named-entity recognition metrics, including macro-F1 and per-label performance.
- [ ] Error analysis by class, text length, language variety, and ambiguous examples.

## Practical sequence

1. Inspect examples and label quality before preprocessing.
2. Build a TF-IDF baseline with a documented split and metric.
3. Read the errors; group them by a pattern that could change the next experiment.
4. Compare one stronger representation or pretrained model against that baseline.
5. Report performance, cost, and the cases that still fail.

## Guardrails I want to keep

- Do not normalize away information before checking whether it matters.
- Fit vocabulary and preprocessing only on the training split.
- Keep the comparison fair: same data split, metric, and evaluation examples.
- Use a model card or short note to describe data limits and likely failure modes.

## Completion evidence

- [ ] Reproducible text pipeline
- [ ] Baseline and stronger-model comparison
- [ ] Per-class results and representative error examples
- [ ] Tokenization and preprocessing choices explained
- [ ] Limitations stated without hiding behind one aggregate score
