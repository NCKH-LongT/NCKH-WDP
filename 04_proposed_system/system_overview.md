# Tổng quan Hệ thống

## 1. Tên Hệ thống

**ACMS-AI** — Hệ thống Quản lý Cuộc thi Học thuật Tích hợp AI (AI-Enhanced Academic Competition Management System)

## 2. Mục đích

ACMS-AI là nền tảng web được thiết kế để quản lý vòng đời đầy đủ của các cuộc thi học thuật (hackathon, cuộc thi nghiên cứu, triển lãm dự án) tại Đại học FPT. Hệ thống tích hợp các khả năng AI để tự động hóa truyền thông quản trị, thực thi timeline cuộc thi chính xác và hỗ trợ giám khảo chuẩn bị cho buổi vấn đáp.

## 3. Đề xuất Giá trị Cốt lõi

| Không có ACMS-AI | Có ACMS-AI |
|---|---|
| Giám sát deadline thủ công | Timeline Agent tự động thực thi mốc đúng giờ |
| Quản trị viên tự soạn từng email thông báo | LLM sinh email phù hợp ngữ cảnh cho từng mốc |
| Giám khảo tự soạn câu hỏi phỏng vấn | LLM sinh câu hỏi phù hợp từ bài đánh giá của từng đội |
| Công cụ rời rạc (bảng tính, email, form) | Nền tảng thống nhất bao phủ toàn bộ vòng đời cuộc thi |
| Chất lượng truyền thông không đồng nhất | Thông báo chuẩn hóa, chính xác về mặt ngữ cảnh |

## 4. Vai trò Người dùng Chính

| Vai trò | Quyền truy cập | Hành động chính |
|---|---|---|
| **Quản trị viên** | Toàn bộ hệ thống | Tạo cuộc thi, cấu hình mốc thời gian, phân bảng, xem xét email AI, truy cập dữ liệu lịch sử |
| **Thí sinh / Đội thi** | Cổng thông tin xem (Gmail SSO) | Xem thông tin đội, bảng thi, chủ đề được giao, countdown, nhận thông báo email |
| **Mentor / Giám khảo** | Giao diện giám khảo (xác thực email FPT) | Review bài nộp, nhập điểm, xem câu hỏi phỏng vấn AI, theo dõi tiến độ chấm |

## 5. Các Module Chính

| Module | Mô tả |
|---|---|
| Thiết lập Cuộc thi | Quản trị viên tạo cuộc thi: tên, mốc timeline, số bảng, chủ đề mỗi bảng |
| Đăng ký Đội thi | Form đăng ký trực tuyến; hệ thống gửi email xác nhận đến TẤT CẢ thành viên |
| Quản lý Bảng thi | Tự động chia đội vào bảng; gán chủ đề (Google Drive link hoặc tương tự) |
| Cổng thông tin Thí sinh | Gmail SSO; hiển thị: thông tin đội, bảng, chủ đề, thời gian bắt đầu/kết thúc, countdown |
| **Bộ sinh Email AI** | Dựa trên LLM: sinh 4 loại email thông báo cuộc thi |
| Phân công Mentor | Admin phân công mentor/giám khảo vào bảng; xác thực domain email FPT |
| Giao diện Chấm điểm | Giám khảo nhập điểm + nhận xét (tùy chọn); cross-judging; theo dõi tiến độ |
| **Bộ sinh Câu hỏi AI** | Đọc văn bản review của giám khảo → sinh 5–7 câu hỏi phỏng vấn qua LLM |
| **Timeline AI Agent** | Scheduler nền: thực thi mốc, kích hoạt email, đóng cổng nộp bài |
| Kết quả & Xếp hạng | Tổng hợp điểm, xếp hạng đội, tự động chọn đội vào chung kết |
| Module Chung kết | Phân công hội đồng giám khảo riêng, chấm điểm chung kết, xếp hạng cuối |
| Xử lý Khiếu nại | Tiếp nhận khiếu nại có cấu trúc, theo dõi, AI hỗ trợ phân loại |
| Truy cập Lịch sử | Chỉ nhân viên/giảng viên truy cập dữ liệu cuộc thi cũ (thí sinh không xem được) |

## 6. Tóm tắt Các Thành phần AI

| Thành phần AI | Công nghệ | Đầu vào | Đầu ra |
|---|---|---|---|
| Bộ sinh Email | LLM (Gemini 1.5 Flash / GPT-4o-mini) | Ngữ cảnh cuộc thi + loại thông báo | Tiêu đề + nội dung email |
| Bộ sinh Câu hỏi | LLM (Gemini 1.5 Pro / GPT-4) | Văn bản review + rubric cuộc thi | 5–7 câu hỏi phỏng vấn |
| Timeline Agent | Cron scheduler + kiểm tra trạng thái DB | Mốc cuộc thi trong database | Cập nhật trạng thái + kích hoạt hành động |
