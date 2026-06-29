# Bước 9: Thiết kế phương pháp đánh giá (Evaluation Metrics)

Một bài báo ứng dụng AI bắt buộc cần có đánh giá định lượng. Hệ thống PBMS gồm nhiều thành phần AI và phi-AI, mỗi thành phần được đánh giá bằng bộ metric phù hợp với bản chất của bài toán đó.

---

## 1. Nhóm Metric theo Loại Bài Toán

| Loại bài toán | Metric phù hợp |
|---|---|
| Phân loại (Classification) | Accuracy, Precision, Recall, F1-score |
| Dự báo (Forecasting) | MAE, RMSE, MAPE |
| Gợi ý (Recommendation) | Top-k Accuracy, Precision@k, Recall@k, NDCG |
| RAG / LLM | Relevance, Faithfulness, Correctness, Expert Rating |
| Hệ thống (System) | Response Time, Throughput, Latency |
| Người dùng (UX) | Survey, SUS, User Satisfaction |
| So sánh quy trình | Time Saving, Error Reduction |

---

## 2. Mapping Metric → Thành Phần Hệ Thống

### 2.1 AI-LPR (YOLOv8 + CRNN-OCR) — Bài toán Phân loại / OCR

> **Loại bài toán:** Phân loại (plate detection) + Nhận dạng chuỗi ký tự (OCR)

| Metric | Định nghĩa | Target | Công cụ |
|---|---|---|---|
| **Character Accuracy** | % ký tự biển số nhận dạng đúng / tổng ký tự | ≥ 85% | Custom eval script |
| **Plate-Level Accuracy** | % biển số đọc đúng hoàn toàn (exact match) | ≥ 80% | Custom eval script |
| **Detection Precision** | TP / (TP + FP) của YOLOv8 plate detector | ≥ 90% | Ultralytics metrics |
| **Detection Recall** | TP / (TP + FN) của YOLOv8 plate detector | ≥ 88% | Ultralytics metrics |
| **F1-score (Detection)** | 2 × Precision × Recall / (P + R) | ≥ 89% | Ultralytics metrics |
| **Inference Latency** | Thời gian LPR inference / 1 frame | < 200 ms | Python time module |

**Công thức Character Accuracy:**
$$\text{Char Acc} = \frac{\sum_{i} \text{correct\_chars}(i)}{\sum_{i} \text{total\_chars}(i)} \times 100\%$$

**Điều kiện thử nghiệm:**
- Standard lighting (indoor, 300–500 lux)
- Adverse conditions (night < 50 lux, direct glare, partial occlusion)
- Oblique angles (±15°, ±25°)

---

### 2.2 Slot Allocator (Heuristic Optimization) — Bài toán So sánh Quy trình

> **Loại bài toán:** Tối ưu hóa + So sánh hiệu quả quy trình

| Metric | Định nghĩa | Target | Công cụ |
|---|---|---|---|
| **Time-to-Park (TTP)** | Thời gian TB từ khi xe vào cổng đến khi đỗ xong (giây) | Giảm ≥ 20% so với baseline | Simulation log |
| **Reservation Success Rate** | % đặt chỗ thành công, không xung đột | ≥ 95% | Booking service log |
| **Allocation Latency** | Thời gian tính toán allocator / 1 request | < 1 giây | Server profiling |
| **Space Utilisation** | % ô đỗ được sử dụng / tổng ô khả dụng | Maximize vs baseline | Parking Service log |
| **Conflict Rate** | % lượt đặt chỗ bị xung đột / tổng lượt | Minimize | Booking service log |

**So sánh kịch bản (Scenario-based):**

| Kịch bản | Occupancy | Mô tả |
|---|---|---|
| Low load | < 40% | Kiểm tra correctness baseline |
| Medium load | 40–70% | Nominal operational test |
| High / Peak | > 80% | Stress test conflict resolution |
| Adverse visibility | Any | Night/occlusion — kiểm tra LPR robustness |

---

### 2.3 Gate Terminal — Bài toán Hệ thống (System Performance)

