# Paper 10 Summary

## Citation

Tên bài: A reservation and allocation model for shared-parking addressing the uncertainty in drivers' arrival/departure time
Tác giả: Wang, S., Li, Z. & Xie, N.
Năm: 2022
Nguồn: Transportation Research Part C: Emerging Technologies, Volume 135, Article 103484. Elsevier (Scopus Q1, IF = 7.9, SJR = 2.734)
DOI/Link: [10.1016/j.trc.2021.103484](https://doi.org/10.1016/j.trc.2021.103484)

## Problem

Bài báo giải quyết bài toán quản lý và vận hành nền tảng đỗ xe chia sẻ (shared-parking). Thách thức lớn nhất là **tính không chắc chắn (uncertainty)** về thời gian thực tế của người dùng — tài xế đến sớm/muộn hoặc rời đi sớm/trễ so với thời gian đăng ký đặt chỗ. Sự sai lệch này dẫn đến **xung đột đỗ xe (service failure)** giữa các xe đỗ liên tiếp trong cùng vị trí — ví dụ xe trước chưa rời đi mà xe sau đã đến — làm giảm hiệu suất khai thác và tăng tỷ lệ phục vụ thất bại. Các hệ thống đặt chỗ truyền thống (deterministic models) giả định tài xế đến/đi đúng giờ, không phản ánh thực tế vận hành.

## Method

Tác giả đề xuất **mô hình tối ưu hóa ràng buộc cơ hội (Chance-Constrained Optimization Model)** kết hợp MILP:

1. **Chance-Constrained Programming:** Mô hình hóa thời gian đến/đi dưới dạng **biến ngẫu nhiên (stochastic variables)** với phân phối xác suất học từ dữ liệu lịch sử. Ràng buộc: `P(service failure ≤ threshold) ≥ 1 - ε`, đảm bảo xác suất phục vụ thành công đạt ngưỡng tối thiểu.

2. **Rule-based MILP (Mixed-Integer Linear Programming):** Biến quyết định: xe nào gán vào slot nào, trong khung thời gian nào. Hàm mục tiêu: **tối đa hóa kỳ vọng tổng thời gian đỗ xe (expected total occupied parking hours)** — tối ưu mức độ sử dụng bãi đỗ.

3. **Reservation-Aware Capacity Model:** Tính effective occupancy bao gồm cả slot đã reserved: `effective_occupancy = (occupied + reserved) / total_slots` → tránh over-allocation.

4. **Stochastic Arrival/Departure Model:** Mô hình hóa thời gian đến/đi bằng phân phối xác suất cụ thể (dựa trên mẫu hành vi lịch sử) → tích hợp vào bài toán tối ưu dưới dạng ràng buộc xác suất.

## Dataset

Bài báo sử dụng **mô phỏng số (numerical simulations)** kết hợp tham số dựa trên dữ liệu thực tế tại các đô thị lớn (Trung Quốc):

- **Khung thời gian hoạt động:** Chia thành nhiều time-slot rời rạc trong ngày.
- **Quy luật phân phối yêu cầu đặt chỗ:** Nhu cầu đỗ xe mô hình hóa theo phân phối xác suất thực nghiệm.
- **Dữ liệu hành vi đỗ xe:** Phân phối xác suất thời gian đi trễ/đến sớm, thu thập từ hệ thống đỗ xe chia sẻ thực tế.
- **Các kịch bản thử nghiệm:** Nhiều kịch bản với số lượng slot, số yêu cầu và mức variance khác nhau.

## Evaluation

| Metric | Mô tả |
|---|---|
| Parking Utilization Level | Kỳ vọng tổng thời gian đỗ xe — tỷ lệ thời gian chỗ trống được lấp đầy hiệu quả |
| Service Failure Rate | Xác suất xe không thể đỗ do xung đột thời gian (xe trước chưa đi, xe sau đã đến) — mục tiêu ≤ ε |
| Request Acceptance Rate | Tỷ lệ yêu cầu đặt chỗ được chấp nhận thành công |
| Average User Cost | Thời gian di chuyển + chờ đợi + chi phí đỗ xe thực tế |

So sánh với baseline: mô hình tất định (deterministic) và FCFS.

## Results

- **Tăng đáng kể parking utilization:** Expected total occupied parking hours cao hơn so với deterministic model, nhờ phân bổ slot linh hoạt hơn.
- **Giảm thiểu service failure rate:** Tích hợp phân phối xác suất thời gian đến/đi vào ràng buộc tối ưu giúp giữ service failure dưới ngưỡng cho phép.
- **Request acceptance rate cao hơn:** Chấp nhận nhiều yêu cầu đặt chỗ hơn mà vẫn đảm bảo chất lượng phục vụ.
- **Average user cost giảm:** Chi phí tổng thể (thời gian + tiền) giảm so với phương pháp không tính uncertainty.
- **Kết luận:** Tích hợp tính ngẫu nhiên (stochasticity) vào quy trình đặt chỗ giúp vận hành hiệu quả và đáng tin cậy hơn so với mô hình tất định.

## Limitations

1. **Giả định phân phối xác suất:** Dựa trên giả định thời gian đến/đi tuân theo pattern cố định — hành vi tài xế thực tế có thể thay đổi đột ngột do ngoại cảnh.
2. **Scalability:** Bài toán MILP gặp khó khăn khi mở rộng lên quy mô rất lớn (hàng nghìn slot, hàng chục nghìn yêu cầu/ngày) — NP-hard.
3. **Chưa tích hợp Dynamic Pricing:** Tập trung vào lập lịch phân bổ, chưa mở rộng vào điều chỉnh giá theo thời gian thực.
4. **Dữ liệu mô phỏng:** Chủ yếu numerical simulations, chưa kiểm chứng đầy đủ trên nền tảng shared-parking thực tế đang hoạt động.
5. **Tính tĩnh của mô hình:** Giải bài toán phân bổ theo batch/rolling horizon, chưa hoàn toàn real-time adaptive.

## Relevance to our topic

Bài báo cung cấp nền tảng lý thuyết cốt lõi cho **RQ4** (cải thiện tỷ lệ sử dụng giờ cao điểm):

- **Reservation-Aware Capacity Model** (`effective_occupancy = (occupied + reserved) / total_slots`) áp dụng trực tiếp vào thuật toán **Load Balancing** — tránh over-allocation khi có slot đã đặt trước nhưng chưa có xe vào.
- **Chance-Constrained framework** cung cấp cơ sở lý thuyết cho việc tính toán **buffer time / safety margin** khi lập lịch phân bổ — quan trọng nếu mở rộng tính năng reservation.
- Nguyên lý **uncertainty handling** giúp thiết kế hệ thống App Đặt Chỗ có khả năng chịu lỗi khi tài xế không đến đúng giờ.
- Bài báo thuộc Scopus **Q1** (IF = 7.9) trên *Transportation Research Part C*, tăng chất lượng học thuật cho danh mục tham khảo.

## Possible improvement

1. **Tích hợp ML dự đoán hành vi tài xế:** Dùng ML (Gradient Boosting, LSTM) dự đoán thời gian đến/đi dựa trên lịch sử cá nhân thay vì phân phối xác suất cố định: `actual_arrival = f(booked_time, user_history, traffic_conditions)`.
2. **Kết hợp Dynamic Pricing:** Tài xế đỗ đúng giờ hoặc chấp nhận slot thời gian đệm ngắn → giá ưu đãi, khuyến khích tuân thủ.
3. **Real-time adaptive re-optimization:** Nâng cấp từ batch/rolling horizon lên real-time có khả năng re-optimize liên tục khi nhận sự kiện mới (xe đến sớm, xe rời muộn, hủy đặt chỗ), kết hợp event-driven architecture.
4. **Đơn giản hóa cho hệ thống:** Trong phạm vi đồ án, đơn giản hóa chance-constrained thành **rule-based reservation check** — khi tính occupancy, luôn cộng thêm slot reserved → ngưỡng 85% bao gồm cả reserved slots.
