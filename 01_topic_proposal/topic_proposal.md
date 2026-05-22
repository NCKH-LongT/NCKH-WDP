# Topic Proposal

## 1. Group Information

- Class: SE1822
- Group: G05
- Leader: Nguyễn Chí Bảo
- Members: Nguyễn Thị Yến Nhi, Trần Minh Kiệt, Thái Minh Tuấn, Nguyễn Vũ Len

## 2. Proposed Title

English title: AI-Enhanced Slot Allocation for Multi-Story Parking Building Management Systems

Vietnamese title: Phân bổ chỗ đỗ xe tăng cường AI cho hệ thống quản lý tòa nhà gửi xe nhiều tầng

## 3. Application Domain

Smart Parking, Transportation Management, Resource Allocation Optimization, Applied AI.

## 4. Problem Statement

Tại các đô thị lớn, nhu cầu gửi xe tăng cao trong khi diện tích đỗ xe bị giới hạn. Tòa nhà gửi xe nhiều tầng là công trình chuyên dùng để tiếp nhận, lưu giữ và tổ chức xe ra/vào theo nhiều tầng hoặc khu vực đỗ khác nhau. Với lưu lượng xe ra vào liên tục, việc phân bổ chỗ đỗ thủ công dẫn đến nhiều vấn đề:

- Xe mất nhiều thời gian tìm chỗ trống (cruising for parking), gây tắc nghẽn nội bộ.
- Một số tầng/khu vực quá tải trong khi tầng khác vẫn trống, gây lãng phí tài nguyên.
- Trong giờ cao điểm, tỷ lệ xe bị từ chối cao do thông tin không realtime và thiếu cơ chế cân bằng tải.
- Nhân viên bãi xe (Staff) mất thời gian hướng dẫn xe vào đúng khu vực phù hợp.

Cần có hệ thống phần mềm tích hợp thuật toán tối ưu hóa và mô hình AI để phân bổ slot tự động, dự đoán nhu cầu, cân bằng tải giữa các tầng và cải thiện hiệu quả sử dụng bãi xe.

## 5. Motivation

- Hiện tượng "cruising for parking" chiếm tới 30% lưu lượng giao thông tại một số khu vực đô thị (nghiên cứu từ Cornell University, Boston University).
- Các hệ thống quản lý bãi xe truyền thống chủ yếu tập trung vào CRUD (quản lý slot, session, tính phí) mà thiếu thuật toán tối ưu hóa phân bổ tài nguyên.
- Nghiên cứu cho thấy hệ thống phân bổ slot tự động (coordinated assignment) có thể giảm thời gian tìm chỗ từ 67% đến 76% so với hệ thống tự do (uncoordinated/free-choice).
- Bài toán phân bổ slot là bài toán Multi-Criteria Decision Making (MCDM) — tối ưu đa tiêu chí, phù hợp để nghiên cứu và đánh giá trong bối cảnh ứng dụng thực tế.

## 6. Target Users

| Actor | Vai trò | Nền tảng |
|---|---|---|
| System Administrator | Quản trị hệ thống, phân quyền RBAC | Web (React) |
| Parking Facility Manager | Quản lý tòa nhà, tầng, slot, bảng giá, báo cáo | Web (React) |
| Parking Staff | Xử lý xe vào/ra, tạo session, thu phí, xử lý ngoại lệ | Web / Tablet (React) |
| Parking User / Driver | Xem bãi xe, đặt chỗ, theo dõi lượt gửi, thanh toán | Mobile (React Native) |

## 7. Proposed AI Model / Method

Nghiên cứu kết hợp **thuật toán tối ưu hóa** (optimization algorithms) với **mô hình AI dự đoán** (predictive AI models) để xây dựng hệ thống phân bổ slot thông minh:

### 7.1. Thuật toán tối ưu hóa (Optimization Algorithms)

| Thuật toán | Nguồn gốc | Phiên bản áp dụng | RQ |
|---|---|---|---|
| Macroscopic Fundamental Diagram (MFD) | Jakob & Menendez 2021 | Dynamic Vehicle-Type Zone Differentiation | RQ1 |
| Hungarian Algorithm (Kuhn-Munkres) | arXiv 2025 + Wang 2021 | Greedy Optimal Matching O(n log n) | RQ2 |
| TOPSIS + CRITIC Weighting | Amari et al. 2023 | Weighted Scoring Model (WSM) 4 tiêu chí | RQ3 |
| NSGA-II Multi-Objective | Zhang 2024 + Wang 2022 | Threshold-based Load Balancing + Reservation-Aware Capacity | RQ4 |

