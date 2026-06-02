# Dữ liệu

## 1. Tổng quan Yêu cầu Dữ liệu

| Thành phần | Dữ liệu cần có | Kích thước | Nguồn |
|---|---|---|---|
| Đánh giá email | Kịch bản cuộc thi (các trường ngữ cảnh) | 80 cặp kịch bản (20 × 4 loại) | Mô phỏng từ cấu trúc cuộc thi thực |
| Baseline email | Email viết tay cho 80 kịch bản | 80 email | Viết bởi 2–3 nhân viên quản trị |
| Đánh giá câu hỏi | Bài đánh giá dự án | 30 bài review | Thực tế (từ cuộc thi cũ) hoặc mô phỏng |
| Baseline câu hỏi | Câu hỏi do giám khảo soạn cho 30 bài review | 30 bộ câu hỏi | Viết bởi 3–5 giám khảo có kinh nghiệm |
| Kiểm tra Timeline Agent | Sự kiện mốc mô phỏng | 50 mốc | Kịch bản kiểm thử tổng hợp |
| Nghiên cứu khả năng sử dụng | Người tham gia (3 vai trò) | ≥ 10 mỗi vai trò (30 tổng) | Nhân viên FPT, giám khảo, tình nguyện viên sinh viên |

## 2. Dữ liệu Đánh giá Email

### 2.1. Xây dựng Kịch bản (80 kịch bản tổng)

| Loại Email | Số kịch bản | Biến thể Ngữ cảnh |
|---|---|---|
| Thông báo vào chung kết | 20 | Thay đổi: tên đội, bảng, chủ đề cuộc thi, số đội vào chung kết |
| Nhắc deadline | 20 | Thay đổi: tên đội, số ngày còn lại (1, 3, 5, 7 ngày), cuộc thi |
| Cảnh báo chưa nộp bài | 20 | Thay đổi: tên đội, số giờ còn lại, số thành viên chưa xác nhận |
| Phân công mentor | 20 | Thay đổi: tên đội, tên mentor, chủ đề bảng, kênh họp |

### 2.2. Thu thập Email Baseline

- Cùng 80 kịch bản giao cho 2–3 nhân viên quản trị
- Nhân viên viết email thủ công (không dùng AI) cho từng kịch bản
- Tính giờ: ghi lại thời gian mỗi email để so sánh hiệu quả
- Tổng cộng: 80 email viết tay

## 3. Dữ liệu Câu hỏi Phỏng vấn

### 3.1. Thu thập Bài đánh giá Dự án

**Phương án A: Dữ liệu thực tế (ưu tiên)**

- Thu thập bài đánh giá từ các buổi chấm cuộc thi FPT trước đây
- Ẩn danh hóa: xóa thông tin nhận dạng giám khảo và đội thi
- Mục tiêu: 30 bài đánh giá trên các loại dự án đa dạng

**Phương án B: Dữ liệu mô phỏng (dự phòng nếu không có dữ liệu thực)**

- Tạo bài review có cấu trúc bằng mẫu dựa trên tiêu chí rubric cuộc thi
- Bao gồm nhiều loại dự án: ứng dụng web, mobile, hệ thống AI, IoT
- Được 2 giảng viên xác nhận tính thực tế

### 3.2. Sinh Câu hỏi bằng AI

- Chạy bộ sinh câu hỏi LLM trên 30 bài đánh giá
- Lưu đầu ra: 30 bộ câu hỏi (5–7 câu mỗi bộ, khoảng 150–210 câu tổng)

### 3.3. Baseline Câu hỏi từ Chuyên gia

- Cùng 30 bài đánh giá giao cho 3–5 giám khảo có kinh nghiệm
- Giám khảo chuẩn bị câu hỏi phỏng vấn như thường lệ (tính giờ)
- Tổng cộng: 30 bộ câu hỏi từ chuyên gia

## 4. Dữ liệu Kiểm tra Timeline Agent

- 50 sự kiện mốc tổng hợp trên 5 cấu hình cuộc thi mô phỏng
- Mỗi mốc có: thoi_gian_du_kien, hanh_dong_mong_doi
- Mốc được dịch thời gian để kích hoạt trong cửa sổ kiểm thử 1 giờ
- Đo lường: thoi_gian_thuc_te vs. thoi_gian_du_kien, ket_qua_hanh_dong

## 5. Người tham gia Nghiên cứu Khả năng Sử dụng

| Vai trò | Số người | Tuyển dụng |
|---|---|---|
| Quản trị viên | ≥ 10 | Nhân viên FPT quản lý cuộc thi |
| Giám khảo / Mentor | ≥ 10 | Giảng viên FPT có kinh nghiệm chấm thi |
| Thí sinh | ≥ 10 | Sinh viên FPT đã tham gia cuộc thi |
| **Tổng** | **≥ 30** | |

### 5.1. Tác vụ Người tham gia

- Admin: tạo cuộc thi, xem xét email AI, duyệt và gửi
- Giám khảo: nhập review, xem câu hỏi AI, hoàn thành chấm điểm
- Thí sinh: đăng nhập, xem cổng thông tin, điều hướng thông tin đội/chủ đề/countdown

## 6. Quyền riêng tư và Đạo đức Dữ liệu

- Tất cả dữ liệu thực tế được ẩn danh hóa (tên đội, tên giám khảo thay bằng mã)
- Kịch bản email dùng tên đội và mentor hư cấu
- Bài đánh giá được loại bỏ danh tính trước khi đánh giá
- Người tham gia nghiên cứu khả năng sử dụng ký đồng ý tham gia có thông tin
- Không lưu trữ dữ liệu cá nhân sau khi kết thúc nghiên cứu

## 7. Ghi chú về Tính sẵn có của Dữ liệu

> Nếu không có bài đánh giá cuộc thi thực tế từ FPT, dữ liệu mô phỏng sẽ được sử dụng. Dữ liệu mô phỏng được xây dựng dưới sự giám sát của giảng viên, dùng rubric cuộc thi thực tế và tuân theo các mẫu thực tế quan sát được trong các cuộc thi trước đây. Cách tiếp cận này phù hợp với thực hành được chấp nhận trong nghiên cứu đánh giá hệ thống AI ứng dụng.
