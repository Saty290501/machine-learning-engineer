# Python for Machine Learning

> **Purpose:** Build Python fluency that makes data work correct, testable, and understandable before model complexity enters the picture.

This is a practical study guide, not a syntax checklist. For each topic, I want to explain the trade-off, make a small implementation, and show how I know it behaves correctly.

## Learning outcomes

- Write small functions with clear inputs, outputs, types, and failure behavior.
- Choose data structures with runtime and memory costs in mind.
- Translate array operations into shapes and vectorized NumPy expressions.
- Use pandas without accidental alignment, silent coercion, or invalid joins.
- Reproduce an analysis from a clean environment and test awkward inputs.
- Profile before optimizing, then show the change preserves behavior.

## 1. Core Python and problem solving

Study mutability, scope, comprehensions, unpacking, exceptions, modules, and imports. Know the difference between iterable and iterator; generators help process streams without retaining the full collection. Understand context managers for reliable cleanup, decorators as wrappers, and dataclasses as lightweight records.

Choose among lists, tuples, dictionaries, sets, deques, heaps, and generators based on the operations needed. Reason about expected runtime and memory as input grows. Practice Big-O for loops, sorting, hashing, and common collection operations. A nested loop is not automatically wrong; repeated work and input size determine whether it matters.

Write functions that do one job and validate assumptions at boundaries. Use exceptions for invalid or exceptional states, not ordinary branching. Type hints describe an interface but do not validate runtime values. Pass random generators, paths, and configuration explicitly when reproducibility matters. Prefer a small function over a class unless state and behavior belong together.

## 2. NumPy: shape-first numerical programming

For a batch matrix X with shape (N, D), N is examples and D is features. If w has shape (D,), X @ w has shape (N,). Track whether labels have shape (N,) or (N, 1): broadcasting can silently turn a residual into an (N, N) matrix.

Study array creation, dtype, views versus copies, slicing, boolean masks, advanced indexing, reductions with explicit axes, and broadcasting from the trailing dimensions. Know matrix multiplication versus elementwise multiplication. Learn when vectorization reduces Python overhead and when it creates large temporary arrays. Use a seeded generator instead of global random state. Inspect finiteness and use stable formulations for probabilities and log likelihoods.

**Shape drill:** Write down the shape after each operation for X (N,D), w (D,), bias scalar, and y (N,). Repeat with y (N,1) and explain why the result differs. Add assertions so a shape mistake fails early.

## 3. pandas and tabular reasoning

Inspect index, names, dtypes, missingness, and row counts before transforming. Know label-based and position-based selection. Use explicit assignments and avoid chained writes. Practice filtering, groupby, joins, concatenation, pivots, reshaping, time parsing, and categorical dtypes.

For merges, state the intended key and cardinality. Validate one-to-one or many-to-one assumptions, count unmatched keys on both sides, and investigate duplicates before aggregation. Pandas aligns arithmetic by index labels; that is useful when intentional and a source of subtle bugs otherwise.

Missingness may be informative. Summarize it by feature, target, subgroup, and time. For time series, sort first, respect entity boundaries, and do not compute rolling features using future observations. Distinguish a row from an entity, event, and prediction point.

## 4. Visualization and exploratory analysis

Every chart should answer one question. Use distributions to find skew and tails; scatterplots for relationships; group plots to reveal heterogeneity; time plots for changes over time. Label axes, units, sample sizes, filters, and any transformations. Check overlapping points and small subgroups. Treat plots as evidence for questions to investigate, not as proof of causality.

## 5. Testing, environments, and project hygiene

Use a project environment and record direct dependencies. Use pytest for deterministic unit tests. Test empty input, one row, duplicate keys, missing values, unexpected categories, shape/dtype contracts, finite outputs, and a tiny hand-computable example. Add a regression test for each bug fixed.

Use logging instead of scattered prints in reusable code. Keep run configuration explicit. Separate reusable logic from notebook exploration, and include commands that work from a clean checkout. Pin versions when exact reproduction needs it; avoid needless dependencies.

## Practice ladder

1. Stream a large CSV and count category frequencies without loading everything.
2. Implement a standardizer and compare a clear loop with a vectorized version.
3. Build a join audit reporting duplicate keys and unmatched records on both sides.
4. Turn a notebook into importable functions and a command-line entry point.
5. Profile a slow transformation, optimize the actual bottleneck, and test equivalence.

For each exercise, include a contract, sample input/output, tests, and a note about time or memory trade-offs.

## Failure modes to recognize

- Mutating a view when a copy was expected.
- Losing row alignment during pandas arithmetic.
- Treating NaN as an ordinary value in equality checks.
- Assuming vectorized code is always faster or more memory efficient.
- Setting one random seed while leaving other randomness uncontrolled.
- Catching every exception and silently continuing.
- Relying on notebook cell order or hidden state.

## Completion evidence

- [ ] I can explain shapes for every nontrivial array expression.
- [ ] Transformations have tests for empty, missing, and duplicate cases.
- [ ] An analysis reproduces from a clean environment.
- [ ] I profiled before optimizing and verified the output stayed equivalent.
- [ ] I can describe a correctness trade-off and a memory trade-off.

## References

- [Python Tutorial](https://docs.python.org/3/tutorial/)
- [Python typing](https://docs.python.org/3/library/typing.html)
- [NumPy User Guide](https://numpy.org/doc/stable/user/)
- [pandas User Guide](https://pandas.pydata.org/docs/user_guide/)
- [Python for Data Analysis, 3rd edition](https://wesmckinney.com/book/)
