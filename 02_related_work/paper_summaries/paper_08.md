# Paper 08 Summary

## Citation
Tên bài: Planning Campus Parking Facilities Using Parking Demand Analysis
Tác giả: 
Năm: 2024
Nguồn: ResearchGate
DOI/Link: 

## Problem
This paper addresses the severe lack of adequate parking space and the resulting chaotic vehicle arrangement on the Manado State Polytechnic (MSP) campus. Due to poor initial physical planning and an increasing number of students, the campus is facing a critical space competition between facilities, leading to a parking crisis where the volume of vehicles heavily exceeds the physical capacity of the current surface lots.

## Method
The methodology relies on observational surveys and mathematical capacity calculations. The authors use questionnaires to count the number of active vehicle users and compare this demand against the available land area. They calculate standard parking characteristics—including Parking Accumulation, Parking Duration, Parking Volume, and Parking Index (the percentage of parked vehicles to available spaces). Capacity needs are determined by multiplying the vehicle volume by the required Parking Space Unit (SRP), which is defined as 11.5 m² (2.30m x 5.0m) for a passenger car and 1.5 m² (0.75m x 2.0m) for a motorcycle.

## Dataset
Data was collected on the MSP campus from August to September 2023. The population dataset included 5,570 total campus residents (5,093 students, 312 lecturers, and 165 employees). The survey identified 346 cars and 1,974 motorcycles used daily. The physical dataset consisted of the existing available campus land: 2,385.18 m² for car parking and 935.137 m² for motorcycle parking.

## Evaluation
The primary evaluation metrics used to assess the campus parking situation were the Parking Duration (average time spent parked), the Parking Index (percentage indicating how much capacity is filled), and the Parking Needs vs. Available Area (calculating the physical deficit in square meters).

## Results
- Car Parking: The average duration was 8 hours with a deeply underutilized Parking Index of 14.51%. However, serving all 346 cars requires 3,979 m² of space, which exceeds the available 2,385.18 m², meaning it does not meet the total spatial needs.
- Motorcycle Parking: The average duration was 8 hours with a severely over-capacitated Parking Index of 150.24%. Serving 1,974 motorcycles requires 2,961 m² of space, but only 935.137 m² is available, causing massive overflow.

## Limitations
- The study relies on basic static formulas and manual questionnaire surveys rather than continuous, real-time sensing data to measure daily fluctuations.
- It is strictly an observational case study; while it conceptually recommends "smart parking technology" and "multi-level parking," it does not propose, simulate, or test an actual allocation algorithm or architectural design to solve the problem.

## Relevance to our topic
For our project on "smart parking slot allocation in multi-floor buildings with motorcycle and car zones," this paper provides excellent baseline evidence for why strict zoning based on vehicle type is absolutely necessary. It quantitatively proves that cars and motorcycles have vastly different spatial requirements (11.5 m² vs 1.5 m²). Furthermore, it highlights what happens when zones are not properly balanced dynamically: car zones may sit underutilized (14.51% index) while motorcycle zones become extremely congested (150.24% index).

## Possible improvement
To adapt these findings for our 90-slot multi-floor building (30 cars + 60 motorbikes), the static SRP calculations (11.5 m² and 1.5 m²) should be used to physically blueprint the floor layouts. However, instead of relying on static surveys, we should implement the "smart parking technology" the authors recommended. By adding real-time sensors and an allocation algorithm, the system could actively monitor the Parking Index of the 60 motorcycle slots and 30 car slots, preventing the 150%+ overcapacity bottlenecks observed in this paper by refusing entry or re-routing users when a specific vehicle zone hits 100% utilization.
