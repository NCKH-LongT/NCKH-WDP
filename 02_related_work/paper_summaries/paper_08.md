# Paper 08 Summary

## Citation

Tên bài: Optimization Method for Allocating Peak-Period Parking Demand in Hub Parking Lot Clusters
Tác giả: Zhang, C., Liu, W., Yan, C., Ye, X. & Cheng, J.
Năm: 2024
Nguồn: Systems, Vol. 12, No. 10, Article 404. MDPI (JCR Q1 — Social Sciences, Interdisciplinary | Scopus Q2 — Modeling & Simulation | IF = 3.1 | CiteScore = 4.1)
DOI/Link: [10.3390/systems12100404](https://doi.org/10.3390/systems12100404)

## Problem

Bài báo giải quyết vấn đề **phân bổ nhu cầu đỗ xe giờ cao điểm cho cụm bãi đỗ tại hub giao thông:**

- **Hub giao thông ngày càng quan trọng:** Với sự phát triển đô thị và phổ biến giao thông đa phương thức (multi-modal), hub giao thông trở thành nút kết nối quan trọng.
- **Giờ cao điểm gây quá tải:** Nhu cầu đỗ xe tăng đột biến → tăng lưu lượng đường xung quanh hub → tắc nghẽn trên các tuyến tiếp cận.
- **Delay tìm chỗ đỗ:** Xe phải chạy vòng tìm chỗ trên các tuyến đường xung quanh bãi xe, gây **parking search delay** đáng kể.

## Method

Tác giả xây dựng **mô hình tối ưu phân bổ nhu cầu đỗ xe** gồm 2 phần:

1. **Mô hình ước lượng parking search delay:**
   - Phân tích quy trình tìm chỗ đỗ (vehicle parking search process) trên đường xung quanh bãi.
   - Xây dựng công thức: `D_k = f(demand_k, capacity_k, road_speed_k)` — tính delay cho mỗi bãi xe k dựa trên nhu cầu, sức chứa, và tốc độ đường dẫn vào.

2. **Mô hình tối ưu phân bổ nhu cầu:**
   - **Hàm mục tiêu:** Tối thiểu hóa tổng parking search delay cho tất cả xe: `min Σ D_k(x)`.
   - **Biến quyết định:** `x_ik` = tỷ lệ nhu cầu từ nguồn i được phân bổ cho bãi k, `Σ_k(x_ik) = 1`.
   - **Giải bằng NSGA-II (Non-dominated Sorting Genetic Algorithm II):** Multi-objective optimization với non-dominated sorting + crowding distance. Toán tử: SBX crossover + polynomial mutation.

## Dataset

Bài báo sử dụng **case study thực tế tại Nanjing (Nam Kinh), Trung Quốc:**

- **Đối tượng:** Một hub giao thông lớn (major transportation hub) tại Nanjing với cụm bãi đỗ xe xung quanh.
- **Thu thập dữ liệu:** Khảo sát thực địa (field investigations) và thí nghiệm mô phỏng (simulation experiments).
- **Xác định giờ cao điểm:** Phân tích dữ liệu để nhận diện peak parking demand periods.
- **Hiệu chuẩn tham số:** Dữ liệu thực tế dùng để calibrate các tham số mô hình delay.

## Evaluation

| Metric | Mô tả |
|---|---|
| Average Vehicle Delay | Thời gian trễ trung bình mỗi xe khi tìm chỗ đỗ — metric chính |
| Total Delay Reduction | Tổng thời gian trễ tiết kiệm được (giây) |
| Delay Reduction Rate | Phần trăm giảm delay so với phương pháp không tối ưu |

So sánh: Mô hình tối ưu vs. phân bổ không tối ưu (status quo).

## Results

- **Giảm 4.5% thời gian trễ trung bình** (average vehicle delay) cho xe tìm chỗ đỗ.
- **Tiết kiệm tổng cộng 13,860 giây** delay trong 1 giờ cao điểm tại hub — tương đương khoảng 231 phút.
- **Phân bổ nhu cầu đều hơn** giữa các bãi đỗ trong cụm → giảm quá tải cục bộ.
- **Kết quả ổn định qua nhiều kịch bản:** Mô hình hiệu quả ở các mức nhu cầu khác nhau.

## Limitations

1. **Tập trung cụm bãi đỗ ngoài trời:** Mô hình dành cho parking lot clusters xung quanh hub — cần điều chỉnh cho bãi đỗ trong nhà đa tầng.
2. **Delay model đơn giản hóa:** Chỉ xét delay trên đường dẫn vào bãi — chưa xét delay bên trong bãi (tìm slot cụ thể).
3. **NSGA-II computational cost:** Multi-objective GA có thời gian tính toán cao — khó áp dụng real-time cho hệ thống quy mô nhỏ.
4. **Case study đơn lẻ:** Chỉ kiểm chứng tại một hub ở Nanjing — cần thêm case studies ở bối cảnh khác.

## Relevance to our topic

Bài báo liên quan trực tiếp đến **RQ4** (cải thiện tỷ lệ sử dụng giờ cao điểm) và cung cấp:

- **Nguyên lý phân bổ nhu cầu:** Phân bổ đều xe giữa các bãi → hệ thống áp dụng tương tự cho phân bổ giữa các tầng (tầng gần đầy → chuyển hướng xe đến tầng trống hơn).
- **Ngưỡng 85%:** Mô hình delay cho thấy delay tăng mạnh khi occupancy vượt ngưỡng → hệ thống sử dụng threshold 85% để kích hoạt load balancing.
- **Peak detection:** Phân tích dữ liệu lịch sử để nhận diện giờ cao điểm → hệ thống dùng: `isPeakHour = checkHistoricalPattern(currentHour)`.
- **NSGA-II → Threshold-based đơn giản hóa:** NSGA-II quá phức tạp cho real-time → hệ thống đơn giản hóa thành threshold-based load balancing, giữ nguyên nguyên lý redirect khi quá tải.

## Possible improvement

1. **Áp dụng delay model cho bãi đỗ trong nhà:** Thay `road_speed_k` bằng `in_lot_traversal_time` → tính delay khi xe di chuyển giữa các tầng.
2. **Nâng cấp threshold-based lên multi-objective:** Khi có đủ dữ liệu, sử dụng NSGA-II hoặc phiên bản đơn giản để tối ưu đồng thời delay + load imbalance.
3. **Kết hợp với Reservation-Aware (P10):** Tính `effective_occupancy = (occupied + reserved) / total` trong mô hình delay → phản ánh chính xác hơn tình trạng thực tế.
4. **Adaptive threshold:** Thay vì cố định 85%, sử dụng dữ liệu lịch sử để tự điều chỉnh ngưỡng tối ưu cho từng tầng/khung giờ.
