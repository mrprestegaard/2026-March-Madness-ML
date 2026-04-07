# Feature Engineering & Definitions

## Overview

A critical component of this project was designing features that accurately capture team strength and matchup dynamics.

Rather than relying solely on basic statistics or seed rankings, this model incorporates advanced metrics and engineered features to better represent team performance.

---

## Core Features Used

### Elo Rating

**What it is:**
A dynamic rating system that updates after each game based on wins, losses, and opponent strength.

**Why it matters:**

* Captures overall team strength over time
* Adjusts based on quality of opponents
* Provides a stronger signal than raw win/loss records

---

### Elo vs Conference Percentage

**What it is:**
A measure of how a team performs relative to its conference competition.

**Why it matters:**

* Accounts for strength of schedule
* Helps normalize teams across different conferences
* Identifies teams that may be over- or under-valued

---

### Adjusted Offensive Efficiency (AdjOE)

**What it is:**
Points scored per 100 possessions, adjusted for opponent strength.

**Why it matters:**

* Measures how effectively a team scores
* Normalizes for pace of play
* Higher values indicate stronger offensive performance

---

### Adjusted Defensive Efficiency (AdjDE)

**What it is:**
Points allowed per 100 possessions, adjusted for opponent strength.

**Why it matters:**

* Measures defensive effectiveness
* Lower values indicate stronger defense
* Critical for identifying well-balanced teams

---

### Barthag Rating

**What it is:**
A composite metric derived from offensive and defensive efficiency.

**Why it matters:**

* Represents overall team strength
* Combines both scoring and defensive ability
* Often correlates strongly with win probability

---

## Feature Engineering Approach

### Matchup-Based Modeling

Instead of modeling teams independently, the dataset was structured around **head-to-head matchups**:

* Team1 vs Team2
* Each row represents a single game
* The target variable indicates the winner

---

### Why This Matters

This approach allows the model to learn:

* How differences in team strength impact outcomes
* Interaction effects between offense and defense
* Situations where traditional rankings (like seeds) may be misleading

---

## Key Insight

The success of the final model was driven more by **feature quality** than model complexity.

Well-engineered features such as Elo ratings and efficiency metrics provided strong predictive signals, allowing simpler models (like gradient boosting) to outperform more complex approaches like deep learning.

---
