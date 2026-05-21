# Topic Proposal

## 1. Group Information

- Class: SE1823
- Group: G07
- Leader: Nguyen Nam Thinh
- Members: Nguyen Duc Anh, Nguyen Hoai An, Nguyen Thanh Phong

## 2. Proposed Title

English title:

**AI-Integrated Horse Racing Tournament Management System with Win Probability Prediction, Race Simulation, and Personalized Recommendation**

Vietnamese title:

**Hệ thống quản lý giải đua ngựa tích hợp AI dự đoán xác suất chiến thắng, mô phỏng cuộc đua và gợi ý cá nhân hóa**

## 3. Application Domain

The project belongs to the following application domains:

- Artificial Intelligence
- Sports Management System
- Tournament Management Platform
- Real-Time Simulation System
- Recommendation System
- Predictive Analytics
- Gamification and Virtual Betting

The system is designed to support the management of horse racing tournaments by providing online registration, schedule management, race result tracking, ranking, virtual betting, AI-based win probability prediction, AI-driven race simulation, and personalized race recommendation for spectators.

## 4. Problem Statement

Horse racing is a sport and entertainment activity that involves many participants such as horse owners, jockeys, referees, organizers, and spectators. In each tournament, many activities must be managed including competition registration, race scheduling, result tracking, ranking, and prediction. Currently, the management of horse racing tournaments is still largely manual and not synchronized, which causes the process of managing information, schedules, results, and predictions to be time-consuming, error-prone, and difficult for both organizers and participants.

The main practical problems include:

1. Tournament organizers manage registration, scheduling, and results through paper forms or spreadsheet files, which is slow, error-prone, and difficult to audit.
2. Horse owners and jockeys do not have a unified system to manage their horses, hired jockeys, race history, points, and earnings.
3. Spectators do not have an objective tool to evaluate the winning probability of each horse before placing a bet and often rely on personal feeling or third-party tips.
4. Race results that are generated purely by random simulation do not reflect realistic differences in horse and jockey performance and reduce the perceived fairness of the system.
5. New spectators are not guided to suitable races and find it difficult to choose races that match their preferences or previous betting behavior.
6. Manual ranking and grade promotion are difficult to track when horses participate in multiple races over long periods.

Traditional tournament management methods are often general, paper-based, and not integrated with prediction or recommendation features. As a result, organizers spend significant effort on manual operations, participants lack a personal dashboard to track their performance, and spectators have a limited and non-personalized experience.

Therefore, an AI-integrated platform is needed to help organizers manage the tournament lifecycle efficiently, help horse owners and jockeys track their performance, and help spectators receive personalized prediction and race recommendation based on historical data and real-time race information.

## 5. Motivation

This topic is important because horse racing management combines several technical challenges that are valuable for a software engineering capstone project, including role-based access control, real-time race simulation, virtual wallet and transaction management, payment sandbox integration, and AI-based prediction and recommendation. A unified digital platform can significantly improve the operation of horse racing tournaments and the experience of all participants.

Traditional management systems based on paper or spreadsheets are useful, but they are not scalable, not real-time, and do not provide intelligent support such as win probability prediction or personalized race recommendation. In addition, these systems are not connected with virtual wallet operations or simulation engines that reflect realistic race outcomes.

By integrating AI into the system, spectators can receive more objective and practical support when placing bets. AI can analyze horse and jockey profiles, compare current performance indicators, predict win probability for each race, simulate realistic finish times, and recommend races based on spectator preferences and betting history.

The system does not replace tournament officials or experienced horse racing experts. Instead, it acts as an intelligent support tool that helps organizers, participants, and spectators make better decisions and enjoy a more engaging experience.

## 6. Target Users

The main users of the system are:

1. **Horse Owners**

   Horse owners use the system to register their horses, manage horse profiles, invite jockeys, register horses for races, and track race history, ranking, and earnings of their horses.

2. **Jockeys**

   Jockeys use the system to manage their professional profile, receive and respond to invitations from horse owners, view assigned races, and track personal race history and achievements.

3. **Race Referees**

   Race referees use the system to inspect horses before each race, monitor the race, record incidents, confirm the final result, and generate official referee reports in PDF format.