> **Loại bài toán:** Hệ thống / Trải nghiệm cổng

| Metric | Định nghĩa | Target | Công cụ |
|---|---|---|---|
| **Gate Entrance Latency** | Thời gian từ khi xe đến cổng đến khi barrier mở (giây) | < 30 giây (medium load) | End-to-end timer |
| **System Throughput** | Số xe xử lý thành công / giờ | Maximize | Simulation counter |
| **API Response Time** | Thời gian Backend phản hồi request LPR (P95) | < 200 ms | Node.js profiler |
| **WebSocket Latency** | Độ trễ cập nhật slot state real-time | < 500 ms | WS message timer |

---

### 2.4 LLM Smart Parking Assistant (Google Gemini) — RAG / LLM

> **Loại bài toán:** RAG + LLM + User Experience

| Metric | Định nghĩa | Target | Công cụ |
|---|---|---|---|
| **Slot Recommendation Accuracy** | % lần Gemini gợi ý đúng slot tối ưu vs ground truth | ≥ 85% | Manual annotation |
| **Relevance Score** | Mức độ phù hợp của response với query (1–5) | ≥ 4.0 / 5.0 | Expert rating |
| **Faithfulness** | Response có chứa thông tin sai (hallucination) không | ≤ 5% hallucination rate | Manual check |
| **Function Call Success Rate** | % lần Function Calling thực thi đúng function + params | ≥ 95% | Function call log |
| **LLM Response Latency** | Thời gian từ query đến response (giây) | < 2 giây | API timer |

---

### 2.5 Người Dùng (UX / User Satisfaction)

> **Loại bài toán:** Trải nghiệm người dùng

| Metric | Định nghĩa | Target | Công cụ |
|---|---|---|---|
| **User Satisfaction Score** | Khảo sát 5 điểm về trải nghiệm tổng thể | ≥ 4.0 / 5.0 | Google Form |
| **AI Assistant Clarity** | Mức độ rõ ràng của hướng dẫn từ AI (1–5) | ≥ 4.2 / 5.0 | Survey |
| **SUS Score** | System Usability Scale (0–100) | ≥ 70 (good) | SUS questionnaire |
| **Error Reduction** | Giảm % lỗi so với quy trình manual (nhập sai biển số, v.v.) | ≥ 30% | Error log comparison |

---

## 3. Evaluation Protocol

### 3.1 Dataset Splits
- Train / Val / Test: **70% / 10% / 20%** cho AI-LPR.
- Test split được giữ độc lập, không dùng trong training.
- Dữ liệu cục bộ (local video) tách thành kịch bản riêng để đánh giá real-world.

### 3.2 Repeats & Statistical Reporting
- Mỗi kịch bản simulation chạy **n = 10 lần** với random seeds khác nhau.
- Báo cáo: **Mean ± Standard Deviation** cho mỗi metric.

### 3.3 Reporting Format
- Kết quả theo kịch bản (low / medium / high load).
- Biểu đồ phân phối Time-to-Park.
- Heatmap mức sử dụng slot theo tầng.
- Bảng so sánh KPI vs Baseline.
- Bảng so sánh LPR accuracy theo điều kiện ánh sáng.

---

## 4. Tóm tắt KPI Targets

| KPI | Target | Baseline so sánh |
|---|---|---|
| LPR Character Accuracy (chuẩn) | ≥ 85% | Manual entry / sensor-only |
| LPR Plate Accuracy (chuẩn) | ≥ 80% | Manual entry |
| Occupancy Detection Accuracy | ≥ 90% | Rule-based counting |
| Time-to-Park Reduction | ≥ 20% | Rule-based allocator |
| Reservation Success Rate | ≥ 95% | First-available allocation |
| Gate Entrance Latency | < 30 giây | Manual check-in (> 60s avg) |
| Allocator Latency | < 1 giây | — |
| LLM Response Latency | < 2 giây | Manual map navigation |
| VNPay Payment Success Rate | ≥ 99% | Manual billing |
| User Satisfaction | ≥ 4.0 / 5.0 | Manual process |
