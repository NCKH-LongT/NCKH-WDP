# Luồng xử lý dữ liệu (Data Flow)

Dưới đây là mô tả luồng xử lý chính cho các nghiệp vụ cốt lõi của Parking Building Management System:

## 1. Luồng Check-in (Xe vào bãi)
1. **Tiếp cận:** Xe của người dùng (Driver) tiến vào cổng bãi đỗ.
2. **Nhận diện:** Gate Terminal ghi nhận biển số xe (hoặc người dùng quét mã QR Booking nếu đã đặt trước).
3. **Gửi yêu cầu:** Terminal gửi API Request (thông tin biển số/QR) lên Backend (Node.js).
4. **Xử lý Backend (Parking Service):**
   * Kiểm tra thông tin xe và xác thực (Auth Service).
   * Tìm chỗ trống trong bãi.
   * Tạo bản ghi mới trong collection `parkingSessions` (trạng thái: In-progress).
5. **Cập nhật Real-time:** Dịch vụ WebSocket phát thông báo trạng thái vị trí đỗ vừa được cấp phát (chuyển sang "Đã có xe") đến tất cả Client đang kết nối.
6. **Phản hồi:** Trả kết quả về Gate Terminal (Mở cổng/Barrier) và cấp vé điện tử (QR) về Mobile App của người dùng (nếu là user có app).

## 2. Luồng Đặt chỗ trước (Booking)
1. **Tìm kiếm:** Driver mở Mobile App, hệ thống gọi API để lấy danh sách chỗ trống theo thời gian thực.
2. **Chọn chỗ:** Driver chọn slot và thời gian muốn gửi xe. App gửi request đặt chỗ (Booking Request) lên Backend.
3. **Ghi nhận & Giữ chỗ:** Backend lưu thông tin vào collection `bookings` và tạm khóa (reserve) slot đó trên hệ thống qua `Parking Service`.
4. **Xác nhận:** Trả về một QR Code đại diện cho Booking trên App người dùng.

## 3. Luồng Check-out và Thanh toán (Xe ra khỏi bãi)
1. **Ra cổng:** Người dùng lái xe ra cổng, Gate Terminal quét QR code hoặc nhận diện lại biển số.
2. **Xác định phiên:** Gửi request lên Backend để tìm `parkingSessions` tương ứng đang mở.
3. **Tính phí (Payment Service):** Backend tính toán thời gian đỗ xe thực tế và dựa vào bảng giá để tính tổng số tiền cần thanh toán.
4. **Thanh toán:**
   * Hệ thống tạo yêu cầu thanh toán (Payment Request) chuyển tới cổng thanh toán **VNPay**.
   * Driver thanh toán qua App VNPay hoặc xác nhận trừ tiền trên ví tích hợp.
   * Cổng thanh toán trả về IPN/Callback báo thanh toán thành công.
5. **Hoàn tất:** 
   * Cập nhật bản ghi `payments`.
   * Cập nhật `parkingSessions` thành trạng thái "Hoàn thành" (Closed).
   * WebSocket cập nhật trạng thái slot thành "Trống".
6. **Mở cổng:** Lệnh mở barrier được gửi đến Gate Terminal.

## 4. Luồng Phân tích & Báo cáo (Dành cho Manager)
1. **Gom dữ liệu:** Định kỳ, `Report Service` truy vấn dữ liệu từ các collection (sessions, payments, bookings).
2. **AI Analysis:** Dữ liệu tổng hợp được gửi qua API đến **Gemini AI** để phân tích, trích xuất xu hướng, đánh giá công suất hoạt động.
3. **Hiển thị:** Dữ liệu phân tích và biểu đồ thống kê (doanh thu, lượt xe) được trả về qua API và render trên Web Admin cho Manager xem và đánh giá.
