# Books I want to study

My shelf is deliberately short. I would rather work through one chapter, reproduce one idea, and write a useful note than keep adding titles I have not opened.

## The reading loop I want to follow

For each chapter I study, I will leave a four-line note:

1. **Question:** What problem is this chapter answering?
2. **Mechanism:** What assumption or mathematical idea makes the method work?
3. **Experiment:** What small implementation or dataset can make the idea visible?
4. **Limit:** What result would make me distrust the method here?

## Core path

| Order | Book | How I plan to use it |
|---|---|---|
| 1 | [Python for Data Analysis, 3rd ed. — Wes McKinney](https://www.oreilly.com/library/view/python-for-data/9781098104023/) | My hands-on reference for NumPy, pandas, joins, reshaping, grouping, time series, and plotting. I will focus on the parts that make a data workflow reproducible, not just a notebook that looks finished. |
| 2 | [Mathematics for Machine Learning — Deisenroth, Faisal & Ong](https://mml-book.github.io/) | A compact bridge from linear algebra, matrix decompositions, vector calculus, probability, and optimization to linear regression, PCA, and SVMs. The authors provide a free online edition. |
| 3 | [An Introduction to Statistical Learning with Applications in Python (ISLP)](https://www.statlearning.com/) | My main applied-statistics spine. I plan to work through regression, classification, resampling, regularization, nonlinear methods, trees, SVMs, and unsupervised learning labs. I will keep the labs and my own conclusions together. |
| 4 | [Hands-On Machine Learning, 3rd ed. — Aurélien Géron](https://www.oreilly.com/library/view/hands-on-machine-learning/9781098125967/) | A practical companion for turning a modeling idea into a clean experiment. For this repository I will use the early chapters on the ML landscape, an end-to-end project, classical models, ensembles, dimensionality reduction, and clustering; later material is outside this repo's current scope. |

## Choose one deeper reference when I need it

I do not need to read both books cover to cover. I will choose based on the question I have:

- [The Elements of Statistical Learning — Hastie, Tibshirani & Friedman](https://link.springer.com/book/10.1007/978-0-387-21606-5): a deeper statistical treatment of regularization, smoothing, trees, boosting, and model uncertainty. I will use it when I want to understand why a method behaves as it does.
- [Understanding Machine Learning: From Theory to Algorithms — Shalev-Shwartz & Ben-David](https://www.cambridge.org/core/books/understanding-machine-learning/3059695661405D25673058E43C8BE2A6): a more proof-oriented route into generalization, learning guarantees, and algorithmic ideas. I will open it when an empirical result raises a question about what can be guaranteed.

## NLP shelf

- [Speech and Language Processing, 3rd ed. draft — Jurafsky & Martin](https://web.stanford.edu/~jurafsky/slp3/): an unusually broad reference for language, tokenization, language models, and NLP tasks. This is an evolving manuscript; I will check the current table of contents and note the draft date when I cite it.
- [Natural Language Processing with Transformers, revised ed. — Tunstall, von Werra & Wolf](https://www.oreilly.com/library/view/natural-language-processing/9781098136789/): a practical guide to tokenization, classification, named-entity recognition, and transformer workflows. I will cross-check code against the live library documentation because software APIs move faster than books.

## My reading order in one line

**Wes McKinney → Mathematics for Machine Learning → ISLP → selected Hands-On ML chapters → one theory reference when needed → NLP foundations → a focused transformer implementation.**

Reading is only the start. The useful part is the small experiment and the note about what did not work.
