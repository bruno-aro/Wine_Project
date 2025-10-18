# Wine Project – BlueBerry Winery

Predict wine type and quality from physicochemical properties, with clear EDA and statistically‑grounded insights for business decisions.

---

## 1) Project Overview

**Role:** Junior Data Analyst, CODE Analytics (course project)

**Business context:** BlueBerry Winery (Portugal) wants a data‑driven way to align product pricing and quality consistency. We analyze red and white wines to uncover key drivers of perceived quality and build simple predictive models.

**Objectives:**

* **EDA:** Compare red vs. white composition; explore patterns that relate to quality.
* **Statistical testing:** Validate differences across quality groups (e.g., alcohol levels).
* **ML (classification):**

  1. Predict *wine type* (red/white).
  2. Predict *quality label* (low/medium/high).
* **Communication:** Present actionable insights for pricing/quality strategy.

---

## 2) Data

* Sources: `winequality-red.csv` (1,599 rows) and `winequality-white.csv` (4,898 rows) + `winequality.names` (data dictionary).
* Target(s):

  * `wine_type` (engineered): red vs. white.
  * `quality_label` (engineered): low (≤5), medium (≤7), high (>7) from `quality` (0–10 expert score).
* Core features (numeric): fixed/volatile acidity, citric acid, residual sugar, chlorides, free/total SO₂, density, pH, sulphates, alcohol.

**Basic checks:** head/tail, `info()`, shape, missing values, duplicates, outliers.

---

## 3) Method & Workflow (high level)

1. **Wrangle & labeling**

   * Load red/white; add `wine_type`; create categorical `quality_label`.
   * Handle nulls/outliers (IQR as needed), dtypes, duplicates.
2. **EDA**

   * Descriptive stats (red vs. white) and visual comparisons.
   * Univariate: histograms per feature; quality distribution.
   * Bivariate/multivariate: boxplots by `quality_label`, joint plots, correlation heatmap.
3. **Statistical tests**

   * One‑way **ANOVA** (e.g., alcohol across quality levels) to confirm significant group differences.
4. **ML prep**

   * Encode categoricals (Label/Ordinal/One‑Hot where appropriate).
   * Train/test split (stratified for quality); **scale on train only** to avoid leakage.
5. **Modeling**

   * Baseline: Logistic Regression → compare with tree/ensemble models.
   * Cross‑validation & hyperparameter tuning.
6. **Evaluation**

   * Confusion matrix; accuracy; **precision/recall/F1 (weighted)**; **Cohen’s kappa** (robust to imbalance).
7. **Communication**

   * Non‑technical summary: drivers, model performance, and business recommendations.

---

## 4) Exploratory Insights (examples to reproduce)

* Red vs. white differ on **volatile acidity** and **sulphates**; density and residual sugar distributions are also distinct.
* Alcohol tends to be higher in higher‑quality labels (validate via ANOVA).
* Correlation heatmap highlights relationships to monitor for collinearity/leakage.

---

## 5) Modeling Snapshot

* **Targets:**

  * *Type model:* binary classification (red vs. white).
  * *Quality model:* multi‑class classification (low/medium/high).
* **Preprocessing:**

  * Ordinal encode `quality_label` for y or map to classes; one‑hot for nominal features.
  * Standardize numeric features (fit on train → transform train/test).
* **Algorithms tried:** Logistic Regression (baseline), Decision Tree / Random Forest / Gradient Boosting (as comparisons).
* **Metrics reported:**

  * Weighted‑F1 and Cohen’s kappa (quality model), Accuracy and ROC‑AUC (type model), plus confusion matrices.

---

## 6) Deliverables

* 4 EDA figures (type mix, quality distribution, boxplots, heatmap, key histograms).
* Confusion matrices and classification report(s).
* Short slide deck for non‑technical stakeholders.
