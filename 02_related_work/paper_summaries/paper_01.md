# Paper 01 Summary

## Citation
Tên bài: Constraint Optimization Model for Dynamic Parking Space Allocation
Tác giả: 
Năm: 2024
Nguồn: 
DOI/Link: 

## Problem
This paper addresses the inefficient utilization of existing parking resources caused by rigid, static parking slot assignments. Specifically, it tackles the inability of current management systems to dynamically adapt to daily variables such as employee absenteeism, fluctuating visitor numbers, working schedules (shifts), and hierarchical user priorities.

## Method
The paper proposes a constraint optimization model formulated with first-order logic and solved using an ad hoc dynamic constraint search algorithm. The algorithm defines variables for users (employees/visitors), scheduled shifts, parking areas (Zones A, B, C), and priority levels. It dynamically allocates slots by evaluating strict constraints—for instance, current shift workers are given higher priority than off-shift workers, and employees have higher priority than visitors. The algorithm uses a backtracking mechanism to reject and reassign slots if an assignment violates any organizational rules or if a slot is already occupied.

## Dataset
The researchers primarily used a simulated experimental testbed featuring three parking areas (Area A, B, and C) containing 5 slots each, testing it across multiple shift scenarios involving up to 21 employees and 13 visitors. Additionally, the authors validated the model using a practical open-source car parking dataset from data.gov.uk, allocating spaces for 11 employees and 3 visitors for a specific shift.

## Evaluation
The proposed model was evaluated against 22 related parking optimization studies using a qualitative benchmark consisting of 7 metrics: dynamic allocation, flexible parking spaces, average waiting time, average distance, confusion (incorrect slot assignments), time to full capacity utilization, and priority assignment.

## Results
The key quantitative result is that the proposed model is the only system out of the 22 benchmarked baseline studies to satisfy 100% (7 out of 7) of the evaluated parameters. In its scenario implementations, the algorithm successfully allocated high-priority drivers to the premium zone (Area A), automatically cascading medium and low-priority drivers to Areas B and C without any logical conflicts.

## Limitations
- The paper lacks quantitative measurements for its benchmark metrics, offering only qualitative pass/fail validations instead of exact numerical reductions in waiting time, search time, or physical distance.
- It does not account for physical space dimensions or different vehicle types (e.g., passenger cars vs. two-wheelers).
- It does not model vertical multi-floor layouts, limiting its spatial routing to simple flat zones.

## Relevance to our topic
For our project on "smart parking slot allocation in multi-floor buildings with motorcycle and car zones," this paper provides a robust mathematical framework for handling administrative logic. Its first-order logic constraints can be adopted to ensure that specific user types (e.g., staff vs. students) are strictly assigned to designated zones, successfully managing booking overlaps and establishing user hierarchies before physical routing begins.

## Possible improvement
To adapt this model for a 90-slot multi-floor building (30 car + 60 motorbike), the algorithm must be extended to include "vehicle type" (car/motorcycle) and "floor level" (1, 2, 3) as strict domain variables to guarantee motorcycles are never assigned to car slots. Furthermore, the objective function should be upgraded to calculate actual vertical traversal times (driving up ramps/walking down stairs) instead of just using arbitrary zones, and the evaluation phase should measure exact percentage increases in capacity utilization rather than just logical constraint satisfaction.
