# Bank Marketing – EDA & Classification

Project using the [UCI Bank Marketing dataset](https://archive.ics.uci.edu/dataset/222/bank+marketing) to work through exploratory data analysis and compare classification algorithms for predicting whether a client subscribes to a term deposit.

## Business Questions

- Which client and campaign attributes are most associated with a client subscribing to a term deposit?
- Can we reliably predict, ahead of a call, which clients are likely to subscribe — to help prioritize outreach?
- How do contact method, timing (day/month), and call duration relate to campaign success?
- Does prior campaign outcome (`poutcome`) or contact history (`pdays`, `previous`) meaningfully improve prediction of future subscription?
- Which classification algorithm best balances precision and recall for this imbalanced target, and is suitable for practical deployment?

## Dataset

Sourced directly via the [`ucimlrepo`](https://pypi.org/project/ucimlrepo/) package (`fetch_ucirepo(id=222)`). Contains client attributes (age, job, marital status, education, etc.), campaign contact details (contact type, day/month, duration, previous outcomes), and the binary target `y`.

## Project Status

**Work in progress** — currently in the data cleaning / EDA phase. Model benchmarking is planned but not yet implemented.

### Completed so far
- Loaded dataset via `ucimlrepo`
- Reviewed metadata and variable descriptions
- Split features into categorical and numerical columns
- Fixed inconsistent category labels (e.g. `admin.` → `admin` in `job`)
- Quantified and imputed missing values (`job`, `education`, `contact`, `poutcome` → `unknown`)
- Handled the `pdays` sentinel value (`-1` = never contacted): added a `never_contacted` flag and imputed with the median of actual contact days
- Visualized the `balance` distribution (histogram + boxplot) to inspect negative balances and outliers

### Planned next steps
- Continue univariate/bivariate EDA (categorical distributions vs. target, correlations)
- Outlier treatment and feature engineering
- Encode categorical variables and scale numerical features
- Train/test split
- Train and compare multiple classifiers (e.g. Logistic Regression, Random Forest, Gradient Boosting, SVM)
- Evaluate with appropriate metrics (given class imbalance in `y`): precision, recall, F1, ROC-AUC
- Model selection and interpretation (feature importance)

## Tech Stack

- Python
- pandas, numpy
- matplotlib, seaborn
- ucimlrepo

## Setup

```bash
pip install pandas numpy matplotlib seaborn ucimlrepo
```

## Usage

Open and run `bank_marketing.ipynb` in Jupyter:

```bash
jupyter notebook bank_marketing.ipynb
```

## Repository Structure

```
.
├── bank_marketing.ipynb   # EDA and modeling notebook
└── README.md
```

## License

For personal learning purposes. Dataset usage subject to the [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/222/bank+marketing) terms.
=======
