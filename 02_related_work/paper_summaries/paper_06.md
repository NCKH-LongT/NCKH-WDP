# Paper 06 Summary

## Citation
Tên bài: Optimization Model of Parking Space Allocation Based on Genetic Algorithm in Reservation System Mode
Tác giả: 
Năm: 
Nguồn: 
DOI/Link: 

## Problem
This paper addresses the severe shortage and ineffective allocation of parking resources caused by surging vehicle ownership and the rise of new energy vehicles. Specifically, it tackles the conflict in mixed parking lots (ordinary vs. EV charging spaces) by establishing an optimal reservation-based allocation system to prevent the chaotic "ineffective traffic flow" of drivers searching for spaces, while aiming to maximize the parking lot operator's total revenue.

## Method
The authors propose a mixed-integer programming model aimed at maximizing combined profit (calculated from ordinary parking fees, charging parking fees, and charging costs). To solve the NP-hard allocation problem, they design a Genetic Algorithm (GA). The GA uses a unique two-dimensional encoding method mapping "order number to parking number" to avoid the limitations of binary coding. The population initialization filters out impossible assignments by checking order time-window conflict matrices. It then applies roulette wheel selection to favor high-profit chromosomes, followed by crossover and single-point mutation operations to iteratively find the optimal allocation that avoids overlapping time windows.

## Dataset
The study uses software-simulated data tested in MATLAB across four distinct capacity scales representing oversaturated demand scenarios. The simulated sizes (spaces vs. orders) were: 5 spaces for 25 orders, 10 spaces for 50 orders, 14 spaces for 100 orders, and 18 spaces for 200 orders. Financial parameters were set as: ordinary parking at 10 yuan/h, charging spaces at 15 yuan/h, and charging costs configured internally. The GA was configured with an initial population size of 100 and a maximum of 500 iterations.

## Evaluation
The model was evaluated by comparing the proposed reservation system mode against a traditional non-appointment (first-come, first-served) mode. The primary evaluation metrics were Maximum profit (total monetary revenue generated), Profit improvement rate (percentage increase in revenue), and Order allocation lift rate (percentage increase in the total number of successfully parked vehicles/utilization).

## Results
- Utilization: Order allocation rates improved by an average of 17%, meaning the lot successfully packed in substantially more vehicles within the 24-hour window.
- Revenue: Total profits increased by an average of 30%. In the largest simulated scenario (18 spaces handling 200 orders), the reservation system increased profit from 5,020 yuan to 6,590 yuan—a direct profit improvement of 31.27%.

## Limitations
- Unrealistic User Assumptions: The model mathematically assumes that users are perfectly punctual, will never temporarily cancel appointments, and that their exact parking duration is known precisely in advance.
- Simplified EV Constraints: It assumes that charging time perfectly equals parking time and completely ignores the power limits of the parking lot's electrical grid.
- Lack of Spatial Dynamics: The model optimizes solely based on temporal overlaps (time windows) and ignores physical routing dynamics, meaning it does not factor in walking distance or the time it takes to drive to the assigned slot.

## Relevance to our topic
For our project concerning "smart parking slot allocation in multi-floor buildings with motorcycle and car zones", this paper offers an excellent mathematical foundation for handling advance reservations and time-window overlaps. If the garage allows users to book spots ahead of time, we can adopt their conflict matrix constraints to ensure maximum daily turnover. Their 2D genetic algorithm encoding can also be adapted to assign requests not just to "ordinary/EV" slots, but specifically to "motorcycle/car" slots.

## Possible improvement
To adapt this model for a 90-slot multi-floor building (30 cars + 60 motorbikes), the algorithm needs three major extensions:
1. Strict Class Constraints: The objective function must add vehicle-type constraints to guarantee that a car demand variable is never assigned to the motorbike slot matrix (and vice versa).
2. Spatial Penalty Weighting: The fitness function should be expanded to include physical routing costs (e.g., penalizing assignments that send drivers to the top floor if lower floors are empty), rather than just optimizing for hourly flat-rate profit.
3. Buffer Times: The time-window constraints should incorporate a 10-15 minute "buffer" parameter to account for real-world driver unpunctuality, replacing the paper's unrealistic assumption of perfect arrival times.
