# Literature Review - Paper List

## Summary
Total papers reviewed: 9

## Paper List

| No | Title | Year | Source | Main Topic | Method | Relevance to RQ |
|---|---|---|---|---|---|---|
| 1 | Constraint Optimization Model for Dynamic Parking Space Allocation | 2024 | MDPI | Dynamic slot allocation with priority constraints | First-order logic + backtracking | RQ3 |
| 2 | ParkGauge: Gauging the Occupancy of Parking Garages with Crowdsensed Parking Characteristics | 2016 | NTU | Infrastructure-free occupancy sensing | Random Forest + HMM + SVR | RQ1 |
| 3 | Smart Parking Guidance: A Step Towards Sustainable Cities | 2022 | IJSRP | Urban parking guidance system | Multi-agent + utility function (MATSim) | RQ2, RQ4 |
| 4 | Entropy-Based Dynamic Programming for Efficient Vehicle Parking | 2024 | arXiv | Optimal floor selection in multi-story garage | Entropy model + Dynamic Programming | RQ2, RQ3 |
| 5 | Study of Parking Patterns for Different Parking Facilities | 2015 | International Journal of Civil and Structural Engineering Research | Vehicle type impact on parking capacity | PCU conversion + t-test | RQ1 |
| 6 | Optimization Model of Parking Space Allocation Based on Genetic Algorithm | 2022 | FIEM 2022 | Reservation-based allocation optimization | Genetic Algorithm (2D encoding) | RQ4 |
| 7 | Parking Reservation Techniques: A Review of Research Topics, Considerations, and Optimization Methods | 2023 | ScienceDirect | Systematic review of reservation systems | Literature review (99 papers) | RQ1, RQ4 |
| 8 | Planning Campus Parking Facilities Using Parking Demand Analysis | 2024 | ResearchGate | Campus parking demand vs capacity | Survey + Parking Index calculation | RQ1 |
| 9 | Motorcycle Drivers' Parking Lot Choice Behaviors in Developing Countries: Analysis for Ho Chi Minh City, Vietnam | 2019 | MDPI | Motorcycle parking behavior in Vietnam | Stated Preference + Mixed Logit | RQ1, RQ2 |

## Grouped by Research Question

### RQ1: Việc phân tầng, khu vực theo loại phương tiện ảnh hưởng thế nào đến hiệu quả sử dụng chỗ đỗ?
- Paper 5 — PCU difference (0.5 vs 1.0), mixed = capacity misuse
- Paper 8 — Car index 14.51% vs motorcycle 150.24%
- Paper 9 — Motorcycle search behavior tại Vietnam
- Paper 7 — Xác nhận gap: chưa ai làm reservation phân biệt two-wheeler/four-wheeler

### RQ2: Phân bổ slot tự động có giúp giảm thời gian tìm chỗ so với cách chọn chỗ tự do không?
- Paper 3 — Guided giảm 15.51% search traffic so với unguided
- Paper 4 — DP giảm cumulative parking time vs free-choice
- Paper 9 — 3.3 min average search time (motorcycle, HCM)

### RQ3: Nên ưu tiên tiêu chí nào khi phân bổ slot: khoảng cách, tầng, loại xe, thời gian gửi hay tỷ lệ lấp đầy slot đỗ các tầng, các khu vực?
- Paper 1 — Priority + zone + shift constraints
- Paper 3 — Utility function: distance + walking + cost
- Paper 4 — Floor occupancy probability + vertical travel time
- Paper 6 — Time-window + revenue maximization

### RQ4: Thuật toán phân bổ slot có thể cải thiện tỷ lệ sử dụng bãi xe trong giờ cao điểm?
- Paper 3 — Peak morning optimized, revenue +29%
- Paper 4 — Outperforms baseline under high congestion
- Paper 6 — GA: +17% allocation rate
- Paper 7 — Reservation smooths peak demand

## Key Research Gap

Từ 9 papers: chưa có nghiên cứu nào kết hợp đồng thời:
1. Multi-floor building (vertical routing)
2. Mixed vehicle types — motorcycle + car (zone separation)
3. Automated allocation algorithm + reservation system
4. Vietnam context (motorcycle-dominated)

→ Đây là contribution của nhóm.
