# Literature Review Matrix

## Ma trận tổng hợp 10 bài báo

| No | Paper Title | Authors | Year | Venue / Ranking | RQ | Method / Algorithm | Dataset | Key Metrics | Main Contribution | Limitation | Relevance |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P1 | A Multi-Agent System for Parking Allocation | Icarte-Ahumada et al. | 2025 | Electronics, MDPI (Scopus Q1, IF=2.6) | RQ1 | Multi-Agent System, Contract Net Protocol (CNP), Decommitment | Mô phỏng | Thời gian phân bổ, Tỷ lệ sử dụng slot | Concurrent + Decommitment hiệu quả nhất trong 4 cơ chế phối hợp | Chỉ mô phỏng, chưa test thực tế | Cơ sở lý thuyết cho vehicle-type zoning |
| P2 | Optimal Parking Occupancy with Differentiated Parking | Jakob & Menendez | 2021 | Transportation Letters (Scopus Q2, IF=3.3) | RQ1 | Macroscopic Fundamental Diagram (MFD), Optimal Occupancy Computation | Mô hình giao thông vĩ mô | Cruising delay, Tỷ lệ lấp đầy | Occupancy >85% gây cruising; Differentiated parking cải thiện hiệu quả | Paywall, mô hình vĩ mô chưa xét hành vi cá nhân | Nguyên lý phân tầng theo loại xe, ngưỡng 85% |
| P3 | Reducing Street Parking Search Time via Smart Assignment | Hemmatpour, Dogani & Laoutaris | 2025 | arXiv preprint (ACM) | RQ2 | Hungarian Algorithm (Kuhn-Munkres), Cord-Approx Strategy | Mô phỏng, dữ liệu thực Madrid | Thời gian tìm chỗ (phút), Tỷ lệ giảm % | Giảm 72% (67-76%) thời gian tìm chỗ; 6.69 vs 19.98 phút | Preprint chưa peer-review, chỉ street parking | Cơ sở cho auto-assign, Hungarian matching |
| P4 | Optimal Parking Management of CAVs | Wang, Levin & Caverly | 2021 | TRC, Elsevier (Scopus Q1, IF=7.9) | RQ2, RQ3 | Lotka-Volterra model, Pontryagin's Minimum Principle (PMP) | Mô phỏng Monte Carlo | Parking availability, Phân bổ nhu cầu | Centralized vượt trội decentralized; Dynamic pricing cân bằng nhu cầu | Yêu cầu CAVs, dynamic pricing phức tạp | Nguyên lý centralized assignment, cân bằng tải |
| P5 | MCDM for Smart Parking: Health Criteria | Amari, Moussaid & Tallal | 2023 | Sustainability, MDPI (Scopus Q2, IF=3.3) | RQ3 | CRITIC weighting, TOPSIS, CODAS, EDAS, WASPAS | Case study minh họa | Tính nhất quán xếp hạng, Inter-item correlation SW | CRITIC tạo trọng số khách quan; Health criteria ảnh hưởng xếp hạng | Case study nhỏ, chưa real-time | Nền tảng lý thuyết cho WSM, CRITIC auto-tuning |
| P6 | Cheetah Optimization Algorithm for Parking | Shirazi & Farzaneh | 2025 | JAIDM (Scopus-indexed) | RQ3 | COA (Cheetah Optimization Algorithm) | Benchmark mô phỏng | Tốc độ hội tụ, Chất lượng giải | COA > GA + WOA về tốc độ hội tụ và chất lượng giải | Regional journal, chưa so sánh với DRL | Hướng nâng cấp tương lai cho WSM |
| P7 | Online Parking Assignment with Multi-Agent Deep RL | Zhang, Zhao, Liao et al. | 2022 | TRC, Elsevier (Scopus Q1, IF=7.9) | RQ3 | MARL (Multi-Agent Deep RL), Value Decomposition | Mô phỏng (CVs + NCVs) | Hiệu quả phân bổ so với FCFS | Cải thiện 15% hiệu quả phân bổ so với FCFS | Yêu cầu Connected Vehicles, chi phí training cao | Hard constraints (vehicleType match) áp dụng vào WSM |
| P8 | Peak-Period Parking Demand Allocation | Zhang, Liu, Yan et al. | 2024 | Systems, MDPI (JCR Q1, IF=3.1) | RQ4 | NSGA-II, Delay Calculation Model | Khảo sát thực địa + mô phỏng, hub Nanjing | Delay trung bình, Tổng delay tiết kiệm | Giảm 4.5% delay (13,860 giây tiết kiệm/giờ) | Chỉ cluster ngoài trời, NSGA-II chi phí tính toán cao | Nguyên lý load balancing, ngưỡng 85%, peak detection |
| P9 | Dynamic Coordinated Strategy for Mixed-Traffic Parking | Wang, Zhang, Xue et al. | 2024 | Electronic Research Archive, AIMS (SCIE, IF=1.1) | RQ4 | DCS, Parking-Cruising Path Tree (PCPT), Conflict Resolution | Mô phỏng (HVs + AVs) | Cruising duration, Forced delay, Tỷ lệ tối ưu | Tối ưu lên đến 18% cruising duration | Chỉ mô phỏng, yêu cầu sensor IoT | Hướng nâng cấp DCS/PCPT cho load balancing real-time |
| P10 | Reservation and Allocation for Shared Parking under Uncertainty | Wang, Li & Xie | 2022 | TRC, Elsevier (Scopus Q1, IF=7.9) | RQ4 | Chance-Constrained Programming, Reservation-Aware Capacity | Mô hình ngẫu nhiên | Tỷ lệ phục vụ, Effective occupancy | Tính cả Reserved khi đánh giá occupancy, tránh over-allocation | Paywall, mô hình phức tạp | Reservation-Aware Capacity: effective = (occupied + reserved) / total |

---

## Phân bổ theo Research Question

| RQ | Papers | Thuật toán chính | Đơn giản hóa cho hệ thống |
|---|---|---|---|
| RQ1 - Phân tầng theo loại phương tiện | P1, P2 | MAS + CNP, MFD + Differentiated Parking | Dynamic Vehicle-Type Zoning (rule-based) |
| RQ2 - Phân bổ slot tự động vs. tự do | P3, P4 | Hungarian Algorithm, PMP + Centralized | Greedy Matching (nearest-first) |
| RQ3 - Tiêu chí ưu tiên phân bổ (MCDM) | P5, P6, P7 | CRITIC/TOPSIS, COA, MARL | Weighted Scoring Model (WSM) |
| RQ4 - Cải thiện tỷ lệ sử dụng giờ cao điểm | P8, P9, P10 | NSGA-II, DCS/PCPT, Chance-Constrained | Threshold-based Load Balancing |

---

## Phân bổ theo năm

| Giai đoạn | Papers | Số lượng |
|---|---|---|
| 2021 | P2, P4 | 2 |
| 2022 | P7, P10 | 2 |
| 2023 | P5 | 1 |
| 2024 | P8, P9 | 2 |
| 2025 | P1, P3, P6 | 3 |

---

## Phân bổ theo Ranking

| Ranking | Papers | Số lượng |
|---|---|---|
| Scopus Q1 | P4, P7, P10 | 3 |
| JCR Q1 | P8 | 1 |
| Scopus Q2 | P2, P5 | 2 |
| Scopus-indexed | P1, P6, P9 | 3 |
| Preprint | P3 | 1 |
