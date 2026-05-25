# Paper 07 Summary

## Citation
Tên bài: Parking Reservation Techniques: A Review of Research Topics, Considerations, and Optimization Methods
Tác giả: 
Năm: 2023
Nguồn: ScienceDirect
DOI/Link: 

## Problem
This paper addresses the severe urban traffic and environmental problems caused by the mismatch between growing private vehicle usage and limited parking resources. Specifically, it tackles the issue of "cruising for parking," noting that up to 30% of urban traffic consists of drivers spending an average of 8.1 minutes searching for spaces. Because a comprehensive scoping review of smart parking reservation techniques is currently lacking, this paper aims to provide a consolidated review of the literature.

## Method
Rather than proposing a new mathematical algorithm, this paper conducts a systematic literature review. The authors searched the Web of Science database for studies published between January 2000 and December 2022 using keywords like "parking reservation" and "parking allocation". They then screened and categorized the literature into four main research themes: inventory control, allocation decisions, pricing strategies, and performance evaluation.

## Dataset
The dataset consists of academic literature. The initial Web of Science search identified 438 publications. After title, abstract, and full-text screening, the final dataset used for in-depth analysis comprised 99 selected studies.

## Evaluation
The paper evaluated the selected studies based on the optimization methods they used (e.g., Binary/Mixed-Integer Linear Programming, Deep Reinforcement Learning, Bi-level planning, Agent-based simulations) and their evaluation metrics. The metrics were categorized into four perspectives: driver (e.g., search time, walking distance, acceptance rate), operator (e.g., resource utilization rate, total revenue), system (e.g., social welfare, service failure rate), and environment (e.g., CO2 emission reductions).

## Results
- Quantitative: Synthesized findings from performance evaluations show that implementing parking reservations can yield a statistically significant reduction of up to 3% in total travel time compared to scenarios without reservations.
- Qualitative: For inventory control, the review found that a combination of reserved and non-reserved (walk-in) spaces smooths peak demand much better than 100% complete parking reservations when supply is slightly scarce. For allocations, it identified that modern models are shifting from static assignments to periodic dynamic approaches that incorporate unpunctuality constraints.

## Limitations
- The authors acknowledge that the review only summarizes popular new research and cannot address all niche aspects of parking reservations due to their own limited scope of knowledge.
- It identifies a major limitation in the underlying literature: current reservation models assume 100% driver compliance. They ignore the unpredictable behaviors of real drivers (non-compliance) and the resulting financial costs required for parking enforcement.

## Relevance to our topic
This paper is highly relevant to our "smart parking slot allocation in multi-floor buildings with motorcycle and car zones" project because it explicitly identifies our exact topic as a gap for future research. Under the "Inventory Control" future directions, the authors specifically state that dividing parking supply based on the "type of vehicle", explicitly mentioning "two-wheeler or four-wheeler", is a highly valuable step to effectively reserving appropriate slots and using space efficiently.

## Possible improvement
To extend the findings of this review to our 90-slot multi-floor building (30 cars + 60 motorbikes), we should implement two advanced concepts highlighted in the paper:
- Mixed Inventory Control: Instead of making all 90 slots 100% reservation-only, allocate a specific ratio (e.g., 80% reserved, 20% walk-in) for the 60 motorbike slots to accommodate the highly spontaneous nature of motorcycle trips, which smooths out peak demand.
- Unpunctuality Time Windows (PUDW): Because drivers rarely arrive exactly on time, the allocation algorithm should incorporate stochastic buffer times to handle early/late arrivals and departures, preventing cascading service failures when a car driver overstays their reservation.
