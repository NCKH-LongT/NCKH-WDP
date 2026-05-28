# Citation
* **Title:** Linkage of jockey falls and injuries with racehorse injuries and fatalities in Thoroughbred flat racing in Victoria, Australia.
* **Authors:** Ashleigh V. Morrice-West, Megan Thomas, Adelene S. M. Wong, Meredith Flash, R. Chris Whitton and Peta L. Hitchens.
* **Year:** 2025
* **Source:** https://www.researchgate.net/publication/388964434_Linkage_of_jockey_falls_and_injuries_with_racehorse_injuries_and_fatalities_in_Thoroughbred_flat_racing_in_Victoria_Australia
* **DOI/Link:** 10.3389/fvets.2024.1481016

# Problem
The paper addresses the issue of investigating racehorse incidents (injuries and fatalities) and jockey incidents (falls and injuries) in tandem rather than in isolation.
It aims to identify modifiable risk factors common or conflicting to both horses and riders using a "One Health" approach to improve overall safety.

# Method
The researchers utilized Poisson regression to estimate incidence rate ratios (IRR).
They applied mixed-effects logistic regression (both univariable and multivariable) to identify horse-level, race-level, jockey-level, and trainer-level factors associated with adverse outcomes.
Pearson's chi-square test was used to assess the difference in proportions of racehorse catastrophic injuries or sudden deaths resulting in a jockey injury.

# Dataset
* **Horse Data:** Race and trial history, injury, and fatality data from the Single National System (SNS) and the Australian Racing Incident Database (ARID) from August 1, 2004, to December 31, 2018, encompassing 651,842 flat race starts.
* **Jockey Data:** Jockey incident dataset from Racing Victoria Ltd. (RVL) spanning January 1, 2014, to December 31, 2019.
* **Merged Data:** For shared risk factor modeling, databases were one-to-one matched for the period of January 1, 2014, to December 31, 2018, resulting in 213,569 flat race starts.

# Evaluation
Incidence rates expressed as the number of events per 1,000 race starts.
Incidence rate ratios (IRR) with 95% confidence intervals (CI).
Odds ratios (OR) with 95% confidence intervals (CI) and p-values to determine statistical significance (limit set at p <= 0.05).

# Results
* **Incidence Rates:** Per 1,000 starts, there were 21.21 racehorse musculoskeletal injuries (MSI), 0.55 racehorse fatalities, 3.01 jockey falls, and 1.79 jockey injuries.
* **Causality:** A racehorse incident was the most prominent risk factor for jockey falls and injuries during a race, with approximately one-third of racehorse fatalities resulting in a jockey fall.
* **Shared Risks:** Firmer turf track conditions and riding less accomplished horses (indicated by no prior prize money earned) increased the risk for both jockey and horse adverse outcomes.
* **Jockey Risks:** Jockeys with fewer career race rides were at a greater risk of falling, while those with a higher percentage of last-place finishes had a greater risk of injury.
* **Recommendation:** The findings strongly support the recommendation that inexperienced riders (e.g., apprentices) should not be paired with novice or inexperienced horses.

# Limitations
Jockey and racehorse incident data are maintained in separate, non-standardized databases, making data linkage and cross-jurisdictional comparisons inefficient and challenging.
The data only accounts for race-day and official trial incidents, thereby underestimating total incidents by excluding trackwork and training accidents.
Unmeasured jockey health conditions, such as dehydration or osteopenia, could be confounding factors for injury risks.
The study linked specific jockey-horse pairs directly, meaning falls caused by interference from other fallen horses in the race might be underestimated.

# Relevance to our topic
The paper provides direct statistical evidence validating the critical need for proper "matching" between jockeys and racehorses. It proves that combining an inexperienced jockey with an inexperienced or poorly performing horse creates a compounding risk effect that significantly increases the probability of severe accidents.

# Possible improvement
* **System/Algorithm Development:** Develop an automated matching or flagging algorithm that utilizes historical racing data to prevent high-risk pairings, such as blocking apprentice jockeys from riding maiden horses.
* **Data Integration:** Establish near real-time, interoperable databases that seamlessly integrate jockey medical records, racehorse veterinary histories, and workload monitoring to flag at-risk pairs before race day.
* **Wearable Technology Integration:** Utilize wearable biometric devices for both the horse (locomotor/cardiac function) and the jockey during training to continuously evaluate fitness and predict prodromal signs of injury.
