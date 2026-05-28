# Problem Statement

## Background
- Bối cảnh: Sự gia tăng đô thị hóa và số lượng phương tiện cá nhân làm tăng nhu cầu bãi đỗ, gây tắc nghẽn, tiêu tốn thời gian và nhiên liệu.
- Mục tiêu chung: Hệ thống quản lý bãi đỗ thông minh (smart parking) nhằm giảm thời gian tìm chỗ, tối ưu hóa công suất sử dụng và hỗ trợ đặt chỗ trước cho bãi đỗ nhiều tầng.

## Specific Problem
- Vấn đề chính: Thiếu một giải pháp tổng hợp cho bãi đỗ nhiều tầng (multi-level) kết hợp phát hiện tình trạng ô theo tầng theo thời gian thực, phân bổ chỗ nhận biết đặt chỗ, và giảm tắc nghẽn tại lối vào khi có xung đột đặt chỗ.
- Triệu chứng thực tế: lái xe mất nhiều thời gian tìm ô trống, xung đột đặt chỗ làm tăng độ trễ tại cổng, và hiệu suất sử dụng bãi chưa tối ưu trong các bãi nhiều tầng.

## Scope
- Phạm vi: Nghiên cứu tập trung vào bãi đỗ nhiều tầng thương mại/công cộng, triển khai giải pháp phần mềm (không bao gồm phần cứng cổng/tự động hóa vật lý).
- Dữ liệu: Sử dụng camera cố định (hình ảnh/luồng video), lịch đặt chỗ, và các tập dữ liệu công khai hoặc thu thập cục bộ để mô phỏng môi trường nhiều tầng.
- Giới hạn: Giai đoạn đầu thử nghiệm trong mô phỏng và tập dữ liệu; mở rộng thực nghiệm thực tế là khuyến nghị tiếp theo.

## Objectives
- Xây dựng mô-đun phát hiện tình trạng ô theo tầng sử dụng phương pháp tầm nhìn máy tính phù hợp cho môi trường nhiều tầng.
- Thiết kế bộ phân bổ chỗ kết hợp (heuristic + ML/optimization) có khả năng xử lý đặt chỗ trước và tối ưu hóa thời gian tìm chỗ.
- Đánh giá hệ thống theo các chỉ số: thời gian tìm chỗ trung bình, tỷ lệ đặt chỗ thành công, độ trễ tại lối vào, công suất sử dụng bãi, và chi phí tính toán.

## Expected Impact
- Giảm thời gian tìm chỗ và ùn tắc, nâng cao trải nghiệm người dùng và hiệu quả hoạt động bãi đỗ.
- Cung cấp khung đánh giá và bộ phương pháp cho quản lý bãi đỗ nhiều tầng, làm cơ sở cho triển khai thực nghiệm và tích hợp với hệ thống quản lý đô thị.

## Experiment setup & Evaluation (Chi tiết thử nghiệm)

### Dataset sources
- Public datasets: CNRPark, PKLot, và các tập ảnh bãi đỗ công khai (dùng để huấn luyện mô-đun phát hiện).
- Thu thập cục bộ: quay video/một số camera cố định tại bãi đỗ nhiều tầng mô phỏng (ghi nhãn occupancy theo tầng, timestamp, và vị trí ô).
- Synthetic / Simulation: tạo kịch bản multi-level trong môi trường mô phỏng (ví dụ SUMO / custom simulator) để kiểm thử thuật toán phân bổ và xung đột đặt chỗ.

### Experimental scenarios (kịch bản thử nghiệm)
- Low load: tỉ lệ lấp đầy < 40%, ít đặt chỗ — kiểm tra độ chính xác phát hiện và baseline phân bổ.
- Medium load: tỉ lệ lấp đầy 40–70% kèm đặt chỗ theo lịch — kiểm tra hiệu quả phân bổ và tỷ lệ thành công reservation.
- High load / peak: tỉ lệ lấp đầy > 80% với nhiều xung đột đặt chỗ đồng thời — kiểm tra cơ chế xử lý xung đột và độ trễ tại lối vào.
- Night / adverse visibility: kiểm thử mô-đun vision trong điều kiện ánh sáng yếu hoặc occlusion.

### Evaluation protocol
- Train/Val/Test splits: giữ ít nhất 20% cho test độc lập; nếu có dữ liệu cục bộ, tách kịch bản thực tế riêng.
- Repeats: chạy mỗi kịch bản nhiều lần (n ≥ 10) với seed khác nhau để lấy trung bình và độ lệch chuẩn.

### Metrics & KPI targets (định lượng)
- Occupancy detection: Accuracy ≥ 90%, Precision ≥ 90% (mục tiêu ban đầu).
- OCR / ALPR (nếu triển khai): OCR accuracy ≥ 85% trong điều kiện chuẩn.
- Time-to-park (time-to-find): giảm ≥ 20% so với baseline rule-based / sensor-only.
- Reservation success rate: ≥ 95% (số lượng đặt chỗ đúng lúc và không bị xung đột).
- Entrance delay (chờ tại cổng trung bình): mục tiêu < 30s dưới tải trung bình; đánh giá thêm tại tải cao.
- System latency: thời gian tính toán allocator cho mỗi yêu cầu < 1s (mục tiêu cho khả năng gần thời gian thực).

### Baselines
- Rule-based allocator (first-available / nearest-first). 
- Sensor-only baseline (per-slot sensor counting) hoặc offline allocation.

### Reporting
- Báo cáo kết quả theo kịch bản (low/medium/high), kèm đồ thị time-to-park phân phối, heatmap mức sử dụng theo tầng, và bảng so sánh KPI vs baseline.