4. **Spectators**

   Spectators use the system to follow tournaments and race schedules, view horse and jockey profiles, top up virtual coins, place virtual bets, watch live race simulation, follow betting history, and receive personalized race recommendation.

5. **Administrators**

   Administrators manage user accounts, tournaments, races, referee assignments, registrations, dashboard statistics, and AI service configuration.

## 7. Proposed AI Model / Method

The project does not aim to build or train a completely new AI model from scratch. Instead, it focuses on integrating existing AI models and machine learning methods into a practical horse racing management platform.

The proposed AI models and methods include:

- **Gradient Boosting Classifier (XGBoost)**

  XGBoost will be used in the Win Probability Prediction module. The model receives features extracted from horses, jockeys, and race characteristics and outputs a probability distribution over all horses in a race, indicating the chance that each horse finishes in first place.

- **Gradient Boosting Regressor (LightGBM)**

  LightGBM will be used in the AI-based Race Simulation Engine. The model predicts the finish time for each horse based on its features, and a Gaussian noise factor is added to preserve the randomness of real races.

- **Multinomial Logit Inspired Approach**

  The win probability calculation is inspired by the multinomial logit model proposed by Bolton and Chapman, which is widely used in horse racing prediction research. The softmax function is used to normalize raw scores into a valid probability distribution that sums to one.

- **Collaborative Filtering with Matrix Factorization**

  Matrix factorization techniques such as Singular Value Decomposition or Alternating Least Squares will be used to learn latent factors from the user-race interaction matrix and recommend races to spectators based on the betting behavior of similar users.

- **Content-Based Filtering**

  Content-based filtering will be used to compute similarity between races using features such as grade, distance, participating horses, and assigned jockeys, in order to recommend races similar to those a spectator has previously interacted with.

- **Hybrid Recommendation Strategy**

  The Race Recommendation module will combine collaborative filtering and content-based filtering using a weighted hybrid approach, which helps reduce the cold-start problem for new spectators and new races.

- **Feature Engineering and Statistical Analysis**

  Feature engineering will be used to derive useful features such as horse win rate, jockey win rate, recent form, current grade weight, and normalized total points from raw race history data.

## 8. System Features

The main features of the system are:

1. **User Management and Authentication**

   The system supports registration and login using Email and Password with JWT-based authentication. It manages five roles including Horse Owner, Jockey, Race Referee, Spectator, and Administrator with role-based access control.

2. **Horse and Jockey Management**

   Horse owners can manage horse profiles including breed, age, weight, current grade, total points, and violation history. They can also invite jockeys and maintain a list of regular jockeys for each horse.

3. **Tournament and Race Management**

   Administrators can create tournaments, configure races with grade, purse, registration fee, scheduled time, registration cutoff, and eligibility conditions. Administrators can also assign referees to each race.

4. **Race Registration**

   Horse owners can register their horses for eligible races by selecting a jockey from the regular jockey list. The registration fee is deducted from the owner wallet, and refund rules are applied automatically when a registration is cancelled or when a horse is disqualified before the race.

5. **Race Referee Module**

   Race referees can perform pre-race horse inspection, record incidents during the race, confirm the final result, and generate official referee reports that can be exported as PDF documents.

6. **Real-Time Race Simulation**

   The system simulates each race in real time using an AI-based simulation engine. Race position updates are broadcast to clients through Socket.IO so that spectators, owners, and jockeys can follow the race live in the web and mobile applications.

7. **Virtual Wallet and Payment Sandbox**

   Each user has a unified virtual wallet that records balance and transactions. Top-up is integrated with Stripe sandbox to simulate real payment flows without using real money.

8. **AI Win Probability Prediction**

   Before each race, the system displays the predicted win probability of each horse based on the trained XGBoost model. Spectators can use this information as an objective reference when placing bets.

9. **AI Race Recommendation**

   The system recommends races to spectators based on their betting history, followed horses and jockeys, and similar races using a hybrid recommendation approach.

10. **Virtual Betting**

    Spectators can place virtual bets on the Win, Place, or Show outcome with fixed multipliers. Bets are settled automatically after the race finishes, and payouts are added to the spectator wallet.

