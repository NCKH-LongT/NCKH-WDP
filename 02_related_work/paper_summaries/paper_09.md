# Paper 09 Summary

## Citation
Tên bài: Motorcycle Drivers' Parking Lot Choice Behaviors in Developing Countries: Analysis for Ho Chi Minh City, Vietnam
Tác giả: Hoang & Vu
Năm: 2019
Nguồn: MDPI
DOI/Link: 

## Problem
This paper addresses the traffic congestion, emissions, and urban management challenges caused by motorcycle drivers searching for parking spaces in developing countries. Specifically, it focuses on identifying the influence factors that affect motorcycle drivers' parking lot choice behaviors (on-street, off-street, and temporary/illegal parking) in motorcycle-dominated urban areas like Vietnam.

## Method
The authors conducted a Stated Preference (SP) survey using a Taguchi design array (mixed 2-3 levels) generating 36 scenarios for respondents to evaluate. The collected data was analyzed using discrete choice models under the assumption of Random Utility Maximization (RUM). Specifically, the study formulated and tested three models: the standard Multinomial Logit (MNL) model, the degenerate Nested Logit model, and the Mixed Logit (RUM-ML) model, with utility equations built on variables like parking cost, walking distance, queuing time, and capacity.

## Dataset
Data was collected in Ho Chi Minh City (HCM City), Vietnam, a highly motorcycle-dependent urban center. The dataset consists of 530 total survey responses (collected via online Google Forms and direct interviews at 7 parking lots in the Central Business District), yielding a final sample of 318 valid responses specifically from motorcycle drivers.

## Evaluation
The discrete choice models were evaluated and compared using model-fit metrics, primarily the Log-Likelihood (LL) and the McFadden parameter (ρ²). Additionally, the Nested Logit model was evaluated using the Inclusive Value (IV) parameter (λk) to measure the degree of independence and correlation among unobserved utility components across the different parking nests.

## Results
- Model Fit: The Mixed Logit model performed the best with a Log-Likelihood of -995.44 and ρ² = 0.288, outperforming the standard MNL model. The Nested Logit model was rejected due to a lack of correlation between on-street and temporary parking (λk = 5.40).
- Preferences: 51.7% of motorcycle drivers preferred on-street parking, with 23.98% specifically looking for free on-street spots.
- Search Behavior: When looking for a spot in unfamiliar areas, 38% of drivers stop to ask pedestrians, 28% cruise on the road to find a spot, and 23% use internet searches.
- Utility Factors: Parking fee, walking distance, and queuing time all showed negative coefficients, meaning increases in these factors decrease the probability of a driver choosing that lot. Conversely, lot capacity had a positive effect.

## Limitations
- The study relies on Stated Preference (SP) questionnaires based on hypothetical scenarios, which may differ from drivers' real-world, Revealed Preference (RP) behavior.
- The inclusion of "temporary parking" (illegal parking) as an alternative confused many respondents who deliberately equated it with legal on-street parking, undermining the validity of the Nested Logit model structure.
- It does not propose or simulate a technological solution (like an allocation algorithm); it strictly observes and analyzes existing manual searching behaviors.

## Relevance to our topic
For our project on "smart parking slot allocation in multi-floor buildings with motorcycle and car zones", this paper is highly relevant as it explicitly quantifies the unique search behavior of motorcycle drivers. Because motorcycles are highly maneuverable, a massive 38% of drivers stop to ask for directions while 28% cruise, creating localized curbside congestion. The paper also mathematically proves that "queuing time" has a significant negative impact on their utility. This strongly justifies our project: an automated allocation system would eliminate the need for motorcycles to cruise or ask for directions, routing them directly to their dedicated zones.

## Possible improvement
To extend these findings to a multi-floor parking building with 90 slots (30 car + 60 motorbike), an allocation algorithm should be designed to aggressively minimize queuing time at the main entrance, which this paper identified as a major deterrent for motorcycle users. Instead of forcing 60 motorcycles to queue at a single ticketing gate alongside 30 cars, the system could use the 23% of users already comfortable with "internet searches" to pre-allocate the 60 motorbike slots via a mobile app, allowing them to bypass the main car queue and proceed directly to their segmented floors.
