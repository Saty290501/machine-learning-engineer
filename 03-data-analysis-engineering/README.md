# Data Analysis & Engineering

> **Purpose:** Turn raw records into data I can defend. A model cannot rescue ambiguous labels, invalid joins, future leakage, or a split that does not match deployment.

## Learning outcomes

- Define the unit of observation, prediction point, target, and eligible information.
- Profile a dataset and investigate quality problems rather than hiding them.
- Design joins, transformations, and validation checks with explicit contracts.
- Create splits that reflect time, entities, and expected use.
- Build a reproducible feature pipeline that avoids train/serve mismatch.

## 1. Start with the data contract

Before analysis, write down: what one row represents; how keys identify it; when each field becomes available; how the target is produced; which population is included; and what missing values mean. Check that the data actually matches those assumptions.

Create a schema with expected columns, types, nullability, ranges, allowed categories, uniqueness, and relationships. Validate at ingestion and after important transformations. A schema check should explain which contract failed.

## 2. Profile and audit

Inspect dimensions, dtypes, duplicate keys, missingness, ranges, category cardinality, and time coverage. Compare these by target and important subgroups. Investigate impossible values and sudden frequency changes. Do not delete outliers just because they are inconvenient; decide whether they are data errors or valid rare cases.

For missing data, record where it occurs and when. Distinguish not collected, not applicable, unknown, and zero. Imputation is a fitted transformation: estimate imputation values from training data only, then reuse them unchanged.

## 3. EDA as a sequence of questions

Begin with a question, then choose a summary or plot. Examine target prevalence, feature distributions, feature-target relationships, pairwise redundancy, and subgroup variation. Be cautious with aggregate statistics that hide group differences. Keep a log of hypotheses, filters, and findings so the analysis can be repeated.

Exploratory choices are still choices. If the same validation score guides repeated feature changes, that validation set has influenced development. Preserve a final holdout or use nested evaluation where appropriate.

## 4. SQL and relational data

Practice SELECT, filtering, aggregation, joins, CTEs, window functions, and date handling. Understand primary and foreign keys, null semantics, and how a join changes row counts.

Before joining, inspect key uniqueness and intended cardinality. After joining, compare row counts, count unmatched keys from both sides, and test a few records manually. A many-to-many join can multiply rows and alter both labels and metrics. Use query plans and indexes when a query is too slow, after confirming correctness.

## 5. Feature engineering without leakage

For numeric features, consider units, skew, clipping rules, transformations, and scaling. For categorical fields, decide how to handle unknown categories and rare levels. For dates, separate calendar effects from elapsed-time features. For text-derived fields, inspect what preprocessing removes.

A feature is unsafe if it contains information unavailable at the prediction point. Common leakage sources include post-outcome status, future aggregates, duplicate entities across random splits, target-derived encodings computed globally, and preprocessing fit on the full dataset. Fit every learned transform inside each training fold.

## 6. Splits and validation design

- Random split: suitable only when examples are exchangeable and no group or time dependency violates that assumption.
- Stratified split: preserves class proportions; it does not solve temporal or entity leakage.
- Group split: keeps related users, patients, devices, or accounts together.
- Time split: trains on the past and evaluates on later periods; use a gap if labels or features overlap across the boundary.
- Nested cross-validation: separates model selection from performance estimation when data is limited.

State what deployment scenario the split approximates. Keep a final set untouched by preprocessing decisions, threshold choices, and repeated model selection.

## 7. Reproducible feature pipelines

Separate raw input, validated tables, feature construction, labels, and split assignment. Give transformations stable names and parameters. Build transformations as a pipeline so imputation, encoding, and scaling are fitted only on training folds and are applied consistently at inference.

Record dataset source/version, extraction time, filters, split strategy, random seed, schema version, and target definition. Do not publish private or licensed data; document how to obtain or synthesize an acceptable sample.

## Practical project: leakage audit

Choose a public tabular dataset and create:
1. A data dictionary and row-level unit definition.
2. A profiling report with missingness, duplicates, and range checks.
3. A baseline split plus rationale for the deployment setting.
4. A feature pipeline fitted only on training data.
5. A leakage checklist showing availability time for each feature.
6. Tests for key uniqueness, split overlap, and stable output schema.

## Common failure modes

- Joining before validating key cardinality.
- Dropping missing values without measuring who is removed.
- Using random splits for repeated users or temporal prediction.
- Calculating rolling or target-encoding features globally.
- Fitting scaling, vocabulary, or imputation before splitting.
- Treating an EDA pattern as causal evidence.
- Reporting a cleaned dataset without recording the cleaning rules.

## Completion evidence

- [ ] I can state the unit, target, and prediction time precisely.
- [ ] Join contracts and unmatched records are measured.
- [ ] Split logic reflects the intended deployment setting.
- [ ] Learned preprocessing is fit inside training folds.
- [ ] A fresh run creates the same schema and documented split.

## References

- [pandas User Guide](https://pandas.pydata.org/docs/user_guide/)
- [DuckDB SQL documentation](https://duckdb.org/docs/stable/)
- [scikit-learn: Common pitfalls and data leakage](https://scikit-learn.org/stable/common_pitfalls.html)
- [Great Expectations documentation](https://docs.greatexpectations.io/)
