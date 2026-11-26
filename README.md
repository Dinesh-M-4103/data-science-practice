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
| ⏳ | Polynomial Regression & Regularization (Ridge / Lasso) | — |
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
│   ├── Simple_Linear_Regression.ipynb     # Notebook: EDA, model, evaluation
│   └── height-weight.csv                  # Dataset: weight (kg) vs height (cm)
├── Multiple Linear Regression/
│   ├── Multiple_Linear_Regression.ipynb   # Notebook: EDA, model, cross-validation, residuals
│   └── economic_index.csv                 # Dataset: interest & unemployment rate vs index price
└── README.md
```

Each new topic follows the same layout: a folder containing a notebook and the dataset(s) it uses.

## 📈 Featured: Simple Linear Regression

Predicting **height from weight** with a single-feature linear model.

**What the notebook covers**
- Loading and exploring data with `pandas`
- Visualizing relationships with `matplotlib` and `seaborn` (scatter plots, correlation)
- Scaling features with `StandardScaler`
- Training a model with `scikit-learn`'s `LinearRegression`
- Evaluating with **MAE**, **MSE**, **RMSE**, and **R²**
- Cross-checking coefficients and statistics using `statsmodels` (OLS summary)

**Key idea:** fit a line `y = β₀ + β₁x` that minimizes the sum of squared errors between predictions and actual values.

## 📊 Featured: Multiple Linear Regression

Predicting a **stock market index price** from **interest rate** and **unemployment rate**.

**What the notebook covers**
- Exploring feature relationships with `seaborn` (pairplot, heatmap, regplot)
- Train/test split and feature scaling with `StandardScaler`
- Training a multi-feature `LinearRegression` model
- Validating with **cross-validation** (`cross_val_score`, negative MSE)
- Evaluating with **MAE**, **MSE**, **RMSE** and **R²**
- Analysing **residuals** with a KDE plot to check model assumptions

**Key idea:** extend the line to several features, `y = β₀ + β₁x₁ + β₂x₂ + …`, where each coefficient shows a feature's effect with the others held constant.

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
