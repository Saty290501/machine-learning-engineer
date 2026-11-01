# Papers worth reading beside the code

I read a paper to answer a concrete question, not to collect citations. For each one, I want to write down the problem, the key assumption, the evidence, and one limitation that matters for my use case.

| Paper | Why it belongs on this shelf | First question I want to ask |
|---|---|---|
| Pedro Domingos, [“A Few Useful Things to Know About Machine Learning”](https://doi.org/10.1145/2347736.2347755), 2012 | A concise set of lessons about data, generalization, feature design, and evaluation. | Which of these lessons would have changed my last experiment? |
| Leo Breiman, [“Random Forests”](https://doi.org/10.1023/A:1010933404324), 2001 | A primary reference for the intuition behind random forests and the role of randomized trees. | What does decorrelation among trees buy me, and what does it not fix? |
| Jerome H. Friedman, [“Greedy Function Approximation: A Gradient Boosting Machine”](https://doi.org/10.1214/aos/1013203451), 2001 | A foundational account of gradient boosting as a stage-wise optimization procedure. | What quantity is each new weak learner trying to improve? |
| Ashish Vaswani et al., [“Attention Is All You Need”](https://proceedings.neurips.cc/paper/7181-attention-is-all-you-need), 2017 | The original Transformer paper, useful context for the architecture behind current NLP models. | Which parts of the architecture are essential for the task I am studying? |
| Jacob Devlin et al., [“BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding”](https://arxiv.org/abs/1810.04805), 2018 | A clear reference for pretrained contextual representations and task-specific fine-tuning. | What changes when I start with a pretrained encoder instead of sparse text features? |

A paper note is not complete until I can explain its central idea without repeating its abstract.
