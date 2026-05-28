# Research Gap

## Summary of Existing Work
- Nhiều nghiên cứu tập trung vào phát hiện tình trạng ô bằng camera hoặc cảm biến riêng lẻ (camera-based occupancy detection, CNN), hoặc vào cơ chế đặt chỗ/reservation workflows.
- Một số công trình đề xuất thuật toán phân bổ (heuristic, optimization, RL) để tối ưu hiệu suất sử dụng bãi, nhưng thường giả định môi trường một tầng hoặc dữ liệu đầy đủ.
- Một vài hệ thống tích hợp thêm dự đoán (predictive availability) nhưng ít xử lý chi tiết cho bãi nhiều tầng và xung đột đặt chỗ thời gian thực.

## Identified Gaps
- Gap 1: Thiếu đánh giá hệ thống toàn diện cho bãi đỗ nhiều tầng — hầu hết giải pháp thử nghiệm trên tập dữ liệu một tầng hoặc môi trường mô phỏng đơn giản.
- Gap 2: Thiếu tích hợp chặt giữa phát hiện ô theo tầng (vision-based) và bộ phân bổ nhận biết đặt chỗ (reservation-aware allocator).
- Gap 3: Thiếu chiến lược xử lý xung đột đặt chỗ tại lối vào và cơ chế ưu tiên/điều phối khi có nhiều yêu cầu đồng thời.
- Gap 4: Đánh giá hiệu suất thường bỏ qua chỉ số thực tiễn như độ trễ tại cổng và trải nghiệm lái xe trong kịch bản multi-level.

## Why These Gaps Matter
- Hạn chế trên dẫn đến hệ thống không sẵn sàng triển khai thực tế cho bãi nhiều tầng, gây lãng phí tài nguyên và không cải thiện đáng kể trải nghiệm người dùng.

## How This Study Will Address the Gaps
- Kết hợp mô-đun phát hiện tình trạng ô theo tầng (camera-based) với bộ phân bổ chỗ nhận biết đặt chỗ, thiết kế cơ chế xử lý xung đột tại lối vào.
- Đề xuất bộ đánh giá toàn diện cho bãi nhiều tầng bao gồm: thời gian tìm chỗ, tỷ lệ đặt chỗ thành công, độ trễ tại cổng và mức sử dụng bãi.
- Thực hiện thử nghiệm cả trong mô phỏng và trên tập dữ liệu thu thập cục bộ để đánh giá kịch bản thực tế.

## Expected Contributions
- Một khung tích hợp phát hiện-phan bổ cho bãi nhiều tầng có khả năng xử lý đặt chỗ trước và xung đột thời gian thực.
- Bộ chỉ số đánh giá thực tiễn cho nghiên cứu và triển khai smart parking đa tầng.
