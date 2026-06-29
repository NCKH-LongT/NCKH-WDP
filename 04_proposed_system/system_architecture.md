# Kiến trúc Hệ thống (System Architecture)

## 1. Kiến trúc Tổng thể (Frontend / Backend / Database / AI Service)
Hệ thống được thiết kế theo kiến trúc Client-Server hiện đại, bổ sung tầng **AI Service** riêng biệt phục vụ hai chức năng AI cốt lõi: AI-LPR tại cổng và LLM Assistant trên Mobile App.

```
┌─────────────────────────────────────────────────────────────┐
│                      CLIENT LAYER                           │
│  ┌───────────────┐  ┌──────────────────┐  ┌─────────────┐  │
│  │  Web Admin    │  │   Mobile App     │  │   Gate      │  │
│  │ (Next.js/     │  │ (React Native/   │  │  Terminal   │  │
│  │  React)       │  │  Expo)           │  │  (Camera UI)│  │
│  └───────┬───────┘  └────────┬─────────┘  └──────┬──────┘  │
└──────────│──────────────────│───────────────────│──────────┘
           │    HTTPS/REST + WebSocket             │
┌──────────▼──────────────────▼───────────────────▼──────────┐
│                   BACKEND LAYER (Node.js / Express)         │
│  ┌──────────┐  ┌───────────────┐  ┌──────────┐  ┌────────┐ │
│  │Auth Svc  │  │ Parking Svc   │  │Payment   │  │Report  │ │
│  │(JWT/RBAC)│  │(Slots/Session │  │Svc(VNPay)│  │Svc     │ │
│  │          │  │ /Booking/     │  │          │  │        │ │
│  │          │  │  Allocator)   │  │          │  │        │ │
│  └──────────┘  └──────┬────────┘  └──────────┘  └───┬────┘ │
└─────────────────────── │──────────────────────────── │ ─────┘
                          │ MongoDB                    │
┌─────────────────────────▼────────────────────────────▼──────┐
│                      DATABASE (MongoDB)                      │
│  users │ parkingSlots │ parkingSessions │ bookings │vehicles │
│  payments                                                    │
└──────────────────────────────────────────────────────────────┘
           ▲ REST calls                   ▲ REST calls
┌──────────┴──────────────────────────────┴──────────────────┐
│                      AI SERVICE LAYER                       │
│                                                             │
│  ┌───────────────────────────────────────┐                  │
│  │  AI-LPR Pipeline (Primary AI)        │                  │
│  │  ┌─────────────┐  ┌────────────────┐  │                  │
│  │  │ YOLOv8      │  │ CRNN-OCR       │  │                  │
│  │  │ (Plate      │→ │ (BiLSTM +      │  │                  │
│  │  │  Detection) │  │  CTC Decoder)  │  │                  │
│  │  └─────────────┘  └────────────────┘  │                  │
│  │  Runs on: Gate Terminal / Edge Server │                  │
│  └───────────────────────────────────────┘                  │
│                                                             │
│  ┌───────────────────────────────────────┐                  │
│  │  LLM Assistant (Secondary AI)        │                  │
│  │  Google Gemini API                    │                  │
│  │  Function Calling + RAG               │                  │
│  │  → Slot Guidance (Mobile App)         │                  │
│  │  → Manager Analytics (Web Admin)      │                  │
│  └───────────────────────────────────────┘                  │
└─────────────────────────────────────────────────────────────┘
```

### Client (Frontend)
* **Web Admin:** Xây dựng bằng **Next.js / React JS**. Phục vụ Manager/Staff UI để quản lý slot, lượt xe, doanh thu và báo cáo AI-generated insights.
* **Mobile App:** Xây dựng bằng **React Native / Expo**. Phục vụ Driver Portal: xem chỗ trống, đặt chỗ, chat với AI Parking Assistant, thanh toán, lịch sử giao dịch.
* **Gate Terminal:** Giao diện tại cổng — hiển thị kết quả AI-LPR (biển số nhận diện được), trạng thái cổng, và nút override thủ công.

### Server (Backend)
* Xây dựng dựa trên **Node.js** và **Express.js**.
* Giao tiếp với Client qua **HTTPS / REST API** và **WebSocket** (real-time slot updates).
* **Các Service chính:**
  * `Auth Service`: Xử lý xác thực và phân quyền bằng **JWT** (4 vai trò: Manager, Staff, Driver, Admin).
  * `Parking Service`: Quản lý slot state, parking sessions, booking lifecycle + **Slot Allocator** (heuristic optimization).
  * `Payment Service`: Tính phí tự động và tích hợp **VNPay** (IPN Callback).
  * `Report Service`: Tổng hợp dữ liệu, push sang Gemini Analytics API, render dashboard.

### Database
* **MongoDB** (NoSQL).
* Collections: `users`, `parkingSlots`, `parkingSessions`, `bookings`, `payments`, `vehicles`.

### Hạ tầng và Triển khai (Deployment)
* Mã nguồn: **GitHub** + CI/CD qua **GitHub Actions**.
* Frontend Web/Admin: **Vercel**.
* Backend Services: **Render**.

---

## 2. AI Service Layer: Chi tiết tích hợp

### 2.1 AI-LPR (Primary AI — AI chính)

| Thuộc tính | Chi tiết |
|---|---|
| **Model** | YOLOv8n (detection) + CRNN-OCR (recognition) |
| **Chạy trên** | Gate Terminal / Edge server tại cổng |
| **Input** | Camera frame (JPEG/video stream) |
| **Output** | JSON: `{plate, confidence, timestamp, gate_id}` |
| **Latency target** | < 200 ms (LPR inference) + < 30s (gate-to-barrier) |
| **Tích hợp** | Gate Terminal → REST POST → Backend Parking Service → Slot Allocator → Barrier open |

**Ứng dụng thực tế:**
* **Check-in tự động**: Camera nhận diện biển số → tra cứu booking → gán slot → mở barrier → cấp QR ticket.
* **Check-out tự động**: Camera nhận diện biển số ra → tra cứu session → kích hoạt Payment Service → đóng session → mở barrier.

### 2.2 Slot Allocator (Heuristic Optimization)

Allocator chọn slot tối ưu `s*` theo hàm mục tiêu:

```
s* = argmin { α·d(s, gate) + β·d(s, elevator) + γ·[floor(s) ≠ f_pref] }
     s ∈ A (available, non-reserved slots)

Trọng số mặc định: α=0.5, β=0.3, γ=0.2
Latency target: < 1 giây / request
```

### 2.3 LLM Parking Assistant (Secondary AI)

| Thuộc tính | Chi tiết |
|---|---|
| **Model** | Google Gemini (via Google AI Studio SDK) |
| **Kỹ thuật** | Function Calling + RAG |
| **Input** | Text query (Mobile App) + JSON slot context |
| **Output** | Structured JSON (slot_id, floor, direction) + Natural Language response |
| **Ứng dụng** | Driver: tìm chỗ bằng ngôn ngữ tự nhiên; Manager: báo cáo phân tích vận hành |

**Ứng dụng thực tế:**
* **Smart Assistant (Driver)**: *"Tìm chỗ gần thang máy tầng 2"* → Gemini Function Call → `find_slot({floor:2, proximity:"elevator"})` → highlight slot trên bản đồ Mobile App.
* **Manager Insights**: Report Service push aggregated data → Gemini phân tích peak hours, underutilised floors, pricing suggestions → render trên Web Admin dashboard.
