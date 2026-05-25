# Paper 03 Summary

## Citation
Tên bài: Smart Parking Guidance: A Step Towards Sustainable Cities
Tác giả: 
Năm: 
Nguồn: 
DOI/Link: 

## Problem
This paper addresses the mismatch between parking supply and demand in dense urban areas, which results in drivers spending excessive time cruising for vacant parking spaces. This inefficient searching process disrupts urban sustainability, as parking search traffic can account for up to 30% of total traffic flow during peak hours, thereby exacerbating road congestion, increasing energy consumption, and elevating carbon dioxide emissions.

## Method
The authors propose a smart parking guidance system based on a multi-agent architecture consisting of driver agents, parking agents, and a central agent. The system matches driver demands with local parking supply by utilizing a utility function (embedded in the MATSim simulator) that calculates the optimal assignment. The utility function mathematically weighs the marginal utility of travel time, walking time, driving distance, cruising time, and the monetary cost of parking to negotiate prices and automatically reserve vacant spaces for drivers.

## Dataset
The study used spatial and road network data from the Tunis city center covering a 10 km² area. The simulated dataset included a road network of 1,361 directed links and 584 nodes, alongside a parking supply of 346 on-street locations (4,250 spots) and 24 off-street lots (4,800 spots). The simulation randomly generated and routed up to 20,000 vehicles per day, primarily focusing on the morning peak period.

## Evaluation
The system was evaluated by comparing an "unguided environment" (baseline, free-choice search) against a "guided environment". The evaluation metrics included traffic conditions (number of vehicles in circulation, road congestion status), parking occupancy rates, parking managers' financial turnover, total travel distance, walking time to the final destination, social well-being (total driver utility), and environmental costs (average energy consumption and CO2 emissions).

## Results
- Traffic & Search Reduction: Guiding drivers reduced the number of vehicles in circulation actively searching for parking by 15.51%.
- Congestion & Distance: Road congestion dropped by 11.92%, and total travel distance was reduced by 450 km (from 3,650 km to 3,200 km).
- Emissions & Energy: Both energy consumption and CO2 emissions were reduced by 12.32%.
- Parking Operations: Overall parking occupancy rates were optimized to 28.38%, and parking managers' turnover (revenue) increased by 29.29% (from 23,857 TND to 33,741 TND).
- Trade-off: Average walking time slightly increased from 12.14 minutes to 13 minutes, as the system occasionally routed drivers to emptier, more distant lots to balance overall capacity.

## Limitations
- The system relies entirely on MATSim software simulations and lacks empirical, real-world field validation to confirm the calculated search-time and emission reductions.
- The model assumes "perfect information" (all drivers have real-time access to accurate parking data) and a homogeneous "value of time" for all users, which does not accurately reflect real-world driver heterogeneity.
- The simulation treats all vehicles homogeneously and does not account for the differing dimensions, maneuverability, or spatial requirements of mixed vehicle types (e.g., cars vs. motorcycles).

## Relevance to our topic
For our project on "smart parking slot allocation in multi-floor buildings with motorcycle and car zones", this paper offers a foundational multi-agent architecture and a highly applicable utility function framework. The mathematical approach of weighing driving distance, walking distance, and parking duration to maximize utility can be adapted to rank the desirability of specific floors or zones inside a multi-level structure.

## Possible improvement
To extend this model for a 90-slot multi-floor building (30 cars + 60 motorbikes), the multi-agent system must be upgraded to classify "driver agents" by vehicle type (car or motorcycle) to strictly restrict them from reserving slots in incompatible zones. Additionally, the utility function must be modified to account for vertical travel constraints—specifically calculating the vehicle driving time up/down garage ramps and the pedestrian walking time up/down stairwells or elevators—rather than relying solely on flat, horizontal geographic distances.
