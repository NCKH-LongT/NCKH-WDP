# Literature Review Matrix

## Ma tran tong hop 10 bai bao

| No | Paper Title | Authors | Year | Venue / Ranking | RQ | Method / Algorithm | Dataset | Key Metrics | Main Contribution | Limitation | Relevance |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P1 | A Multi-Agent System for Parking Allocation | Icarte-Ahumada et al. | 2025 | Electronics, MDPI (Scopus Q1, IF=2.6) | RQ1 | Multi-Agent System, Contract Net Protocol (CNP), Decommitment | Simulation | Allocation time, Slot utilization | Concurrent + Decommitment hieu qua nhat trong 4 co che phoi hop | Chi mo phong, chua test thuc te | Co so ly thuyet cho vehicle-type zoning |
| P2 | Optimal Parking Occupancy with Differentiated Parking | Jakob & Menendez | 2021 | Transportation Letters (Scopus Q2, IF=3.3) | RQ1 | Macroscopic Fundamental Diagram (MFD), Optimal Occupancy Computation | Macroscopic traffic model | Cruising delay, Occupancy rate | Occupancy >85% gay cruising; Differentiated parking cai thien hieu qua | Paywall, mo hinh vi mo chua xet hanh vi ca nhan | Nguyen ly phan tang theo loai xe, nguong 85% |
| P3 | Reducing Street Parking Search Time via Smart Assignment | Hemmatpour, Dogani & Laoutaris | 2025 | arXiv preprint (ACM) | RQ2 | Hungarian Algorithm (Kuhn-Munkres), Cord-Approx Strategy | Simulation, du lieu thuc Madrid | Search time (min), Reduction % | Giam 72% (67-76%) thoi gian tim cho; 6.69 vs 19.98 min | Preprint chua peer-review, chi street parking | Co so cho auto-assign, Hungarian matching |
| P4 | Optimal Parking Management of CAVs | Wang, Levin & Caverly | 2021 | TRC, Elsevier (Scopus Q1, IF=7.9) | RQ2, RQ3 | Lotka-Volterra model, Pontryagin's Minimum Principle (PMP) | Monte Carlo simulation | Parking availability, Demand distribution | Centralized vuot troi decentralized; Dynamic pricing can bang nhu cau | Yeu cau CAVs, dynamic pricing phuc tap | Nguyen ly centralized assignment, can bang tai |
| P5 | MCDM for Smart Parking: Health Criteria | Amari, Moussaid & Tallal | 2023 | Sustainability, MDPI (Scopus Q2, IF=3.3) | RQ3 | CRITIC weighting, TOPSIS, CODAS, EDAS, WASPAS | Case study minh hoa | Ranking consistency, Inter-item correlation SW | CRITIC tao trong so khach quan; Health criteria anh huong xep hang | Case study nho, chua real-time | Nen tang ly thuyet cho WSM, CRITIC auto-tuning |
| P6 | Cheetah Optimization Algorithm for Parking | Shirazi & Farzaneh | 2025 | JAIDM (Scopus-indexed) | RQ3 | COA (Cheetah Optimization Algorithm) | Benchmark simulation | Convergence speed, Solution quality | COA > GA + WOA ve toc do hoi tu va chat luong giai | Regional journal, chua so sanh voi DRL | Huong nang cap tuong lai cho WSM |
| P7 | Online Parking Assignment with Multi-Agent Deep RL | Zhang, Zhao, Liao et al. | 2022 | TRC, Elsevier (Scopus Q1, IF=7.9) | RQ3 | MARL (Multi-Agent Deep RL), Value Decomposition | Simulation (CVs + NCVs) | Assignment efficiency vs FCFS | Cai thien 15% hieu qua phan bo so voi FCFS | Yeu cau Connected Vehicles, training cost cao | Hard constraints (vehicleType match) ap dung vao WSM |
| P8 | Peak-Period Parking Demand Allocation | Zhang, Liu, Yan et al. | 2024 | Systems, MDPI (JCR Q1, IF=3.1) | RQ4 | NSGA-II, Delay Calculation Model | Field investigation + simulation, Nanjing hub | Average delay, Total delay reduction | Giam 4.5% delay (13,860s tiet kiem/gio) | Chi cluster ngoai troi, NSGA-II cost cao | Nguyen ly load balancing, threshold 85%, peak detection |
| P9 | Dynamic Coordinated Strategy for Mixed-Traffic Parking | Wang, Zhang, Xue et al. | 2024 | Electronic Research Archive, AIMS (SCIE, IF=1.1) | RQ4 | DCS, Parking-Cruising Path Tree (PCPT), Conflict Resolution | Simulation (HVs + AVs) | Cruising duration, Forced delay, Optimization rate | Toi uu len den 18% cruising duration | Chi mo phong, yeu cau sensor IoT | Huong nang cap DCS/PCPT cho load balancing real-time |
| P10 | Reservation and Allocation for Shared Parking under Uncertainty | Wang, Li & Xie | 2022 | TRC, Elsevier (Scopus Q1, IF=7.9) | RQ4 | Chance-Constrained Programming, Reservation-Aware Capacity | Stochastic model | Service rate, Effective occupancy | Tinh ca Reserved khi danh gia occupancy, tranh over-allocation | Paywall, mo hinh phuc tap | Reservation-Aware Capacity: effective = (occupied + reserved) / total |

---

## Phan bo theo Research Question

| RQ | Papers | Thuat toan chinh | Don gian hoa cho he thong |
|---|---|---|---|
| RQ1 - Phan tang theo loai phuong tien | P1, P2 | MAS + CNP, MFD + Differentiated Parking | Dynamic Vehicle-Type Zoning (rule-based) |
| RQ2 - Phan bo slot tu dong vs. tu do | P3, P4 | Hungarian Algorithm, PMP + Centralized | Greedy Matching (nearest-first) |
| RQ3 - Tieu chi uu tien phan bo (MCDM) | P5, P6, P7 | CRITIC/TOPSIS, COA, MARL | Weighted Scoring Model (WSM) |
| RQ4 - Cai thien ty le su dung gio cao diem | P8, P9, P10 | NSGA-II, DCS/PCPT, Chance-Constrained | Threshold-based Load Balancing |

---

## Phan bo theo nam

| Giai doan | Papers | So luong |
|---|---|---|
| 2021 | P2, P4 | 2 |
| 2022 | P7, P10 | 2 |
| 2023 | P5 | 1 |
| 2024 | P8, P9 | 2 |
| 2025 | P1, P3, P6 | 3 |

---

## Phan bo theo Ranking

| Ranking | Papers | So luong |
|---|---|---|
| Scopus Q1 | P4, P7, P10 | 3 |
| JCR Q1 | P8 | 1 |
| Scopus Q2 | P2, P5 | 2 |
| Scopus-indexed | P1, P6, P9 | 3 |
| Preprint | P3 | 1 |
