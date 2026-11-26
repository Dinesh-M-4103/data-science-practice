# 🧠 Machine Learning — Daily Learning Journal

> *"Learn a little every day, and the compound interest does the rest."*

A living notebook of my machine learning journey. Each topic gets its own folder with hands-on Jupyter notebooks, small datasets, and notes — built from first principles, then implemented with real libraries.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)
![Status](https://img.shields.io/badge/status-learning%20in%20public-brightgreen)

---

## 🎯 Purpose

- Build a solid, intuitive understanding of ML concepts — not just call `.fit()`.
- Keep a searchable record of what I learn, day by day.
- Practice explaining ideas clearly through code, plots, and short notes.

## 📚 Learning Roadmap

| Status | Topic | Folder |
|:------:|-------|--------|
| ✅ | Simple Linear Regression | [`Simple Linear Regression/`](Simple%20Linear%20Regression) |
| ✅ | Multiple Linear Regression | [`Multiple Linear Regression/`](Multiple%20Linear%20Regression) |
| ✅ | Polynomial Regression | [`Polynomial Regression/`](Polynomial%20Regression) |
| 🚧 | Regularization (Ridge / Lasso / ElasticNet) | *up next* |
| ⏳ | Logistic Regression | — |
| ⏳ | Decision Trees & Random Forests | — |
| ⏳ | k-Nearest Neighbors | — |
| ⏳ | Support Vector Machines | — |
| ⏳ | Naive Bayes | — |
| ⏳ | Clustering (K-Means, Hierarchical, DBSCAN) | — |
| ⏳ | Dimensionality Reduction (PCA) | — |
| ⏳ | Gradient Boosting (XGBoost, LightGBM) | — |
| ⏳ | Model Evaluation, Cross-Validation & Hyperparameter Tuning | — |
| ⏳ | Neural Networks & Deep Learning basics | — |

Legend: ✅ done · 🚧 in progress · ⏳ planned

## 🗂️ Repository Structure

```
Machine Learning/
├── Simple Linear Regression/
│   ├── Simple_Linear_Regression.ipynb     # Height from weight: EDA, model, metrics, OLS
│   └── height-weight.csv                  # Dataset: 23 rows, Weight & Height
├── Multiple Linear Regression/
│   ├── Multiple_Linear_Regression.ipynb   # Index price: CV, metrics, residual analysis, OLS
│   └── economic_index.csv                 # Dataset: 24 rows, interest & unemployment rate
├── Polynomial Regression/
│   └── Polynomial_Regression.ipynb        # Synthetic quadratic data, degrees 1-6, Pipeline
└── README.md
```

Each topic lives in its own folder with a notebook and the dataset(s) it uses (Polynomial Regression generates its own data, so it has no CSV).

> **Note:** the notebooks were written in Google Colab and read their CSVs from `/content/`. When running locally, change the path to the CSV in the same folder, e.g. `pd.read_csv("height-weight.csv")`.

## 📈 Simple Linear Regression

Predicting **height from weight** with a single-feature linear model.

**What the notebook covers**
- Loading the data with `pandas`, then a scatter plot, correlation matrix, heatmap and pairplot
- Why `X` must be 2-D (a DataFrame) while `y` can be 1-D
- 75/25 train/test split, then `StandardScaler` fitted on the training set only
- `LinearRegression` fit, with slope and intercept read from `coef_` and `intercept_`
- Plotting the best-fit line over the training data
- Metrics: **MSE, MAE, RMSE, R²** and a hand-computed **adjusted R²**
- A `statsmodels` OLS summary and a prediction for a new weight

**Results**

| Metric | Value |
|---|---|
| Correlation (Weight vs Height) | 0.93 |
| R² (test) | 0.74 |
| Adjusted R² (test) | 0.67 |
| MAE / RMSE (test) | 9.67 / 10.72 |

**Key idea:** fit a line `y = β₀ + β₁x` that minimizes the sum of squared errors between predictions and actual values.

## 📊 Multiple Linear Regression

Predicting an **index price** from **interest rate** and **unemployment rate**.

**What the notebook covers**
- Cleaning: dropping the unused `Unnamed: 0`, `year` and `month` columns and checking for nulls
- EDA: pairplot, correlation matrix, heatmap, scatter and `regplot`
- 75/25 split and `StandardScaler`
- Training a two-feature `LinearRegression`
- **3-fold cross-validation** with `cross_val_score` (negative MSE)
- Metrics: **MSE, MAE, RMSE, R²** and **adjusted R²**
- **Checking assumptions:** actual vs predicted plot, residuals with a KDE plot, and residuals vs predictions
- A `statsmodels` OLS summary

**Results**

| Metric | Value |
|---|---|
| Mean CV score (neg. MSE) | -5914.8 |
| R² (test) | 0.83 |
| Adjusted R² (test) | 0.71 |
| MAE / RMSE (test) | 59.94 / 76.12 |
| Coefficients (scaled features) | interest rate +88.3, unemployment rate -116.3 |

**Key idea:** extend the line to several features, `y = β₀ + β₁x₁ + β₂x₂ + …`, where each coefficient shows a feature's effect with the others held constant. The two inputs are strongly correlated with each other (-0.93), a **multicollinearity** warning sign.

With only 24 rows, the test set has just 6 points, so these scores are noisy.

## 🌀 Polynomial Regression

Fitting **curved data** with a linear model by adding polynomial features.

**What the notebook covers**
- Generating 100 synthetic points from `y = 0.5x² + 1.5x + 2 + noise`
- Fitting a plain straight line first as the baseline
- Using `PolynomialFeatures` (degree 2 and degree 3) to expand `X`, then fitting `LinearRegression` on it
- Drawing a smooth prediction curve over a `linspace` of new X values
- Building a **`Pipeline`** (`PolynomialFeatures` → `LinearRegression`) in a reusable `poly_regression(degree)` function
- Trying degree 6 to see the model start to **overfit**

**Results** (random data, no seed, so your numbers will vary)

| Model | R² (test) |
|---|---|
| Straight line | 0.66 |
| Degree 2 | 0.93 |
| Degree 3 | 0.93 |

**Key idea:** the model is still linear in its coefficients. Only the inputs are transformed (`x → x, x², x³ …`). Higher degrees give more flexibility but risk overfitting, which is what **regularization** (up next) tackles.

## 🛠️ Tech Stack

- **Python 3**
- **NumPy**, **pandas** — numerical computing and data wrangling
- **Matplotlib**, **seaborn** — visualization
- **scikit-learn** — modeling, preprocessing, metrics
- **statsmodels** — statistical analysis
- **Jupyter Notebook / VS Code** — interactive environment

## 🚀 Getting Started

```bash
# 1. Clone the repository
git clone <your-repo-url>
cd "Machine Learning"

# 2. (Recommended) create a virtual environment
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # macOS / Linux

# 3. Install dependencies
pip install numpy pandas matplotlib seaborn scikit-learn statsmodels jupyter

# 4. Launch Jupyter
jupyter notebook
```

Then open any notebook inside a topic folder and run the cells top to bottom.

## 🧭 How I Study Each Topic

1. **Intuition** — what problem does this solve, and why does it work?
2. **Math** — the core equations, kept as simple as possible.
3. **Code** — implement it, then compare with the library version.
4. **Evaluate** — pick the right metrics and interpret the results.
5. **Reflect** — note pitfalls, assumptions, and when *not* to use it.

## 🔗 Resources I Find Useful

- [scikit-learn User Guide](https://scikit-learn.org/stable/user_guide.html)
- [StatQuest with Josh Starmer](https://www.youtube.com/@statquest)
- [Andrew Ng's Machine Learning Specialization](https://www.coursera.org/specializations/machine-learning-introduction)
- [Kaggle Learn](https://www.kaggle.com/learn)

## 🤝 Feedback

This is a personal learning repo, but suggestions, corrections, and discussion are always welcome — feel free to open an issue.

---

<p align="center">⭐ If you find this useful, consider starring the repo — and happy learning!</p>
