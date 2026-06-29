# Luồng xử lý dữ liệu (Data Flow)

Dưới đây là mô tả luồng xử lý chính cho các nghiệp vụ cốt lõi của Parking Building Management System:

---

## 1. Luồng Check-in (Xe vào bãi) — **AI-LPR Path**

> AI-LPR là bước xử lý cốt lõi tại cổng vào.

```
Xe tiến vào cổng
      │
      ▼
[Gate Camera] chụp frame
      │
      ▼
[AI-LPR: YOLOv8 + CRNN-OCR]
 → Phát hiện biển số (Detection)
 → Đọc ký tự biển số (Recognition)
 → Output: {"plate":"51A-123.45", "confidence":0.91, ...}
      │ REST POST (< 200ms)
      ▼
[Backend — Parking Service]
 ├─ Tra cứu vehicles collection (plate có trong hệ thống?)
 ├─ Tra cứu bookings (có đặt chỗ trước không?)
 ├─ Gọi Slot Allocator → chọn slot tối ưu s*
 └─ Tạo parkingSessions record (status: In-Progress)
      │
      ├─ WebSocket broadcast → cập nhật slot state "Occupied"
      │   → Web Admin + Mobile App real-time update
      │
      ├─ Phản hồi Gate Terminal → Mở barrier
      │
      └─ Cấp QR Ticket → Mobile App của Driver (nếu có tài khoản)
```

**Bước chi tiết:**
1. **Tiếp cận:** Xe của Driver tiến vào cổng bãi đỗ.
2. **AI-LPR:** Camera tại cổng chụp frame → YOLOv8 phát hiện vùng biển số → CRNN-OCR đọc chuỗi ký tự.
3. **Gửi yêu cầu:** Terminal gửi JSON payload lên Backend (plate string + confidence + gate_id).
4. **Xử lý Backend (Parking Service):**
   * Xác thực plate trong `vehicles`, tra cứu `bookings`.
   * Kích hoạt **Slot Allocator**: chọn slot tối ưu theo hàm mục tiêu.
   * Tạo bản ghi mới trong `parkingSessions` (status: *In-Progress*).
5. **Cập nhật Real-time:** WebSocket phát broadcast cập nhật slot state sang "Đã có xe" đến tất cả Client.
6. **Phản hồi:** Gửi lệnh mở barrier đến Gate Terminal; cấp QR Ticket về Mobile App.

---

## 2. Luồng Đặt chỗ trước (Advance Booking)

1. **Tìm kiếm / AI Assistant:** Driver mở Mobile App → chat với AI Parking Assistant (Gemini) bằng ngôn ngữ tự nhiên HOẶC xem bản đồ slot 2D. App gọi API lấy danh sách slot trống theo thời gian thực.
2. **Chọn chỗ:** Driver chọn slot và thời gian. App gửi Booking Request lên Backend.
3. **Ghi nhận & Giữ chỗ:** Parking Service lưu vào `bookings`, **lock (reserve)** slot đó — slot chuyển trạng thái "Reserved" qua WebSocket broadcast.
4. **Xác nhận:** Trả về QR Code Booking về Mobile App của Driver.

---

## 3. Luồng Check-out và Thanh toán (Xe ra bãi)

```
Xe tiến ra cổng
      │
      ▼
[Gate Camera] chụp frame
      │ (hoặc Driver quét QR Code)
      ▼
[AI-LPR] nhận diện biển số ra
      │ REST POST
      ▼
[Backend — Parking Service]
 └─ Tra cứu parkingSessions đang mở theo plate/QR
      │
      ▼
[Payment Service]
 ├─ Tính phí: (checkout_time - checkin_time) × rate
 ├─ Tạo VNPay payment request
 └─ Chờ IPN Callback từ VNPay
      │
      ▼
[Sau IPN Callback "Success"]
 ├─ Cập nhật payments collection
 ├─ Cập nhật parkingSessions → "Completed"
 ├─ WebSocket broadcast → slot state "Vacant"
 └─ Lệnh mở barrier → Gate Terminal
```

**Bước chi tiết:**
1. **Ra cổng:** Camera tại cổng ra nhận diện lại biển số (AI-LPR) hoặc Driver quét QR Ticket.
2. **Xác định phiên:** Tìm `parkingSessions` đang mở tương ứng.
3. **Tính phí:** Parking Service tính thời gian đỗ thực tế × bảng giá → Payment Service.
4. **Thanh toán:** Tạo VNPay request → Driver thanh toán qua App → VNPay gửi IPN Callback.
5. **Hoàn tất:** Cập nhật records → WebSocket broadcast slot "Trống" → Mở barrier.

---

## 4. Luồng AI Parking Assistant (Dành cho Driver)

```
Driver nhập query: "Tìm chỗ gần thang máy tầng 2"
      │ (Mobile App)
      ▼
[Backend — Gemini API call]
 ├─ Fetch available slots từ MongoDB (context JSON)
 ├─ Gọi Gemini: query + slot context
 └─ Gemini Function Calling:
    → find_slot({floor: 2, proximity: "elevator"})
      │
      ▼
[Slot Allocator] trả về slot_id tối ưu
      │
      ▼
Gemini response: {slot_id: "B2-045", floor: 2, message: "Tôi tìm được chỗ B2-045 gần thang máy..."}
      │
      ▼
Mobile App: Highlight slot B2-045 trên bản đồ + hiển thị text response
```

---

## 5. Luồng Phân tích & Báo cáo (Dành cho Manager)

1. **Gom dữ liệu:** Định kỳ, `Report Service` truy vấn dữ liệu từ các collections (`sessions`, `payments`, `bookings`).
2. **AI Analytics:** Dữ liệu tổng hợp (anonymised) gửi đến **Gemini API** để phân tích: peak hours, underutilised floors, pricing suggestions, occupancy trends.
3. **Hiển thị:** Kết quả phân tích + biểu đồ thống kê được render trên **Web Admin Dashboard** cho Manager.

---

## 6. Tóm tắt các luồng dữ liệu chính

| Luồng | AI component | Input | Output | Latency target |
|---|---|---|---|---|
| Check-in | AI-LPR (YOLOv8 + CRNN) | Camera frame | Plate string + barrier open | < 30s (gate-to-barrier) |
| Check-out | AI-LPR + Payment Service | Camera frame / QR | Billing + barrier open | < 30s |
| Slot Allocation | Heuristic Allocator | Available slots + weights | Optimal slot s* | < 1s |
| Smart Search | Gemini Function Calling | Text query + slot JSON | Slot recommendation | < 2s |
| Analytics | Gemini Analytics | Aggregated session data | Natural language report | async |
