# Câu hỏi Nghiên cứu (Research Questions)

Dựa trên khoảng trống nghiên cứu đã được xác định, nhóm đề xuất bốn câu hỏi nghiên cứu chính:

---

## RQ1. Scheduling Optimization
> How effectively can a POX-Heuristic Genetic Algorithm automate the generation of conflict-free tournament schedules while satisfying multiple hard and soft constraints (jockey availability, horse recovery windows, referee fairness)?

**Mục tiêu:** Đánh giá khả năng của thuật toán di truyền POX-Heuristic trong việc tự động tạo lịch thi đấu không xung đột, đồng thời thỏa mãn các ràng buộc cứng/mềm phức tạp.

**Metrics dự kiến:** Số xung đột lịch (= 0), thời gian tính toán (giây), tốc độ hội tụ Fitness, so sánh với xếp lịch thủ công.

---

## RQ2. Race Outcome Prediction
> How accurately can the proposed 8-5-7-1 Multilayer Feedforward ANN predict race completion times and Top-3 placements using physiological and environmental features?

**Mục tiêu:** Đánh giá độ chính xác của mô hình mạng nơ-ron ANN 8-5-7-1 trong việc dự đoán thời gian về đích và thứ hạng Top-3.

**Metrics dự kiến:** MSE, Placement Accuracy (Top-1, Top-3), so sánh với baseline (Random Forest, Linear Regression).

---

## RQ3. System Integration Effectiveness
> To what extent does the integration of AI modules (scheduling GA and prediction ANN) into a unified B/S web platform improve operational efficiency compared to traditional manual workflows?

**Mục tiêu:** Đo lường mức độ cải thiện hiệu quả vận hành khi tích hợp các module AI vào nền tảng web thống nhất, so với quy trình thủ công truyền thống.

**Metrics dự kiến:** Thời gian tiết kiệm (%), tỷ lệ lỗi con người giảm, Response Time API, Throughput hệ thống.

---

## RQ4. Spectator Engagement Enhancement
> How does the provision of AI-driven VIP prediction packages and real-time race tracking via WebSocket improve spectator engagement and platform interaction metrics?

**Mục tiêu:** Đánh giá tác động của các gói dự đoán AI VIP và theo dõi cuộc đua thời gian thực đến mức độ tương tác của khán giả.

**Metrics dự kiến:** Latency WebSocket (ms), số lượng tương tác/phiên, tỷ lệ mua gói VIP, User Satisfaction Survey (SUS).
