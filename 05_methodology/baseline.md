# Bước 10: Xây dựng Baseline

Baseline là phương pháp dùng để so sánh với hệ thống đề xuất. Mỗi thành phần AI của PBMS có một baseline riêng phù hợp với bài toán của nó.

---

## 1. Tổng quan Baseline Framework

| Thành phần hệ thống | Bài toán | Baseline được chọn |
|---|---|---|
| AI-LPR (Gate check-in/out) | Nhận dạng biển số / gate processing | **Manual Entry + Sensor-only** |
| Slot Allocator | Phân bổ chỗ đỗ | **Rule-based (First-Available / Nearest-First)** |
| LLM Parking Assistant | Hướng dẫn tìm chỗ | **Manual 2D Map Navigation** |
| Automated Billing | Tính phí tự động | **Manual Billing (Staff-directed)** |
| Manager Analytics | Phân tích dữ liệu vận hành | **Spreadsheet / Manual Report** |

---

## 2. Baseline Chi Tiết

### 2.1 Baseline cho AI-LPR — Manual Entry + Sensor-only

> **Mô tả:** Không dùng camera AI. Nhân viên nhập biển số thủ công tại cổng, hoặc dùng cảm biến IR/loop detector đếm xe vào/ra (không nhận dạng biển số).

**Baseline A — Manual Entry (Staff-directed):**
- Nhân viên tại cổng nhìn biển số và gõ tay vào máy tính / tablet.
- Ưu điểm: Không cần phần cứng đặc biệt.
- Nhược điểm: Lỗi nhập tay (~5–15% typo rate), chậm (~15–30 giây / xe chỉ cho bước nhập), không scale được giờ cao điểm.

**Baseline B — Sensor-only (IR / Loop Detector):**
- Cảm biến hồng ngoại hoặc vòng từ đếm xe vào/ra, cập nhật tổng số xe.
- Ưu điểm: Tự động, chi phí thấp.
- Nhược điểm: Không biết biển số xe → không tra cứu được booking, không cá nhân hóa, không hỗ trợ billing theo xe cụ thể.

**Đo lường so sánh:**
- Gate entrance latency: Manual ~60–90s, Sensor-only ~45s, **AI-LPR target < 30s**
- Error rate: Manual ~10%, Sensor-only không áp dụng (không có OCR), **AI-LPR < 15% (adverse)**, < 5% (standard)
- Booking lookup: Manual = thủ công tra bảng, Sensor-only = không có, **AI-LPR = tự động 100%**

---

### 2.2 Baseline cho Slot Allocator — Rule-based Allocation

> **Mô tả:** Hệ thống phân bổ slot theo quy tắc cố định, không có AI optimization.

**Baseline A — First-Available:**
- Gán slot đầu tiên tìm thấy còn trống (quét tuần tự từ tầng 1, ô A1 trở đi).
- Không quan tâm đến khoảng cách từ cổng, vị trí thang máy, hay floor preference của Driver.

**Baseline B — Nearest-First (Distance-only):**
- Gán slot gần cổng nhất (chỉ theo khoảng cách, không có reservation awareness).
- Không xử lý xung đột khi nhiều request cùng lúc.

**Baseline C — Manual Allocation (Staff-directed):**
- Nhân viên tự quyết định gán xe vào tầng nào, ô nào dựa trên kinh nghiệm.
- Không nhất quán, phụ thuộc vào con người, không scale được giờ cao điểm.

**Đo lường so sánh (Average Time-to-Park, giây):**

| Method | Low Load | Medium Load | High Load |
|---|---|---|---|
| Manual (Staff) | ~312 ± 41 | ~487 ± 63 | ~731 ± 89 |
| Sensor-only + First-Available | ~201 ± 25 | ~361 ± 42 | ~579 ± 68 |
| Rule-based (Nearest-First) | ~198 ± 22 | ~354 ± 37 | ~562 ± 71 |
| **Proposed (Heuristic Optimized)** | **~155 ± 18** | **~271 ± 29** | **~438 ± 54** |

> Target: Giảm ≥ 20% so với Rule-based baseline tại medium và high load.

---

