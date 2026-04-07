# March Madness Bracket Prediction with Machine Learning

This project uses machine learning to predict NCAA March Madness basketball game outcomes and generate bracket picks based on win probabilities.

The goal was to test whether a data-driven approach could outperform intuition in a real bracket challenge. Using engineered team-strength and matchup features, I trained and evaluated multiple models to predict head-to-head game outcomes. The final model helped power a winning office March Madness bracket.

---

## Project Objective

The objective of this project was to predict the probability that one NCAA basketball team would defeat another in a tournament matchup.

Rather than ranking teams in isolation, the problem was framed as a **matchup-based binary classification task**, where each observation represented a Team 1 vs Team 2 game and the target variable indicated the winner.

---

## Data Sources

This project combines historical NCAA basketball data with external advanced team metrics.

### Primary sources
- Kaggle March Machine Learning Mania competition datasets
- Historical regular season game results
- Team metadata and spellings tables
- External advanced metrics from Bart Torvik

### Additional processing
To integrate external team ratings with Kaggle data, team names were cleaned and matched using:
- manual team name fixes
- spelling tables
- fuzzy matching for unresolved cases

---

## Feature Engineering

A major focus of the project was creating features that better represented team quality and matchup strength.

### Key features used in the men's model
- `Elo_T1`
- `Elo_T2`
- `Elo_vs_Conf_Pct_T1`
- `Elo_vs_Conf_Pct_T2`
- `AdjOE_T1`
- `AdjOE_T2`
- `AdjDE_T1`
- `AdjDE_T2`
- `Barthag_T1`
- `Barthag_T2`

### Additional engineered features explored
- season-by-season Elo ratings
- conference-relative strength
- Pythagorean expectation
- offensive and defensive efficiency metrics
- team-level advanced performance indicators from Bart Torvik

---

## Modeling Approach

I tested multiple machine learning approaches to determine which was the best fit for this problem.

### 1. LSTM (experimental)
I explored an LSTM-based sequence model to test whether prior game history in sequence form would improve predictions.

**Results**
- Accuracy: ~0.507
- ROC-AUC: 0.500

This model performed at approximately random-chance levels, suggesting that a sequence-based deep learning approach was not a good fit for this matchup prediction problem.

### 2. Gradient Boosting / XGBoost (final approach)
I also trained a gradient boosting classifier using the engineered team and matchup features.

**Results**
- Accuracy: ~0.797
- ROC-AUC: 0.874

This model performed substantially better and became the preferred approach for bracket prediction.

---

## Why Gradient Boosting Outperformed LSTM

The project reinforced an important machine learning lesson: the best model is not always the most complex one.

The LSTM underperformed likely because:
- the problem is fundamentally a **tabular classification** problem rather than a true sequence problem
- tournament outcomes are noisy and limited in sample size
- engineered features like Elo and efficiency ratings already captured much of the relevant historical information

Gradient boosting was a better fit because it:
- performs well on structured/tabular data
- captures nonlinear feature interactions
- works effectively with smaller datasets
- makes strong use of carefully engineered features

---

## Model Evaluation

Models were evaluated using:
- Accuracy
- ROC-AUC

| Model | Accuracy | ROC-AUC |
|------|----------|---------|
| LSTM | 0.507 | 0.500 |
| Gradient Boosting / XGBoost | 0.797 | 0.874 |

---

## Bracket Strategy

After training the final model, I used predicted win probabilities to evaluate tournament matchups and make bracket selections.

This approach supported:
- probability-based winner selection
- upset identification
- stronger decision-making than relying on seed alone

The final result was a bracket that won my office March Madness challenge.

---

## Key Takeaways

- Feature engineering was more important than model complexity
- Elo and efficiency-based features added strong predictive value
- Sequence models were not well suited for this problem
- Matchup-based modeling was more useful than simple team ranking
- Probability-based decision-making helped improve bracket selection strategy

---

## Repository Contents

- `notebooks/` – exploratory work and modeling notebooks
- `src/` – reusable helper functions and model code
- `docs/` – project documentation and write-up
- `data/` – notes on source datasets and data handling

---

## Future Improvements

Potential next steps for this project include:
- tournament-specific feature engineering
- more formal cross-validation by season
- calibration testing for predicted probabilities
- simulation-based bracket optimization
- feature importance and SHAP-based interpretability

---

## Author

Madeline Prestegaard

This project was built as a practical machine learning experiment applying sports analytics, feature engineering, and predictive modeling to NCAA tournament forecasting.
