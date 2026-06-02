# Evaluation Metrics

## 1. AI Task Definition

The AI component predicts the winning probability of horses participating in upcoming races.

The task is formulated as:

* Classification Problem
* Ranking / Recommendation Problem

---

## 2. Classification Metrics

### Accuracy

Measures the percentage of correct predictions.

Formula:

Accuracy = (TP + TN) / (TP + TN + FP + FN)

Target:

* Accuracy ≥ 80%

---

### Precision

Measures how many predicted winners are actual winners.

Formula:

Precision = TP / (TP + FP)

Target:

* Precision ≥ 80%

---

### Recall

Measures how many actual winners are correctly identified.

Formula:

Recall = TP / (TP + FN)

Target:

* Recall ≥ 80%

---

### F1-Score

Balances Precision and Recall.

Formula:

F1 = 2 × Precision × Recall / (Precision + Recall)

Target:

* F1-Score ≥ 0.80

---

## 3. Ranking Metrics

### Precision@5

Measures how many horses in the Top-5 recommendation list are actual winners.

Target:

* Precision@5 ≥ 75%

---

### Recall@5

Measures how many actual winners appear in the Top-5 recommendation list.

Target:

* Recall@5 ≥ 75%

---

### NDCG@5

Evaluates ranking quality by rewarding correctly ranked horses at higher positions.

Target:

* NDCG@5 ≥ 0.80

---

## 4. System Metrics

### Response Time

Average prediction response time.

Target:

* Less than 2 seconds

### Throughput

Number of requests processed per second.

Target:

* At least 100 concurrent users

### Latency

End-to-end processing delay.

Target:

* Less than 2 seconds

---

## 5. User Evaluation

Participants:

* Horse Owners
* Jockeys
* Spectators
* Administrators

Survey Criteria:

| Criteria               | Scale |
| ---------------------- | ----- |
| Ease of Use            | 1-5   |
| User Interface         | 1-5   |
| Prediction Helpfulness | 1-5   |
| System Performance     | 1-5   |
| Overall Satisfaction   | 1-5   |

Target:

* Average Score ≥ 4.0 / 5.0

---

## 6. Success Criteria

The proposed system is considered successful if:

* Accuracy ≥ 80%
* Precision ≥ 80%
* Recall ≥ 80%
* F1-Score ≥ 0.80
* Precision@5 ≥ 75%
* Response Time ≤ 2 seconds
* User Satisfaction ≥ 4.0 / 5.0
