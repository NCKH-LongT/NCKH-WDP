# Bước 8: Chọn model AI và mô tả cách tích hợp

Hệ thống sử dụng **hai tầng AI** phục vụ hai bài toán khác nhau:

---

## 🎯 AI Chính — AI-LPR (Automatic License Plate Recognition)

> Đây là AI cốt lõi trong vòng đời Check-in / Check-out của hệ thống bãi đỗ xe.

| Nội dung | Phân tích và Quyết định |
| --- | --- |
| **Model dùng là gì?** | Pipeline 2 giai đoạn: **(1) YOLOv8** (object detection — phát hiện biển số) + **(2) CRNN-OCR** (Convolutional Recurrent Neural Network — đọc ký tự biển số bằng CTC decoder). |
| **Vì sao chọn model này?** | YOLOv8 là kiến trúc SOTA cho real-time detection, nhỏ gọn (nano variant), chạy được trên edge/camera. CRNN+CTC là chuẩn công nghiệp cho nhận dạng ký tự tuần tự (sequential OCR) — phù hợp với cấu trúc chuỗi ký tự biển số Việt Nam. Kết hợp 2 model cho phép xử lý toàn bộ pipeline từ frame camera đến chuỗi biển số trong < 200 ms. |
| **Model lấy từ đâu?** | - **YOLOv8**: Ultralytics (open-source, fine-tune trên tập biển số Việt Nam từ Kaggle/Roboflow + 800 ảnh chụp tại bãi đỗ thực tế TP.HCM).<br>- **CRNN-OCR**: Cài đặt custom dựa trên kiến trúc CRNN cổ điển (Shi et al., 2016) + bộ dữ liệu ký tự biển số Việt Nam. Tham khảo từ bài báo *"Advanced Machine Learning-Driven Automated Multi-Level Parking System"* (IEEE 2024) — đạt 98.21% spatial accuracy khi dùng Region-based CNN cho nhận diện biển số tại cổng. |
| **Input của model là gì?** | Frame video/ảnh từ **camera cố định tại cổng vào/ra** của bãi đỗ (gate camera). Preprocessing: resize, normalization, augment (brightness, blur, rotation ±25°). |
| **Output của model là gì?** | Chuỗi ký tự biển số (VD: `"51A-123.45"`), confidence score, timestamp, gate_id — đóng gói JSON gửi về Backend qua REST API. |
| **Cách tích hợp vào app?** | Chạy trên **Gate Terminal** hoặc **Edge server** tại cổng. Backend Node.js nhận payload JSON từ LPR module, tra cứu `vehicles` + `bookings`, kích hoạt **Slot Allocator** và mở barrier. Round-trip latency target: < 200 ms (P95). |
| **Có baseline không?** | **Có. Baseline là Sensor-only + Manual Entry**: Thay vì camera AI, nhân viên nhập biển số thủ công hoặc dùng cảm biến IR đếm xe (không nhận dạng biển số). AI-LPR giảm lỗi nhập liệu, tăng tốc check-in và cho phép tự động tra cứu thông tin đặt chỗ trước (booking lookup). |
| **KPI mục tiêu** | Character-level accuracy ≥ 85% (điều kiện ánh sáng chuẩn); Gate entrance latency < 30 giây (từ khi xe đến cổng đến khi barrier mở). |

### Pipeline AI-LPR Chi Tiết

```
Camera Frame
     │
     ▼
[YOLOv8 Detector]
 → Plate Bounding Box (IoU≥0.45, Conf≥0.60)
     │
     ▼
[Crop + Resize 100×32px]
     │
     ▼
[CRNN-OCR]
 ├─ CNN Backbone (4 conv blocks + BN + MaxPool)
 ├─ BiLSTM (2 layers, 256 hidden units)
 └─ CTC Decoder (beam search)
     │
     ▼
Plate String: "51A-123.45"  (confidence: 0.91)
     │
     ▼
REST POST → Backend Parking Service
```

---

## 🤖 AI Phụ — LLM Smart Parking Assistant (Google Gemini)

> Hỗ trợ Driver tìm chỗ đỗ và Manager phân tích dữ liệu vận hành.

| Nội dung | Phân tích và Quyết định |
| --- | --- |
| **Model dùng là gì?** | **Google Gemini** kết hợp kỹ thuật **Function Calling** và **RAG (Retrieval-Augmented Generation)**. |
| **Vì sao chọn model này?** | LLM giúp người dùng tìm chỗ đỗ bằng ngôn ngữ tự nhiên (VD: *"Tìm giúp tôi chỗ gần thang máy tầng 2"*). Function Calling cho phép Gemini mapping câu lệnh với dữ liệu slot thời gian thực mà không cần người dùng thao tác thủ công trên bản đồ 2D. |
| **Model lấy từ đâu?** | **Google AI Studio** (REST API / SDK chính thức). Cảm hứng từ kiến trúc PTAS của Chang et al. (2026) — kết hợp YOLO + LLM (GPT-4o, Claude, Gemini) để phân tích ngữ nghĩa dữ liệu giao thông đa phương thức. |
| **Input của model là gì?** | **(1) Text**: Câu truy vấn của người dùng từ Mobile App.<br>**(2) JSON Context**: Danh sách slot trống (slot_id, floor, tọa độ, khoảng cách thang máy) nạp vào làm context. |
| **Output của model là gì?** | JSON structured `{slot_id, floor, direction, message}` để Mobile App render highlight trên bản đồ + phản hồi text tự nhiên. |
| **Cách tích hợp vào app?** | Node.js Backend gọi Gemini API kết hợp dữ liệu slot từ MongoDB, trả kết quả về Mobile App. Manager nhận báo cáo dạng ngôn ngữ tự nhiên (peak hours, underutilised floors) trên Web Admin dashboard. |
| **Có baseline không?** | **Có. Baseline là Manual Map**: Người dùng tự xem sơ đồ 2D trên App và chọn slot màu xanh (trống) thủ công. |

---

## 📊 Tóm tắt So sánh 2 AI Components

| Thuộc tính | AI-LPR (Primary) | Gemini Assistant (Secondary) |
|---|---|---|
| **Mục đích** | Check-in/out tự động | Tìm chỗ & báo cáo |
| **Loại AI** | Computer Vision + OCR | LLM + Function Calling |
| **Input** | Camera frame (image) | Text + JSON context |
| **Output** | Plate string JSON | Slot recommendation JSON + Text |
| **Tích hợp** | Edge/Gate Terminal → REST → Backend | Mobile App → Backend → Gemini API |
| **Latency target** | < 200 ms (LPR) + < 30s (gate) | < 2s (assistant response) |
| **Baseline** | Manual entry / Sensor-only | Manual 2D map navigation |
