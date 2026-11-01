# Natural Language Processing

I want to understand the text before reaching for a large model. This section moves from inspectable lexical baselines to contextual encoders, keeping tokenization, evaluation, and error analysis visible throughout.

## Learning outcomes

- Inspect text and labels before normalizing or tokenizing.
- Build a reproducible TF-IDF baseline and explain its limits.
- Understand tokenization, embeddings, attention, and encoder fine-tuning.
- Evaluate per class and analyze errors by language and text properties.
- Describe data, compute, and privacy limitations of a text model.

## 1. Define the task and inspect examples

State the unit (document, sentence, token, or pair), target, prediction setting, and action. Inspect examples from every label, including ambiguous and unusually short or long text. Check duplicate texts, label conflicts, class prevalence, language variety, and whether documents from one author or source cross splits.

Create a label guide with inclusion rules and edge cases. If humans disagree, measure or discuss that ambiguity instead of pretending the label is perfectly objective.

## 2. Unicode, normalization, and tokenization

Text is Unicode, not merely ASCII characters. Learn normalization forms, code points, combining marks, case folding, punctuation, whitespace, and language-specific segmentation. A tokenizer's choices define the units a model sees.

Normalization can erase signal: casing, diacritics, punctuation, emoji, repeated letters, and word boundaries may matter for sentiment, names, or multilingual text. Compare alternatives on examples and holdout results rather than applying a universal cleanup recipe. Fit any learned vocabulary on training data only.

## 3. Sparse lexical baselines

Bag of Words represents token counts; n-grams preserve limited local order; TF-IDF downweights terms common across documents. Build a sparse matrix and fit logistic regression or Multinomial Naive Bayes. This baseline is fast, interpretable, and often difficult to beat on small task-specific datasets.

Control vocabulary size, minimum document frequency, token pattern, n-gram range, and class weighting. Put vectorization inside the training pipeline to prevent vocabulary leakage. Inspect high-weight terms cautiously: correlation is not a causal explanation and can reveal source or annotation artifacts.

## 4. Embeddings and contextual representations

Static word embeddings map a token to one vector regardless of context; this is compact but conflates different senses. Contextual encoders produce token representations conditioned on surrounding text. Learn the conceptual role of positional information, attention, and transformer encoder layers without treating hidden vectors as human-readable definitions.

Compare frozen embeddings, feature extraction, and fine-tuning. Fine-tuning can overfit small data and is sensitive to learning rate, batch size, sequence length, and random seed. Record model checkpoint, tokenizer, truncation and padding rules, and training configuration.

## 5. Transformer fine-tuning workflow

1. Establish a lexical baseline and fixed split.
2. Select a pretrained encoder appropriate to language and license.
3. Tokenize with the matching tokenizer and inspect truncation rates.
4. Fine-tune only on training data; select settings on validation data.
5. Choose threshold and calibration using validation predictions.
6. Evaluate once on held-out data.
7. Save the model, tokenizer, label mapping, configuration, and preprocessing.
8. Compare quality, latency, memory, and failure examples against the baseline.

Do not compare models on different examples or with a changed label mapping. Account for sequence length: attention cost grows roughly quadratically with token count in the standard implementation.

## 6. Tasks and evaluation

For classification, report precision, recall, F1, and confusion matrix; specify macro, micro, or weighted averaging. For imbalanced labels, include per-class support and PR behavior. For named-entity recognition, define exact or partial span matching and report entity-level metrics. For text similarity, define the annotation and evaluation unit.

Accuracy alone hides rare-class failures. Inspect performance by language, length, source, time, and relevant demographic or dialect groups where appropriate. Keep subgroup sample sizes visible.

## 7. Error analysis

Create an error table with text, gold label, prediction, confidence, length, language/source, and an error category. Group errors into actionable patterns: ambiguity, negation, domain vocabulary, truncation, spelling variation, label noise, or source shift. Select the next experiment from a pattern that can be tested.

Review both false positives and false negatives. High-confidence mistakes deserve attention, but do not cherry-pick examples to tell a flattering story. Remove or mask personal information in examples before publishing.

## Project: baseline-to-encoder comparison

Use a public, licensed dataset. Document the label guide, split strategy, TF-IDF baseline, encoder and tokenizer versions, metrics, training cost, and representative errors. Keep the split fixed and report what the stronger model still gets wrong. Include instructions that run on CPU where practical.

## Common failure modes

- Stripping punctuation, case, emoji, or diacritics without checking their meaning.
- Splitting documents from the same author across train and test.
- Fitting vocabulary before the split.
- Ignoring truncation and tokenizer mismatch.
- Reporting aggregate accuracy while a class or language fails.
- Treating attention weights or token importance as a causal explanation.
- Publishing private text or personally identifying examples.

## Completion evidence

- [ ] A lexical baseline is reproducible and evaluated fairly.
- [ ] Tokenization and preprocessing decisions have evidence.
- [ ] Stronger model comparison uses the same split and label map.
- [ ] Per-class metrics and representative errors are documented.
- [ ] Data rights, privacy, model limits, and compute are described.

## References

- [NLTK Book](https://www.nltk.org/book/)
- [Speech and Language Processing, 3rd edition draft](https://web.stanford.edu/~jurafsky/slp3/)
- [Stanford CS224N](https://web.stanford.edu/class/cs224n/)
- [Natural Language Processing with Transformers](https://www.oreilly.com/library/view/natural-language-processing/9781098136796/)
- [Hugging Face course](https://huggingface.co/learn/nlp-course/)
