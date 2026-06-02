# Dataset

## 1. Dataset Overview

The Horse Racing Tournament Management System utilizes historical horse racing data and tournament operational data to train and evaluate the AI prediction model.

The objective is to predict the probability of a horse winning an upcoming race and provide horse ranking recommendations.

---

## 2. Data Sources

The dataset is collected from the following sources:

### Horse Information

* Horse ID
* Horse Name
* Breed
* Age
* Weight
* Health Status
* Vaccination Status
* Previous Achievements
* Total Wins

### Jockey Information

* Jockey ID
* Name
* Experience (years)
* Total Participated Races
* Total Wins
* Win Rate
* Ranking Position

### Race Information

* Race ID
* Tournament ID
* Race Date
* Race Distance
* Weather Condition
* Track Condition
* Number of Competitors

### Historical Results

* Final Position
* Completion Time
* Prize Amount
* Violations
* Penalties

---

## 3. Dataset Structure

### Horse Table

| Feature       | Type     |
| ------------- | -------- |
| horse_id      | Integer  |
| age           | Integer  |
| weight        | Float    |
| breed         | Category |
| health_status | Category |
| total_wins    | Integer  |

### Jockey Table

| Feature          | Type    |
| ---------------- | ------- |
| jockey_id        | Integer |
| experience_years | Integer |
| total_races      | Integer |
| total_wins       | Integer |
| win_rate         | Float   |

### Race Table

| Feature         | Type     |
| --------------- | -------- |
| race_id         | Integer  |
| distance        | Float    |
| weather         | Category |
| track_condition | Category |
| competitors     | Integer  |

### Result Table

| Feature         | Type    |
| --------------- | ------- |
| race_id         | Integer |
| horse_id        | Integer |
| jockey_id       | Integer |
| final_position  | Integer |
| completion_time | Float   |
| prize_amount    | Float   |

---

## 4. Dataset Size

| Data Category | Estimated Records |
| ------------- | ----------------- |
| Horses        | 500+              |
| Jockeys       | 200+              |
| Tournaments   | 100+              |
| Races         | 1,000+            |
| Race Results  | 10,000+           |

---

## 5. Data Preprocessing

The following preprocessing steps are applied:

### Missing Value Handling

* Remove incomplete records
* Fill missing values using statistical methods

### Duplicate Removal

* Remove duplicated race records

### Feature Encoding

* One-Hot Encoding
* Label Encoding

### Normalization

* Scale numerical features

### Feature Engineering

Generated features include:

* Horse Win Rate
* Jockey Win Rate
* Average Race Time
* Recent Performance Score
* Health Condition Score
* Horse-Jockey Compatibility Score

---

## 6. Dataset Split

| Dataset        | Percentage |
| -------------- | ---------- |
| Training Set   | 70%        |
| Validation Set | 15%        |
| Testing Set    | 15%        |

Stratified sampling is used to maintain balanced data distribution.

---

## 7. Target Variable

Target Variable:

winner

Values:

* 1 = Horse wins the race
* 0 = Horse does not win the race

---

## 8. Dataset Usage

The dataset supports:

* Winner prediction
* Horse ranking recommendation
* Performance analysis
* Experimental evaluation of AI models
