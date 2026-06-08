# Kiến trúc Hệ thống (System Architecture)

## 1. Kiến trúc Tổng thể (Frontend / Backend / Database)
Hệ thống được thiết kế theo kiến trúc Client-Server hiện đại, chia tách rõ ràng giữa giao diện người dùng và xử lý nghiệp vụ:

### Client (Frontend)
* **Web Admin:** Xây dựng bằng **Next.js / React JS**. Phục vụ các giao diện cho Manager/Staff (Manager / Staff UI) để quản lý slot, lượt xe, doanh thu và báo cáo.
* **Mobile App:** Xây dựng bằng **React Native**. Phục vụ Driver Portal để xem chỗ trống, đặt chỗ, thanh toán và lịch sử giao dịch.
* **Gate Terminal:** Ứng dụng/Giao diện tại cổng dùng để nhập/quét biển số, quét QR code check-in/out.

### Server (Backend)
* Được xây dựng dựa trên **Node.js** và **Express.js**.
* Giao tiếp với Client qua giao thức **HTTPS / REST API** và sử dụng **WebSocket** để cập nhật trạng thái chỗ trống theo thời gian thực (Real-time).
* **Các Service chính:**
  * `Auth Service`: Xử lý xác thực và phân quyền bằng **JWT**.
  * `Parking Service`: Quản lý chỗ trống (slots), phiên gửi xe (sessions), và phương tiện (vehicles).
  * `Payment Service`: Quản lý tính phí và tích hợp thanh toán (Cổng thanh toán **VNPay**).
  * `Report Service`: Tổng hợp dữ liệu, kết xuất báo cáo doanh thu và lưu lượng.

### Database
* Sử dụng hệ quản trị cơ sở dữ liệu phi cấu trúc **MongoDB**.
* Các collection chính: `users`, `parkingSlots`, `parkingSessions`, `bookings`, `payments`, `vehicles`.

### Hạ tầng và Triển khai (Deployment)
* Quản lý mã nguồn bằng **GitHub**.
* CI/CD thông qua **GitHub Actions**.
* Frontend Web/Admin được host trên **Vercel**.
* Backend Services được deploy trên **Render**.

## 2. AI Service: Tích hợp mô hình AI
Hệ thống tích hợp mô hình trí tuệ nhân tạo để nâng cao trải nghiệm và tối ưu hóa vận hành.

* **AI Model sử dụng:** **Google Gemini**.
* **Cách tích hợp model AI:**
  * **API Integration:** Backend Node.js gọi API trực tiếp đến dịch vụ của Gemini.
  * **Ứng dụng thực tế trong hệ thống:** 
    * **Phân tích dữ liệu & Gợi ý (Data Insights):** Dựa vào lịch sử gửi xe và data thu thập từ `Report Service`, Gemini giúp phân tích hành vi của người dùng, dự báo thời gian cao điểm, và gợi ý cho Manager cách tối ưu hóa bảng giá hoặc phân bổ vị trí.
    * **Hỗ trợ người dùng (Smart Assistant):** Gemini có thể được tích hợp vào Mobile App dưới dạng Chatbot để tự động trả lời các thắc mắc của tài xế về vị trí đỗ, chính sách giá, hoặc hướng dẫn sử dụng.
    * (Tùy chọn nâng cao) Có thể dùng khả năng Multimodal của Gemini để hỗ trợ đối chiếu hình ảnh biển số với text trong các trường hợp nghi ngờ sai lệch nhận diện ở cổng.
