# Paper 04 Summary

## Citation

Tên bài: Optimal parking management of connected autonomous vehicles: A control-theoretic approach
Tác giả: Wang, S., Levin, M. W. & Caverly, R. J.
Năm: 2021
Nguồn: Transportation Research Part C: Emerging Technologies, Elsevier (Scopus Q1, IF = 7.9, SJR = 2.734)
DOI/Link: [10.1016/j.trc.2020.102924](https://doi.org/10.1016/j.trc.2020.102924)

## Problem

Bài báo giải quyết vấn đề **quản lý tối ưu bãi đỗ xe cho Connected Autonomous Vehicles (CAVs)** trong bối cảnh có nhiều bãi đỗ trong cùng khu vực:

- **Cạnh tranh giữa các bãi đỗ:** Nhiều bãi đỗ cùng phục vụ một khu vực → nhu cầu phân bổ không đều, có bãi quá tải trong khi bãi khác còn trống.
- **Biến đổi theo thời gian:** Số slot trống thay đổi liên tục theo giờ → cần mô hình động (dynamic model) thay vì tĩnh.
- **Tác động đến giao thông:** Xe tìm chỗ đỗ (cruising) gây tắc nghẽn và tăng tiêu thụ nhiên liệu.

## Method

Tác giả xây dựng **mô hình động ngẫu nhiên liên tục (continuous-time stochastic dynamic model)** lấy cảm hứng từ **phương trình Lotka-Volterra:**

1. **Mô hình hóa hệ thống:** Trạng thái hệ thống `x(t)` = [số slot trống tại mỗi bãi]. Tương tác giữa các bãi đỗ được mô hình hóa tương tự mô hình predator-prey — khi bãi A đầy, nhu cầu tràn sang bãi B.
2. **Biến điều khiển:** Giá đỗ xe (parking rate) tại mỗi bãi là **đầu vào điều khiển `u(t)`** — có thể điều chỉnh bởi nhà vận hành.
3. **Bài toán tối ưu (Bolza problem):** Tối thiểu hóa sai lệch giữa trạng thái thực và trạng thái mong muốn (desired occupancy level) qua thời gian.
4. **Giải bằng Pontryagin's Minimum Principle (PMP):** Xác định điều kiện cần cho nghiệm tối ưu → phát triển thuật toán tính toán cho bài toán phi tuyến và chứng minh hội tụ.

**Lưu ý:** Bài báo sử dụng **PMP (Pontryagin's Minimum Principle)** cho bài toán tối ưu phi tuyến, không phải LQR (Linear Quadratic Regulator). PMP tổng quát hơn LQR — áp dụng cho hệ thống phi tuyến với ràng buộc.

## Dataset

Bài báo sử dụng **mô phỏng Monte Carlo** dưới nhiều kịch bản:

- **Nhiều bãi đỗ:** Mô phỏng hệ thống với nhiều bãi đỗ cạnh tranh trong cùng khu vực.
- **Kịch bản đa dạng:** Thay đổi nhu cầu, tỷ lệ CAVs, và cấu hình bãi đỗ.
- **Mô hình ngẫu nhiên:** Nhu cầu đỗ xe có tính ngẫu nhiên (stochastic demand).

## Evaluation

| Metric | Mô tả |
|---|---|
| Parking Availability | Mức độ duy trì slot trống tại ngưỡng mong muốn |
| Demand Distribution | Hiệu quả phân bổ nhu cầu giữa các bãi đỗ |
| Optimal Pricing Policy | Chính sách giá tối ưu cho từng bãi đỗ theo thời gian |
| Convergence | Tốc độ hội tụ của thuật toán PMP |

So sánh: Centralized coordination (PMP) vs. Decentralized decision-making (greedy nearest-first).

## Results

- **Centralized vượt trội hơn decentralized:** Hệ thống phối hợp trung tâm phân bổ nhu cầu đều hơn giữa các bãi, giảm tắc nghẽn cục bộ.
- **Dynamic pricing hiệu quả:** Điều chỉnh giá theo thời gian thực giúp cân bằng nhu cầu giữa các bãi.
- **Thuật toán hội tụ:** Thuật toán dựa trên PMP được chứng minh hội tụ toán học.
- **Giảm cruising:** Phân bổ tối ưu giúp giảm thời gian xe chạy vòng tìm chỗ, cải thiện giao thông khu vực.

## Limitations

1. **Yêu cầu CAVs:** Giả định xe tự hành tuân thủ tuyệt đối chỉ dẫn — chưa áp dụng cho xe thường.
2. **Dynamic pricing phức tạp:** Đòi hỏi cơ chế giá linh hoạt theo thời gian thực — khó triển khai cho bãi đỗ truyền thống.
3. **Dựa trên mô phỏng:** Chưa có kiểm chứng thực tế (field test).
4. **Multi-facility focus:** Tập trung vào quản lý nhiều bãi đỗ — ít phù hợp trực tiếp cho single-facility.

## Relevance to our topic

Bài báo liên quan đến **RQ2** (phân bổ tự động vs. tự do) và **RQ3** (tiêu chí ưu tiên):

- **Centralized coordination:** Chứng minh hệ thống gán tự động (centralized) hiệu quả hơn người dùng tự chọn (decentralized) — cơ sở lý thuyết cho auto-assign.
- **Nguyên lý cân bằng tải:** Ý tưởng phân bổ nhu cầu đều giữa các bãi → áp dụng cho phân bổ giữa các tầng trong single-facility.
- **Mô hình trạng thái động:** Hệ thống theo dõi `x(t)` = [slot trống] liên tục → tương tự kiến trúc real-time (Socket.IO) của hệ thống.

## Possible improvement

1. **Áp dụng nguyên lý centralized cho single-facility:** Thay vì quản lý nhiều bãi, centralized assignment quản lý nhiều tầng — mỗi tầng tương tự một "bãi" trong mô hình.
2. **Thay dynamic pricing bằng dynamic weight:** Thay vì điều chỉnh giá, điều chỉnh trọng số W2 (occupancy balance) trong WSM khi giờ cao điểm.
3. **Kết hợp với Load Balancing (RQ4):** Nguyên lý phân bổ nhu cầu đều → áp dụng trực tiếp cho Threshold-based Load Balancing.