11. **Ranking and Statistics**

    The system maintains rankings for horses, jockeys, and owners based on points and total earnings, and provides an administrative dashboard with statistics such as total revenue, number of races, and active users.

12. **Notification**

    The system provides in-app notifications for important events such as upcoming races, race result publication, jockey invitations, bet outcomes, and pre-race disqualification refunds.

## 9. Expected Contribution

The expected contributions of the project are:

1. A unified AI-integrated tournament management platform for horse racing that supports five distinct user roles and a complete race lifecycle from tournament creation to result publication.

2. An AI-based Win Probability Prediction module that uses gradient boosting on horse, jockey, and race features and is justified by classical horse racing prediction research.

3. An AI-driven race simulation engine that produces realistic finish times by combining predictive modelling with controlled randomness.

4. A hybrid recommendation module that combines collaborative filtering and content-based filtering to suggest suitable races to spectators and to mitigate the cold-start problem.

5. A virtual wallet and Stripe sandbox payment integration that demonstrates secure transaction handling, refund flows, and automatic bet settlement without involving real money.

6. A real-time race tracking experience implemented through Socket.IO for both web and mobile clients.

7. A practical integration of XGBoost, LightGBM, matrix factorization, content-based similarity, and feature engineering inside a full-stack production-style web and mobile application.

## 10. Evaluation Plan

The system will be evaluated using both technical metrics and user-centered evaluation.

- **Dataset:**

  Race results, horse profiles, jockey profiles, registration records, and betting records collected from the system itself, combined with publicly available horse racing datasets and synthetic data generated based on the Kentucky Derby Points System for the cold-start phase.

- **Baseline:**

  Random prediction (uniform probability across horses), simple win rate ranking, random race simulation without AI, popularity-based race recommendation, and rule-based heuristic models without machine learning.

- **Metrics:**

  Top-1 accuracy and Top-3 accuracy for Win Probability Prediction, Log Loss and Brier Score for probability calibration, Root Mean Squared Error and Spearman rank correlation for Race Simulation, Precision at K, Recall at K, and Normalized Discounted Cumulative Gain at K for the Recommendation module, API response time, system uptime, and concurrent user capacity.

- **Expert evaluation:**

  Domain experts or course instructors can review the prediction outputs, simulated race results, referee report templates, and recommendation suggestions to evaluate their reasonableness, correctness, and practical value.

- **User survey:**

  Test users from the team and selected classmates can evaluate the system based on ease of use, usefulness of the win probability display, perceived realism of the race simulation, relevance of the recommended races, and overall satisfaction with the platform.

## 11. Related Papers

| No  | Title                                                                                                       | Year | Source                                                                                             | Link / DOI                    |
| --- | ----------------------------------------------------------------------------------------------------------- | ---: | -------------------------------------------------------------------------------------------------- | ----------------------------- |
| 1   | Searching for Positive Returns at the Track: A Multinomial Logit Model for Handicapping Horse Races         | 1986 | Management Science                                                                                 | DOI: 10.1287/mnsc.32.8.1040   |
| 2   | Still Searching for Positive Returns at the Track: Empirical Results from 2,000 Hong Kong Races             | 2008 | Efficiency of Racetrack Betting Markets, World Scientific                                          | World Scientific Book Chapter |
| 3   | Horse Racing Prediction at the Champ de Mars using a Weighted Probabilistic Approach                        | 2013 | International Journal of Computer Applications                                                     | IJCA Paper Link               |
| 4   | XGBoost: A Scalable Tree Boosting System                                                                    | 2016 | Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining | DOI: 10.1145/2939672.2939785  |
| 5   | LightGBM: A Highly Efficient Gradient Boosting Decision Tree                                                | 2017 | Advances in Neural Information Processing Systems (NeurIPS)                                        | NeurIPS Paper Link            |
| 6   | Matrix Factorization Techniques for Recommender Systems                                                     | 2009 | Computer (IEEE)                                                                                    | DOI: 10.1109/MC.2009.263      |
| 7   | Optimal Model of Horse Racing Competition Decision Management Based on Association Rules and Neural Network | 2022 | Scientific Programming                                                                             | DOI: 10.1155/2022/4240244     |
