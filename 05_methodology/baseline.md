# Baseline Methods

## 1. Baseline 1 – Rule-Based Ranking

### Description

A traditional ranking approach using manually defined business rules.

### Formula

Horse Score =
0.5 × Horse Win Rate +
0.3 × Jockey Win Rate +
0.2 × Recent Performance Score

### Prediction Rule

The horse with the highest score is predicted as the winner.

### Advantages

* Easy to implement
* Easy to explain

### Disadvantages

* Cannot learn hidden patterns
* Sensitive to manually selected weights

---

## 2. Baseline 2 – Historical Average Method

### Description

Prediction is based solely on historical average race completion time.

### Formula

Average Time = Total Completion Time / Number of Participated Races

### Prediction Rule

The horse with the lowest average completion time is predicted as the winner.

### Advantages

* Very simple implementation
* Low computational cost

### Disadvantages

* Ignores jockey performance
* Ignores weather condition
* Ignores horse health information

---

## 3. Baseline 3 – Logistic Regression

### Description

A supervised machine learning classification model.

### Input Features

* Horse age
* Horse weight
* Horse win rate
* Jockey experience
* Jockey win rate
* Previous achievements

### Output

Probability that a horse wins the race.

### Advantages

* Fast training
* Easy interpretation

### Disadvantages

* Limited ability to model complex relationships

---

## 4. Proposed Model

### Model

Random Forest / XGBoost

### Input Features

Horse Features:

* Age
* Weight
* Breed
* Health Status
* Historical Performance

Jockey Features:

* Experience
* Win Rate
* Ranking

Race Features:

* Distance
* Weather
* Track Condition
* Number of Competitors

### Expected Advantages

* Higher prediction accuracy
* Better ranking quality
* Better generalization capability

---

## 5. Experimental Comparison

| Method              | Accuracy | Precision | Recall | F1-Score | Precision@5 |
| ------------------- | -------- | --------- | ------ | -------- | ----------- |
| Rule-Based Ranking  | -        | -         | -      | -        | -           |
| Historical Average  | -        | -         | -      | -        | -           |
| Logistic Regression | -        | -         | -      | -        | -           |
| Proposed AI Model   | -        | -         | -      | -        | -           |