### 7.2. Mô hình AI dự đoán (Predictive AI Models)

| AI Model | Input | Output | Thay thế cho | Kỹ thuật |
|---|---|---|---|---|
| **Peak Hour Prediction** | Giờ, thứ trong tuần, tháng, dữ liệu lịch sử check-in | Xác suất giờ cao điểm (0–1) | Rule-based: `rate > avg × 1.5` | Random Forest / Gradient Boosting |
| **Parking Duration Prediction** | Loại xe, giờ vào, thứ trong tuần, khu vực | Thời gian gửi dự kiến (phút) | Staff tự ước lượng | Linear Regression / Random Forest |

**Vai trò AI trong pipeline:**
- Peak Hour Prediction cung cấp đầu vào cho Load Balancer (RQ4) — kích hoạt cân bằng tải sớm hơn, chính xác hơn so với threshold cứng.
- Parking Duration Prediction cung cấp đầu vào cho WSM Scoring (RQ3) — trọng số W3 (duration match) dựa trên dự đoán thay vì giả định.

### 7.3. Pipeline tích hợp

```
 Xe vào bãi
  → [1] Zone Filter (RQ1) — vehicleType match + slot available
  → [2] AI: Peak Hour Prediction → isPeakHour?
      ├── Peak + floor >= 85% → Load Balancer (RQ4)
      └── Normal → AI: Duration Prediction → WSM Scoring (RQ3)
  → [3] Greedy Match (RQ2) — bestSlot = highest score
  → Slot Assigned (auto / manual mode for A/B testing)
```

## 8. System Features

Các chức năng chính của hệ thống:

**Chức năng quản lý (Manager):**
1. Quản lý thông tin tòa nhà gửi xe (CRUD)
2. Quản lý loại phương tiện (xe máy, ô tô, xe đạp, xe điện…)
3. Quản lý phân tầng theo loại xe
4. Quản lý slot đỗ xe và trạng thái slot (Available, Occupied, Reserved, Maintenance, Locked)
5. Quản lý bảng giá, chính sách tính phí
6. Xem báo cáo doanh thu, lượt xe, tỷ lệ lấp đầy, khung giờ cao điểm

**Chức năng vận hành (Staff):**
7. Xử lý xe vào bãi: kiểm tra điều kiện, nhập/quét biển số, hướng dẫn tầng/khu vực
8. Tạo lượt gửi xe (parking session) với auto-assign hoặc manual mode
9. Xử lý xe ra bãi: tìm lượt gửi, tính phí tự động, thu phí
10. Xử lý ngoại lệ: mất thẻ, sai biển số, quá hạn, gửi sai khu vực

**Chức năng người dùng (Driver):**
11. Xem thông tin bãi xe, bảng giá, số slot trống (realtime)
12. Đặt chỗ trước (reservation)
13. Theo dõi lượt gửi xe hiện tại và lịch sử
14. Thanh toán online

**Chức năng thuật toán tối ưu (Research):**
15. API gợi ý tầng/slot tối ưu với 2 mode: auto-assign / manual (A/B testing)
16. Zone Filtering theo loại xe và trạng thái slot
17. WSM Scoring đa tiêu chí (khoảng cách, tỷ lệ lấp đầy, thời gian gửi, tầng ưu tiên)
18. Threshold Load Balancing khi giờ cao điểm (floor ≥ 85% occupancy)

**Chức năng AI dự đoán:**
19. Dự đoán giờ cao điểm (Peak Hour Prediction) — train trên dữ liệu check-in lịch sử
20. Dự đoán thời gian gửi xe (Parking Duration Prediction) — train trên dữ liệu session lịch sử

## 9. Expected Contribution

Đóng góp dự kiến:

