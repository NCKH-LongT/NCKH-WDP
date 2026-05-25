# Paper 04 Summary

## Citation
Tên bài: Entropy-Based Dynamic Programming for Efficient Vehicle Parking
Tác giả: 
Năm: 
Nguồn: 
DOI/Link: 

## Problem
This paper addresses the significant congestion, inefficiency, and lost time caused by drivers searching for parking spaces in urban environments. Specifically, it focuses on the unique routing challenges presented by internal, multi-story parking structures, where vertical designs and capacity constraints render traditional surface-level optimization strategies inadequate.

## Method
The authors propose a Temperature-Informed Parking Policy (TIPP) that combines an entropy-based prediction model with a dynamic programming (DP) control framework. Inspired by statistical mechanics (the canonical ensemble), the model predicts the probability of a parking spot being occupied based on its "energy" (desirability/distance to an entrance) and a single parameter called "temperature" (overall garage fill rate). A dynamic programming algorithm then uses this predicted occupancy distribution to assign entering vehicles to an optimal floor. The objective function f(i) minimizes the expected total parking time by mathematically balancing the driving time to scan a floor (t1), the passenger walking time up the stairs (t2), the vehicle driving time down the ramps (t3), and the probability of finding a spot on floor i (pi).

## Dataset
To validate the entropy prediction model, the authors used empirical data from 10 sample parking lots of varying sizes and occupancies across five US cities (Antioch and Dublin, CA; Moab, UT; Colorado Springs, CO; and Louisville, KY). To test the dynamic programming control policy, they used a custom Python simulator modeling a 10-level parking garage with 30 spots per level (300 spots total), into which 30 cars were sequentially inserted.

## Evaluation
The accuracy of the predictive entropy model was evaluated using Mean Squared Error (MSE). The efficiency of the TIPP allocation algorithm was evaluated by measuring the individual time to park and the cumulative time to park for all vehicles. The policy was benchmarked against an "Optimal Policy" (perfect information), a "Benchmark Policy" (top-down sequential search), and an "Inverse Policy" (bottom-up search) across light, medium, and high occupancy scenarios (Temperatures of 0.1, 0.5, and 1.0).

## Results
- Prediction Accuracy: The Entropy Model achieved an excellent fit against real-world data with an overall MSE of 0.173.
- Sample Efficiency: The model is highly sample-efficient, requiring only 10 observations (less than 10% of total spots) to produce a highly accurate approximation of the entire parking lot's occupancy distribution.
- Search Time Reduction: In medium (Temperature: 0.5) and high occupancy (Temperature: 1.0) scenarios, the TIPP dynamic programming algorithm consistently outperformed the Benchmark and Inverse free-choice policies, maintaining significantly lower cumulative parking times.

## Limitations
- Restrictive movement assumptions: The mathematical model assumes vehicles can only descend to lower floors and passengers can only ascend on foot, which oversimplifies real-world bi-directional garage layouts.
- Lack of slot-level precision: The algorithm only guides a vehicle to an optimal floor, leaving the driver to scan for and park at the first available slot they encounter on that level, rather than reserving a specific space.
- Simulated environment: The control policy was exclusively evaluated within a Python simulator rather than through empirical field testing in a physical multi-story garage.

## Relevance to our topic
For our project concerning "smart parking slot allocation in multi-floor buildings with motorcycle and car zones", this paper provides a vital mathematical framework for vertical routing. It proves that treating a multi-story building as a vertical distance problem—and using dynamic programming to balance the walking time against the probability of finding a spot on a given floor—drastically reduces total parking search time compared to standard unguided searches.

## Possible improvement
To adapt this model for a 90-slot multi-floor building containing 30 car and 60 motorbike spaces, the entropy model and DP framework must be expanded to handle heterogeneous vehicle types and segmented zones. The state space must be updated so that the "energy" function E(i) and the "temperature" are calculated independently for the motorcycle zones and the car zones. This would ensure the dynamic programming algorithm correctly assesses the occupancy probability of the 60 motorbike slots versus the 30 car slots, preventing a car from being routed to a floor where only motorbike spaces remain.
