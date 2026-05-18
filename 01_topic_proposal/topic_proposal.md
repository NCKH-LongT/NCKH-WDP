# AI Study Hub — Topic Proposal

> **Hệ thống Quản lý Tài liệu Học tập AI**
>
> Một nền tảng web hỗ trợ sinh viên lưu trữ, quản lý, tìm kiếm và chia sẻ tài liệu học tập trên cloud, đồng thời tích hợp AI Chatbot để hỗ trợ hỏi đáp nội dung học tập.

---

## 1. Topic

**Tên hệ thống:** Hệ thống Quản lý Tài liệu Học tập AI (**AI Study Hub**)

---

## 2. Context

Trong quá trình học tập, sinh viên thường lưu trữ tài liệu ở nhiều nơi khác nhau như:

- Google Drive
- Messenger
- Facebook Group
- Email
- USB cá nhân

Điều này dẫn đến việc:

- Khó quản lý tài liệu
- Khó tìm kiếm lại tài liệu cũ
- Thất lạc dữ liệu
- Chia sẻ tài liệu thiếu đồng bộ

Ngoài ra, sinh viên hiện nay có nhu cầu:

- Lưu trữ tài liệu online
- Truy cập mọi lúc mọi nơi
- Tìm kiếm nhanh theo môn học hoặc từ khóa
- Sử dụng AI để hỗ trợ học tập và giải đáp nội dung tài liệu

Vì vậy, cần xây dựng một hệ thống web tập trung giúp sinh viên:

- Upload và quản lý tài liệu học tập
- Lưu trữ file trên cloud
- Tìm kiếm tài liệu hiệu quả
- Chia sẻ tài liệu dễ dàng
- Tích hợp AI chatbot để hỗ trợ học tập thông minh

> Hệ thống cũng giúp sinh viên tiếp cận quy trình phát triển phần mềm fullstack thực tế.

---

## 3. Problems

Hệ thống được xây dựng để giải quyết các vấn đề sau:

### 3.1 Tài liệu học tập phân tán

Tài liệu nằm ở nhiều nền tảng khác nhau khiến việc quản lý và truy cập trở nên khó khăn.

### 3.2 Khó tìm kiếm tài liệu cũ

Sinh viên mất nhiều thời gian để tìm lại tài liệu đã lưu trước đó.

### 3.3 Không có hệ thống phân loại rõ ràng

Tài liệu chưa được tổ chức theo môn học, chủ đề hoặc loại tài liệu.

### 3.4 Chia sẻ tài liệu thủ công

Việc gửi tài liệu qua Messenger hoặc Email gây bất tiện và khó quản lý phiên bản.

### 3.5 Giới hạn dung lượng lưu trữ cá nhân

Lưu trữ trên máy tính hoặc USB dễ gây đầy bộ nhớ và mất dữ liệu.

### 3.6 Thiếu công cụ hỗ trợ học tập thông minh

Sinh viên chưa thể đặt câu hỏi trực tiếp về nội dung tài liệu để được hỗ trợ nhanh chóng.

---

## 4. Primary Actors

| Actor              | Mô tả                                                          |
| ------------------ | -------------------------------------------------------------- |
| **Guest**          | Người dùng chưa đăng nhập, có thể truy cập các trang công khai |
| **User**           | Sinh viên sử dụng hệ thống để quản lý và sử dụng tài liệu      |
| **Admin**          | Quản trị viên quản lý hệ thống và người dùng                   |
| **ChatbotService** | Dịch vụ AI xử lý câu hỏi và trả lời nội dung học tập           |

---

## 5. Functional Requirements

### 5.1 Authentication

User có thể:

- Đăng ký tài khoản
- Đăng nhập
- Đăng xuất
- Quên mật khẩu
- Cập nhật thông tin cá nhân (profile)

### 5.2 Document Management

User có thể:

- Upload tài liệu học tập
- Xem danh sách tài liệu
- Xem chi tiết tài liệu
- Tải xuống tài liệu
- Chỉnh sửa thông tin tài liệu
- Xóa tài liệu
- Tìm kiếm tài liệu theo từ khóa
- Lọc tài liệu theo môn học

### 5.3 Cloud Storage

Hệ thống hỗ trợ:

- Upload file lên cloud storage
- Theo dõi trạng thái upload
- Lưu trữ file online
- Preview tài liệu trực tiếp trên web

### 5.4 AI Chatbot

**User** có thể:

- Chat với AI chatbot
- Đặt câu hỏi liên quan đến tài liệu học tập
- Nhận câu trả lời từ AI
- Xem lịch sử hội thoại

**ChatbotService** có nhiệm vụ:

- Tiếp nhận câu hỏi từ user
- Phân tích nội dung câu hỏi
- Truy xuất dữ liệu liên quan
- Sinh câu trả lời AI phù hợp

### 5.5 Administration

Admin có thể:

- Quản lý người dùng
- Quản lý tài liệu
- Xóa tài liệu vi phạm
- Theo dõi hoạt động hệ thống
- Quản lý nội dung chatbot nếu cần

---

## References

- **Slide:** [AI Study Hub — Gamma Presentation](https://gamma.app/docs/AI-Study-Hub-f3vjn56quuppq7a)
