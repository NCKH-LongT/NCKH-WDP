# Paper 02 Summary

## Citation
Tên bài: ParkGauge: Gauging the Occupancy of Parking Garages with Crowdsensed Parking Characteristics
Tác giả: 
Năm: 2016
Nguồn: NTU (Nanyang Technological University)
DOI/Link: 

## Problem
This paper addresses the challenge of acquiring real-time occupancy information for indoor parking garages, where traditional crowdsensing methods fail because infrastructure like GPS and Wi-Fi is unavailable. Furthermore, installing physical occupancy sensors at every parking slot is too expensive and lacks scalability, while existing crowdsourced apps requiring manual data entry lack user incentives.

## Method
The authors propose "ParkGauge," an infrastructure-free smartphone crowdsensing method that infers garage occupancy by evaluating temporal parking characteristics rather than directly counting vehicles. The system uses low-power smartphone sensors (accelerometer, gyroscope, and barometer) to extract time-domain and frequency-domain features. A Random Forest classifier (using 10 trees with a max depth of 3) identifies driving states such as braking, accelerating, and turning. A Hidden Markov Model (HMM) then translates these observable states into hidden driving contexts, such as "cruising," "queuing," or "parked". Finally, Support Vector Regression (SVR) utilizing a Pearson VII Universal Kernel (PUK) is used to map these temporal characteristics (like time-to-park and time-in-queuing) into an accurate prediction of the garage's real-time occupancy.

## Dataset
Data was collected over two months in Singapore and London across various shopping mall parking garages. The dataset contains roughly 120 traces (including 62 self-parking sessions) gathered by 6 different drivers using both petrol and electric cars. The data was collected using 5 different Android smartphones (Samsung Galaxy S4, S3, HTC One M8, One X, and LG Nexus 5). For testing the regression model, a dataset of 78 records was used, combining 37 high-fidelity manual observations with 41 crowdsensed records from the app.

## Evaluation
The primary metric used to evaluate the accuracy of the occupancy inference regression methods is the Normalized Root-Mean Squared Error (NRMSE). The system also evaluated the accuracy and latency of detecting driving contexts across various time window sizes, and the Cumulative Distribution Function (CDF) of the estimation errors for time-to-park.

## Results
- Occupancy Inference: SVR with the PUK kernel achieved the best generalization performance, yielding an NRMSE of 0.0993. This approach more than doubled the accuracy of a Simple Linear Regression model (NRMSE 0.2106) that only used the time-to-park feature.
- Time-to-Park Estimation: The error margin for predicting time-to-park was highly accurate, mostly clustering around 18 seconds and bounded between 5s and 30s.
- Parameter Optimization: The optimal sliding window size (W) for driving state detection was found to be 10 seconds, while the best parameters for the SVR(PUK) model were optimized at ω = 2 and σ = 1.

## Limitations
- The system requires background sensing using multiple smartphone sensors, which presents an energy consumption challenge for mobile batteries.
- The model relies on collecting some high-fidelity, location-specific manual observations (ground truth data) to properly train the initial regression model for a new garage.
- Traffic jams immediately outside the parking garage can occasionally trigger false-positive "start-parking" arrivals, although the system attempts to mitigate this using a "give-up-parking" context cancelation.

## Relevance to our topic
For our project on "smart parking slot allocation in multi-floor buildings with motorcycle and car zones", this paper is highly relevant due to its Floor-Change Detector (FCD) module. The paper proves that a smartphone barometer can reliably track a vehicle's vertical movement up and down ramps (with an altitude variation slope of roughly 0.12mb/m). This allows tracking floor-level congestion and cruising times without installing hardware sensors on every floor of a multi-level garage.

## Possible improvement
To extend this methodology for a 90-slot multi-floor building (30 car + 60 motorbike):
- Vehicle-Type Classification: The Random Forest classifier could be trained to extract inertial features (like lean angles from the gyroscope or vibration patterns from the accelerometer) to autonomously distinguish whether the user is riding a motorcycle or driving a car, routing them to the correct 30/60 capacity zones automatically.
- Floor-Specific Routing: Instead of just recording time-in-cruising per floor, the barometer's floor-change data could be linked to an active allocation algorithm. If the system detects a motorcycle looping on floor 1 for more than 30 seconds without triggering a "parked" context, the app could dynamically reallocate and guide the rider to an empty slot on floor 2.
