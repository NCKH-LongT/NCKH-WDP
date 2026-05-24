# Paper 02 Summary

## Citation

Tên bài: Optimal parking occupancy with and without differentiated parking: A macroscopic analysis
Tác giả: Jakob, M. & Menendez, M.
Năm: 2021
Nguồn: Transportation Letters: The International Journal of Transportation Research, Taylor & Francis (Scopus Q2, IF = 3.3, CiteScore = 7.7, SJR = 0.889)
DOI/Link: [10.1080/19427867.2021.1988245](https://www.researchgate.net/publication/342281166_Optimal_Parking_Occupancy_with_and_without_Differentiated_Parking_A_Macroscopic_Analysis)

## Problem

Bài báo giải quyết vấn đề xác định **tỷ lệ lấp đầy tối ưu (optimal occupancy)** cho bãi xe đô thị. Vấn đề cụ thể:
- Occupancy quá cao (>85%) gây ra hiện tượng **"cruising"** — xe chạy vòng tìm chỗ trống, tăng tắc nghẽn nội bộ, thời gian tìm chỗ tăng phi tuyến.
- Occupancy quá thấp (<50%) lãng phí tài nguyên hạ tầng — bãi xe rộng nhưng không được sử dụng hiệu quả.
- Cần tìm điểm cân bằng tối ưu giữa cruising delay và under-utilization cost.
- Câu hỏi nghiên cứu: Liệu chính sách **differentiated parking** (dành riêng khu vực cho từng loại xe) có cải thiện tỷ lệ sử dụng so với bãi đỗ hỗn hợp (mixed parking)?

## Method

Sử dụng **mô hình giao thông vĩ mô (macroscopic traffic model)** với ba thành phần chính:

1. **Macroscopic Fundamental Diagram (MFD):**
   - Mô hình hóa mối quan hệ giữa mật độ xe (density), lưu lượng (flow), và tốc độ trung bình (average speed) trên toàn mạng lưới bãi xe.
   - Khi mật độ tăng quá ngưỡng → flow giảm (tắc nghẽn) → cruising tăng.

2. **Optimal Occupancy Computation:**
   - Hàm mục tiêu: `O* = argmin_{O} [CruisingDelay(O) + UnderUtilizationCost(O)]`
   - Tìm điểm O* nơi tổng chi phí (cruising + lãng phí) là nhỏ nhất.
   - CruisingDelay(O) tăng phi tuyến khi O > 85%.
   - UnderUtilizationCost(O) giảm tuyến tính khi O tăng.

3. **Zone Differentiation Model:**
   - Chia bãi xe thành zones theo loại xe (EV, xe thường, xe tải nhỏ).
   - Tính riêng O* cho mỗi zone.
   - So sánh kết quả với bãi không phân zone (mixed parking).

## Dataset

Bài báo sử dụng **mô hình toán học và mô phỏng:**
- Dữ liệu tham số dựa trên nghiên cứu giao thông đô thị (urban traffic studies).
- Mô phỏng với các tham số: số slot, tỷ lệ các loại xe, tốc độ đến (arrival rate), thời gian đỗ trung bình (average parking duration).
- Nhiều kịch bản: mixed vs. differentiated, occupancy 50% – 95%, tỷ lệ EV 10% – 30%.
- Không sử dụng dataset thực tế từ bãi xe cụ thể.

## Evaluation

Các metric đánh giá:
- **Optimal Occupancy Rate (O*):** Tỷ lệ lấp đầy tối ưu tìm được cho mỗi kịch bản.
- **Total System Cost:** Tổng chi phí = CruisingDelay + UnderUtilizationCost.
- **Cruising Time:** Thời gian trung bình xe chạy vòng tìm chỗ (giây).
- **Zone-Level Occupancy Variance:** Độ lệch chuẩn occupancy giữa các zone — đánh giá mức cân bằng.

## Results

Kết quả chính:
- **Optimal occupancy O* nằm trong khoảng 70%–85%** tùy kịch bản — không phải 100% như trực giác.
- Khi occupancy > 85%, cruising delay **tăng phi tuyến** (exponential) → chi phí hệ thống tăng nhanh.
- **Differentiated parking giảm total system cost 10–15%** so với mixed parking trong hầu hết kịch bản.
- Zone dành riêng cho từng loại xe giúp giảm variance giữa các zone → occupancy cân bằng hơn.
- Khi tỷ lệ EV tăng (>20%), lợi ích của differentiated parking càng rõ rệt vì EV có parking duration dài hơn xe thường.

## Limitations

- **Mô hình vĩ mô, không chi tiết mức slot:** MFD mô hình hóa ở mức tổng thể (aggregated), không phân biệt từng slot riêng lẻ → khó áp dụng trực tiếp cho phân bổ slot real-time.
- **Giả định arrival rate ổn định:** Không xét giờ cao điểm vs. thấp điểm → thiếu tính thực tiễn cho bãi xe có lưu lượng biến động.
- **Chưa tích hợp dynamic zoning:** Zone được chia cố định từ đầu, không thay đổi theo thời gian thực khi demand thay đổi.
- **Không xét reservation:** Không tính slot đã đặt trước vào effective occupancy.
- **Thiếu validation thực tế:** Kết quả dựa trên mô phỏng toán học, chưa kiểm chứng trên bãi xe thực.

## Relevance to our topic

**Liên quan trực tiếp đến RQ1** (phân tầng theo loại phương tiện) và **RQ4** (cải thiện tỷ lệ sử dụng giờ cao điểm):

- **RQ1:** Kết quả differentiated parking > mixed parking là **cơ sở trực tiếp cho giả thuyết H1** rằng phân tầng chuyên biệt (mỗi tầng dành cho 1 loại xe) cải thiện occupancy. Hệ thống áp dụng nguyên lý này qua **Dynamic Vehicle-Type Zoning**: tầng gần cổng → xe máy (turnover cao), tầng xa → ô tô (duration dài).
- **RQ4:** Ngưỡng 85% occupancy được sử dụng trực tiếp trong **Load Balancing Algorithm** — khi `floor.occupancy >= 0.85` → kích hoạt chuyển hướng xe sang tầng khác, tránh cruising delay.
- **Metric:** StdDev(occupancy_per_floor) ≤ 10% lấy cảm hứng từ zone-level occupancy variance trong bài báo.

## Possible improvement

1. **Từ static zoning sang dynamic zoning:** P2 chia zone cố định → hệ thống có thể mở rộng sang dynamic zoning dựa trên dữ liệu check-in lịch sử (demand_ratio thay đổi theo thời gian).
2. **Thêm giờ cao điểm:** P2 giả định arrival rate ổn định → hệ thống tích hợp **Peak Hour Prediction (AI)** để phát hiện giờ cao điểm và kích hoạt load balancing sớm hơn.
3. **Chi tiết hóa xuống mức slot:** P2 mô hình hóa ở mức vĩ mô → hệ thống chi tiết hóa xuống mức từng slot bằng **WSM scoring** (RQ3) — kết hợp khoảng cách, tỷ lệ lấp đầy, thời gian gửi, tầng ưu tiên.
4. **Reservation-aware occupancy:** P2 không tính reservation → hệ thống bổ sung `effective_occupancy = (occupied + reserved) / total` từ [P10] (Wang, Li & Xie 2022).
5. **Validation trên seed data:** So sánh differentiated vs. mixed qua A/B testing với seed data 500+ sessions thay vì chỉ mô phỏng toán học.
