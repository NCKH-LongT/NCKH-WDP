# Dataset (Nguồn Dữ liệu)

Hệ thống PBMS sử dụng dữ liệu cho **hai thành phần AI** chính: AI-LPR (nhận dạng biển số) và Slot Allocator (phân bổ chỗ đỗ). Phần LLM (Gemini) không cần training data riêng vì sử dụng pre-trained model qua API.

---

## 1. Dataset cho AI-LPR (YOLOv8 + CRNN-OCR)

### 1.1 Nguồn dữ liệu công khai (Public Datasets)

| Dataset | Mô tả | Số lượng | Nguồn |
|---|---|---|---|
| **Vietnamese License Plate (Kaggle)** | Ảnh biển số xe máy và ô tô Việt Nam, nhiều loại nền/ánh sáng | ~6,500 ảnh | [Kaggle — Vietnamese LP](https://www.kaggle.com/) |
| **Roboflow Vietnamese LP** | Biển số Việt Nam đã được annotate (YOLO format) với bounding boxes | ~2,000 ảnh | [Roboflow Universe](https://universe.roboflow.com/) |
| **CNRPark + EXT** | Ảnh bãi đỗ xe với nhãn trạng thái slot (trống/đầy) — dùng để đánh giá occupancy | ~144,965 ảnh | [CNRPark Dataset](http://cnrpark.it/) |
| **PKLot** | Ảnh bãi đỗ xe từ Brazil (2 bãi, nhiều điều kiện thời tiết), nhãn slot occupancy | ~695,899 patches | [PKLot Dataset](https://web.inf.ufpr.br/vri/databases/parking-lot-database/) |

### 1.2 Dữ liệu thu thập cục bộ (Local Collection)

| Nguồn | Mô tả | Số lượng | Ghi chú |
|---|---|---|---|
| **Camera cổng bãi đỗ TP.HCM** | Video/frame từ camera cố định tại cổng vào/ra, chụp biển số xe Việt Nam trong điều kiện thực tế | ~800 ảnh (~30 video clips) | Đã ghi nhãn thủ công (plate string + bounding box) |
| **Simulation environment** | Kịch bản multi-level parking được mô phỏng để kiểm thử allocator (custom simulator / SUMO) | N/A | Dữ liệu synthetic cho allocation scenarios |

### 1.3 Điều kiện thu thập (Collection Conditions)

| Điều kiện | Mô tả | Mục đích |
|---|---|---|
| Standard lighting | Ánh sáng trong nhà 300–500 lux | Training chính + benchmark |
| Night / Low light | < 50 lux, camera hồng ngoại | Test robustness của LPR |
| Direct glare | Đèn chiếu thẳng vào camera | Test adversarial condition |
| Partial occlusion | Biển số bị che một phần | Test detection recall |
| Oblique angle | Góc nghiêng ±15°, ±25° | Test CRNN OCR accuracy |

### 1.4 Augmentation (Data Augmentation)

Để tăng cường dataset training, áp dụng các biến đổi:

| Augmentation | Tham số |
|---|---|
| Brightness jitter | ±30% |
| Gaussian blur | kernel 3×3, sigma 0–1.5 |
| Random rotation | ±25° |
| Horizontal flip | 50% probability |
| Mosaic augmentation | 4-image mosaic (YOLOv8 default) |
| CLAHE | Contrast Limited Adaptive Histogram Equalization |

---

## 2. Dataset Splits cho AI-LPR

| Split | Tỷ lệ | Mô tả |
|---|---|---|
| **Train** | 70% | Dùng để huấn luyện YOLOv8 detector và CRNN-OCR |
| **Validation** | 10% | Theo dõi loss, điều chỉnh hyperparameters, early stopping |
| **Test** | 20% | Đánh giá cuối cùng — độc lập, không dùng trong training |

> **Lưu ý:** Dữ liệu cục bộ (800 ảnh) được giữ hoàn toàn trong test split để đánh giá real-world performance riêng biệt, không trộn với train split.

---

## 3. Dataset cho Slot Allocator (Simulation)

Slot allocator không cần dataset training (heuristic-based), nhưng cần **kịch bản simulation** để đánh giá:

| Kịch bản | Occupancy | Số xe / giờ | Số booking đồng thời | Số lần chạy |
|---|---|---|---|---|
| Low load | < 40% | 10–30 xe/h | 0–5 | n = 10 |
| Medium load | 40–70% | 30–80 xe/h | 5–20 | n = 10 |
| High / Peak | > 80% | 80–150 xe/h | 20–50 | n = 10 |
| Night (adverse) | Any | 5–15 xe/h | 0–5 | n = 10 |

**Tham số bãi đỗ giả định (simulation environment):**
- 5 tầng (Floors B1, B2, 1, 2, 3)
- 50 slot / tầng → 250 slot tổng
- 2 cổng vào/ra
- 1 thang máy / tầng tại vị trí cố định

---

## 4. Dataset cho Đánh giá LLM Assistant

Vì Gemini là pre-trained model, không cần training dataset. Tuy nhiên cần **evaluation dataset**:

| Loại | Mô tả | Số lượng |
|---|---|---|
| **Query-Answer pairs (Manual)** | Tập câu hỏi mẫu của Driver (tiếng Việt + tiếng Anh) với ground-truth slot recommendation được annotate bởi chuyên gia | 50 cặp |
| **User survey** | Bảng khảo sát 5 điểm gửi đến người dùng thực tế sau khi dùng AI Assistant | n = 20 người dùng |

**Mẫu Query-Answer pairs:**

| Query | Expected Function Call | Expected Slot |
|---|---|---|
| "Tìm chỗ gần thang máy tầng 2" | `find_slot({floor:2, proximity:"elevator"})` | Slot gần thang máy nhất tầng 2 |
| "Cho tôi chỗ ô tô ở tầng dưới cùng" | `find_slot({floor:"B1", vehicle_type:"car"})` | Slot loại car, tầng B1 |
| "Còn chỗ nào trống không?" | `get_available_slots({})` | Danh sách slot trống tất cả tầng |

---

## 5. Tóm tắt Dataset

| Thành phần | Dataset chính | Kích thước | Loại |
|---|---|---|---|
| YOLOv8 Plate Detection | Kaggle VN LP + Roboflow + Local | ~9,300 ảnh | Public + Local |
| CRNN-OCR | Kaggle VN LP + Local | ~7,300 ảnh | Public + Local |
| Occupancy benchmark | CNRPark + PKLot | ~840K patches | Public |
| Slot Allocator evaluation | Custom simulation | 4 kịch bản × 10 runs | Synthetic |
| LLM Assistant evaluation | Manual annotation + User survey | 50 Q&A pairs + 20 users | Manual |
