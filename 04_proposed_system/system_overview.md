# Tổng quan Hệ thống (System Overview)

## 1. Mục tiêu hệ thống
**Parking Building Management System** hướng tới việc số hóa toàn bộ vòng đời của một lượt gửi xe: từ lúc xe vào cổng đến khi ra khỏi bãi. Hệ thống bao gồm việc quản lý chỗ trống theo thời gian thực, tính phí tự động, báo cáo doanh thu chi tiết và phân quyền chặt chẽ theo từng vai trò cụ thể.

## 2. Người dùng chính (Actors) và Trách nhiệm
Hệ thống được thiết kế phục vụ 4 nhóm người dùng chính:
* **Parking Manager (Quản lý bãi đỗ):** Quản lý cấu hình bãi đỗ/tòa nhà (thiết lập tầng, loại xe, bảng giá) và xem báo cáo tổng hợp (doanh thu, lưu lượng).
* **Parking Staff (Nhân viên bãi đỗ):** Xử lý các nghiệp vụ tại cổng (check-in, check-out) và giải quyết các trường hợp ngoại lệ.
* **Driver / User (Người lái xe/Khách hàng):** Tìm kiếm và xem trạng thái chỗ trống, đặt chỗ trước, nhận vé (mã QR), theo dõi lịch sử gửi xe và thực hiện thanh toán.
* **System Admin (Quản trị hệ thống):** Quản lý tài khoản toàn hệ thống, cấu hình tham số cốt lõi và phân quyền người dùng.

## 3. Chức năng chính
* **Quản lý bãi đỗ & Chỗ trống (Parking Service):** Theo dõi trạng thái từng vị trí đỗ xe theo thời gian thực.
* **Xử lý xe vào/ra (Gate Terminal):** Ghi nhận thông tin xe vào/ra thông qua việc nhập biển số hoặc quét mã QR.
* **Quản lý phiên gửi xe (Session Management):** Ghi nhận thời gian bắt đầu và kết thúc của một lượt gửi xe để phục vụ tính phí.
* **Đặt chỗ trước (Booking):** Cho phép Driver đặt chỗ trước thông qua Mobile App.
* **Thanh toán trực tuyến (Payment):** Tích hợp cổng thanh toán VNPay để tự động tính và thu phí gửi xe.
* **Báo cáo & Thống kê (Report Service):** Xuất các báo cáo doanh thu, biểu đồ lưu lượng xe cho Manager.
* **Trợ lý thông minh (AI Integration):** Tích hợp AI (Gemini) để hỗ trợ phân tích dữ liệu, gợi ý hệ thống hoặc hỗ trợ người dùng.

## 4. Dữ liệu đầu vào
* **Thông tin định danh:** Biển số xe, mã QR vé xe.
* **Hành động người dùng:** Yêu cầu đặt chỗ (thời gian, vị trí), yêu cầu check-in/check-out.
* **Dữ liệu cấu hình:** Bảng giá dịch vụ, sơ đồ bãi đỗ.
* **Dữ liệu tài khoản:** Thông tin đăng nhập, hồ sơ cá nhân của nhân viên và người dùng.

## 5. Output của hệ thống
* **Đối với Driver/User:** Vé gửi xe điện tử (QR Code), biên lai thanh toán thành công, thông báo trạng thái chỗ đỗ.
* **Đối với Staff/Gate Terminal:** Tín hiệu mở cổng (Barrier), cảnh báo lỗi/ngoại lệ.
* **Đối với Manager:** Dashboard thống kê trực quan (báo cáo doanh thu, công suất sử dụng bãi đỗ).