1. **Thiết kế kiến trúc hệ thống** quản lý tòa nhà gửi xe nhiều tầng tích hợp thuật toán phân bổ slot tối ưu và mô hình AI dự đoán, sử dụng Node.js Express + React + React Native + MongoDB.
2. **Đơn giản hóa và tích hợp** 4 thuật toán tối ưu hóa từ nghiên cứu (MFD, Hungarian, TOPSIS/CRITIC, NSGA-II) thành pipeline phân bổ slot khả thi cho ứng dụng thực tế.
3. **Xây dựng mô hình AI dự đoán** giờ cao điểm và thời gian gửi xe, tích hợp vào pipeline phân bổ slot để nâng cao độ chính xác quyết định (so với rule-based truyền thống).
4. **Đánh giá thực nghiệm** hiệu quả của thuật toán phân bổ tự động + AI so với phân bổ thủ công thông qua A/B testing với 4 kịch bản, bao gồm: tỷ lệ lấp đầy, thời gian tìm chỗ, throughput giờ cao điểm, rejection rate.
5. **Phân tích và so sánh** các chiến lược phân bổ slot (single-criteria vs. multi-criteria, rule-based vs. AI-enhanced) và đề xuất bộ trọng số WSM phù hợp cho bãi xe nhiều tầng.

## 10. Evaluation Plan

Nhóm sẽ đánh giá hệ thống như thế nào?

- **Dataset:** Seed data giả lập 500+ parking sessions với kịch bản giờ cao điểm, giờ bình thường. Dữ liệu thực tế thu thập trong 4 tuần vận hành.
- **Baseline:** Manual assignment (Staff tự chọn khu vực), Single-criteria assignment (chỉ theo khoảng cách hoặc tầng thấp nhất).
- **Metrics:**

| Metric | Mục tiêu | RQ |
|---|---|---|
| Tỷ lệ lấp đầy trung bình (Occupancy Rate) | ≥ 75% giờ bình thường | RQ1 |
| Tỷ lệ lấp đầy đồng đều (StdDev giữa tầng) | ≤ 10% | RQ1 |
| Thời gian tìm chỗ trung bình | Auto ≤ 2 phút | RQ2 |
| Tỷ lệ giảm thời gian so với manual | ≥ 40% | RQ2 |
| Slot Assignment Accuracy (không đổi slot) | ≥ 90% | RQ3 |
| Occupancy Balance Score | ≥ 0.85 | RQ3 |
| Tỷ lệ sử dụng giờ cao điểm | ≥ 85% | RQ4 |
| Rejection Rate (xe bị từ chối) | ≤ 5% | RQ4 |
| Peak Throughput | ≥ 30 session/giờ | RQ4 |
| Peak Prediction Accuracy (AI) | F1-score ≥ 0.80 | AI |
| Duration Prediction Error (AI) | MAE ≤ 15 phút | AI |
| AI vs Rule-based Improvement | Occupancy tăng ≥ 5% so với rule-based | AI |

- **AI Model Evaluation:** So sánh pipeline AI-enhanced vs. rule-based trên cùng dataset (500+ sessions). Đo accuracy, precision, recall cho Peak Prediction; MAE, RMSE cho Duration Prediction.
- **Expert evaluation:** Đánh giá bởi giảng viên hướng dẫn và chuyên gia domain.
- **User survey:** Khảo sát Staff về mức hài lòng (thang 1–5, mục tiêu ≥ 4.0).

## 11. Related Papers

Liệt kê ít nhất 5 bài báo liên quan.

| No | Title | Year | Source | Link / DOI |
|---|---|---|---|---|
| 1 | Optimal parking occupancy with and without differentiated parking: A macroscopic analysis | 2021 | Transportation Letters, Scopus Q2, IF=3.3 | [10.1080/19427867.2021.1988245](https://www.researchgate.net/publication/342281166_Optimal_Parking_Occupancy_with_and_without_Differentiated_Parking_A_Macroscopic_Analysis) |
| 2 | Optimal parking management of connected autonomous vehicles: A control-theoretic approach | 2021 | Transportation Research Part C, Scopus Q1, IF=7.9 | [10.1016/j.trc.2020.102924](https://doi.org/10.1016/j.trc.2020.102924) |
| 3 | New Parking Lot Selection Approach Based on the Multi-Criteria Decision Making (MCDM) Methods: Health Criteria | 2023 | Sustainability, Scopus Q2, IF=3.3 | [10.3390/su15020938](https://doi.org/10.3390/su15020938) |
| 4 | Optimization Method for Allocating Peak-Period Parking Demand in Hub Parking Lot Clusters | 2024 | Systems, JCR Q1, IF=3.1 | [10.3390/systems12100404](https://doi.org/10.3390/systems12100404) |
| 5 | A reservation and allocation model for shared-parking addressing the uncertainty in drivers' arrival/departure time | 2022 | Transportation Research Part C, Scopus Q1, IF=7.9 | [10.1016/j.trc.2021.103484](https://doi.org/10.1016/j.trc.2021.103484) |

