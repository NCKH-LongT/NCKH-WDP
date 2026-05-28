# Research Questions

## Main Research Question
- Hệ thống quản lý bãi đỗ nhiều tầng tích hợp phát hiện ô theo thời gian thực và phân bổ nhận biết đặt chỗ sẽ cải thiện hiệu quả phân bổ chỗ và giảm thời gian tìm chỗ như thế nào?

## Research Questions (2–4 câu)
RQ1. Hệ thống phát hiện tình trạng ô dựa trên camera (vision-based) có độ chính xác và độ trễ như thế nào trong bãi nhiều tầng so với hệ thống cảm biến từng ô?

RQ2. Thuật toán phân bổ chỗ nào (heuristic, tối ưu hóa, kết hợp ML) cho trade-off tốt nhất giữa thời gian tính toán và hiệu quả sử dụng bãi khi có dữ liệu đặt chỗ trước?

RQ3. Việc tích hợp dữ liệu đặt chỗ (reservation) ảnh hưởng ra sao đến throughput hệ thống và độ trễ tại lối vào trong các kịch bản tải khác nhau?

RQ4 (tùy chọn). Cơ chế xử lý xung đột đặt chỗ tại lối vào (prioritization / reallocation) nào giảm thiểu độ trễ và tỷ lệ hủy đặt chỗ hiệu quả nhất?

## Measurable targets (liên kết KPI)
- RQ1 targets: occupancy detection Accuracy ≥ 90%; processing latency per frame ≤ 200ms (edge-friendly target) for practical deployment.
- RQ2 targets: allocator runtime per decision ≤ 1s; achieved utilization within 5% of optimal (simulated optimum) under medium load.
- RQ3 targets: reservation success rate ≥ 95%; average entrance delay < 30s under medium load.
- RQ4 targets: under peak load, prioritization strategy should reduce cancellation rate and keep mean waiting time improvement ≥ 15% vs naive first-come-first-serve.

## (Optional) Hypotheses
- H1: Bộ phân bổ nhận biết đặt chỗ giảm thời gian tìm chỗ trung bình ít nhất 20% trong kịch bản nhiều tầng giả lập.
- H2: Bộ phân bổ hybrid (ML + heuristic) đạt hiệu suất sử dụng bãi gần bằng tối ưu với thời gian xử lý chấp nhận được cho thời gian thực.
