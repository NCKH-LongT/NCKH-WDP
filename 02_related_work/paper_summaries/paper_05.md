# Paper 05 Summary

## Citation
Tên bài: Study of Parking Patterns for Different Parking Facilities
Tác giả: 
Năm: 
Nguồn: 
DOI/Link: 

## Problem
This paper addresses the growing issue of inadequate parking facilities driven by increasing population and vehicle usage. It specifically focuses on the need to study and understand varying parking patterns and demands across different facilities to prevent chaotic traffic conditions and the misuse of parking spaces.

## Method
The method involves counting different types of vehicles (cycles, two-wheelers, four-wheelers) and mathematically converting them into a standardized unit called the Passenger Car Unit (PCU) using factors provided by the Indian Road Congress (e.g., 0.5 for motorcycles, 1.0 for cars). The author then applies a statistical Student's t-test at an 8% significance level (where t-critical = 2.306004) to compare the mean PCU values between different parking locations to determine if their parking patterns significantly differ.

## Dataset
The dataset consists of manual vehicle counts collected from three major parking sites inside the Lovely Professional University campus in Punjab, India: Main Parking, Eastern Gate Parking, and Southern Gate Parking. The data was recorded in 15-minute intervals during the morning peak college start hours (8:00 AM to 10:00 AM) on working days.

## Evaluation
The primary evaluation metric was the t-statistic (t-stat) calculated from the PCU data of the different parking lots. This t-stat was compared against the t-critical value (2.306004) to test the hypothesis of whether the parking patterns (demand and capacity utilization) between two different facilities were statistically different or the same.

## Results
- Quantitative: The t-test results revealed that the Main Parking and Southern Gate had similar parking patterns (t-stat = 0.795, which is < 2.306). However, the Eastern Gate significantly differed from both the Southern Gate (t-stat = 3.223) and the Main Parking (t-stat = 3.782).
- Qualitative: The study concluded that mixing different vehicle types without proper physical alignment or spacing leads to the severe misuse of parking capacity.

## Limitations
- The study relies on a very small and limited dataset, observing only a 2-hour window (yielding just 8 data points per site) on an unspecified number of working days.
- It uses a basic statistical t-test for time-series data, which assumes normal distribution and independent samples, and does not propose an actual algorithm or software model to solve the problem.
- The findings are strictly observational and only offer qualitative recommendations (e.g., "there should be proper alignment") rather than quantitative solutions.

## Relevance to our topic
For our project focusing on "smart parking slot allocation in multi-floor buildings with motorcycle and car zones," this paper establishes the fundamental mathematical baseline that cars and motorcycles have different spatial requirements (1.0 PCU vs. 0.5 PCU). It empirically proves that failing to physically segment or align these different vehicle types leads directly to the misuse of parking capacity, strongly supporting our project's premise of creating dedicated motorcycle and car zones.

## Possible improvement
To adapt this study's findings for a multi-floor parking building with 90 slots (30 cars + 60 motorbikes), the static PCU normalization could be integrated into a real-time tracking algorithm. Instead of merely observing that mixed vehicles cause space misuse, our system could actively route two-wheelers and four-wheelers to their respective segmented floors/zones to physically enforce the "proper alignment" recommended by the author. Furthermore, the system could dynamically calculate the facility's total PCU load in real-time, rather than relying on manual 15-minute interval counts.
