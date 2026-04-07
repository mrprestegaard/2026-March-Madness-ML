# Modeling Approach

## Overview

This project was framed as a **binary classification problem**, where the goal was to predict the probability that Team1 defeats Team2 in a given matchup.

Each observation represents a head-to-head game, with engineered features describing both teams.

---

## Model Candidates

Multiple modeling approaches were tested to determine the best fit for this problem.

### 1. Logistic Regression (Baseline)

A logistic regression model was used as a baseline to establish a simple, interpretable benchmark.

**Why used:**

* Fast to train
* Easy to interpret
* Provides a strong baseline for comparison

---

### 2. LSTM (Experimental)

A Long Short-Term Memory (LSTM) model was tested to evaluate whether sequential patterns in team performance could improve predictions.

**Approach:**

* Modeled sequences of prior games
* Attempted to capture temporal trends in team performance

**Results:**

* Accuracy: ~0.507
* ROC-AUC: 0.500

**Conclusion:**
The model performed at approximately random levels, indicating it was unable to extract meaningful signal from the data.

**Why it struggled:**

* The problem is not inherently sequential (it is matchup-based)
* Limited dataset size for deep learning
* Engineered features already captured historical performance effectively

---

### 3. Gradient Boosting (XGBoost) — Final Model

A gradient boosting model was selected as the final approach.

**Why used:**

* Strong performance on structured/tabular data
* Captures nonlinear relationships between features
* Handles feature interactions effectively

**Hyperparameters (example):**

* n_estimators: 200
* learning_rate: 0.025
* max_depth: 6
* subsample: 0.8
* colsample_bytree: 0.8

---

## Model Evaluation

Models were evaluated using:

* **Accuracy** — overall correctness of predictions
* **ROC-AUC** — quality of probability estimates

| Model             | Accuracy | ROC-AUC |
| ----------------- | -------- | ------- |
| LSTM              | 0.507    | 0.500   |
| Gradient Boosting | 0.797    | 0.874   |

---

## Model Selection

The gradient boosting model was selected based on significantly stronger performance.

### Key Insight

The problem is best treated as a **tabular classification task**, not a sequence modeling problem.

Tree-based models were more effective because they:

* Leverage engineered features directly
* Capture nonlinear relationships
* Require less data than deep learning models

---

## Prediction Strategy

The final model outputs **win probabilities** for each matchup.

These probabilities were used to:

* Select likely winners
* Identify potential upset opportunities
* Improve bracket decision-making

---

## Lessons Learned

* Feature engineering had a greater impact than model complexity
* Deep learning is not always the best approach for structured data
* Matchup-based modeling is critical for sports predictions
* Probability-based decisions outperform intuition in aggregate

---