### 2.3 Baseline cho LLM Smart Parking Assistant — Manual 2D Map Navigation

> **Mô tả:** Không dùng AI assistant. Driver tự xem bản đồ 2D trên App để tìm slot màu xanh (trống) thủ công.

**Baseline — Manual Map Navigation:**
- App hiển thị sơ đồ bãi đỗ dạng 2D grid, slot trống màu xanh, slot đầy màu đỏ.
- Driver cuộn qua các tầng, tự chọn slot.
- Ưu điểm: Đơn giản, không cần AI.
- Nhược điểm: Khó dùng trong bãi đỗ lớn (> 5 tầng, > 100 slot/tầng), dễ gây nhầm lẫn, không gợi ý theo proximity/preference.

**Baseline nâng cao — Filter-based Search:**
- Thanh lọc cứng (filter by floor, slot type) — không có natural language processing.

**Đo lường so sánh:**

| Metric | Manual Map | Filter-based | **AI Assistant (Gemini)** |
|---|---|---|---|
| Avg. time to select slot | ~45 giây | ~25 giây | **< 10 giây** |
| User satisfaction (1–5) | ~2.8 | ~3.4 | **≥ 4.2** |
| First-try accuracy | ~70% | ~80% | **≥ 85%** |

---

### 2.4 Baseline cho Automated Billing — Manual Billing

> **Mô tả:** Không dùng hệ thống tính phí tự động. Nhân viên tính tay hoặc dùng máy tính tay cầm.

**Baseline — Manual Billing (Staff-directed):**
- Nhân viên xem thời gian vào/ra từ sổ ghi tay hoặc máy tính thủ công.
- Tính phí bằng máy tính hoặc bảng tra giá.
- Lỗi tính toán, chậm (~2–5 phút / xe), không tạo receipt tự động.

**Đo lường so sánh:**

| Metric | Manual Billing | **VNPay Automated** |
|---|---|---|
| Time to complete billing | 2–5 phút | **< 30 giây** |
| Error rate | ~8–12% | **< 1%** |
| Digital receipt | Không | **Có (tức thì)** |
| Payment success tracking | Thủ công | **Tự động (IPN callback)** |

---

### 2.5 Baseline cho Manager Analytics — Spreadsheet / Manual Report

> **Mô tả:** Manager xuất dữ liệu raw từ hệ thống cũ (hoặc sổ ghi tay) ra Excel và tự phân tích.

**Baseline — Manual Spreadsheet Analysis:**
- Export CSV từ database → mở Excel → vẽ biểu đồ thủ công.
- Không có insight tự động, không phát hiện bất thường real-time.

**Proposed — Gemini Analytics:**
- Report Service push aggregated data định kỳ → Gemini phân tích → tự động highlight peak hours, underutilised floors, pricing suggestions.
- Dashboard real-time trên Web Admin.

---

## 3. Tóm tắt Baseline vs Proposed

| Bài toán | Baseline | Proposed | Metric cải thiện |
|---|---|---|---|
| Gate identification | Manual entry / Sensor-only | YOLOv8 + CRNN-OCR | Char Acc ≥ 85%; Latency < 30s |
| Slot allocation | First-available / Nearest-first | Heuristic optimizer | TTP giảm ≥ 20% |
| Booking conflicts | None (manual resolution) | Priority queue conflict resolver | Reservation success ≥ 95% |
| Driver slot finding | Manual 2D map | Gemini Function Calling | Satisfaction ≥ 4.2/5; Time < 10s |
| Billing | Manual staff billing | VNPay automated | Error < 1%; Time < 30s |
| Manager analytics | Spreadsheet | Gemini Analytics | Automated insights, real-time |

---

## 4. Ghi chú Triển khai Baseline

Để đảm bảo so sánh công bằng (fair comparison):
- Baseline rule-based được implement trên cùng cơ sở hạ tầng backend (Node.js) — chỉ thay đổi logic allocator.
- Thử nghiệm cùng kịch bản simulation (low / medium / high load) và cùng dataset.
- Mỗi kịch bản chạy n = 10 lần với random seeds khác nhau; báo cáo Mean ± SD.
