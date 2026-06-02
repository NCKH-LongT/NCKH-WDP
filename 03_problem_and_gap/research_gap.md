# Khoảng trống Nghiên cứu

## 1. Những gì các Hệ thống Hiện tại Đã Làm

### 1.1. AI trong Quản lý Sự kiện và Cuộc thi

Các hệ thống quản lý sự kiện tích hợp AI hiện có (ví dụ: Smart Event Management System Using Machine Learning) tập trung vào tối ưu hóa lịch và phân tích hành vi người tham gia bằng ML. Chúng chứng minh được hiệu quả cải thiện nhưng không giải quyết truyền thông tự động hay hỗ trợ chuẩn bị giám khảo.

### 1.2. Hệ thống Quản lý Tích hợp AI (Bối cảnh LMS)

Các hệ thống như Aduvia tích hợp nhiều tính năng AI (chatbot, sinh quiz, gợi ý) vào nền tảng quản lý đặc thù theo lĩnh vực. Các hệ thống này thiết lập tính khả thi về kiến trúc của tích hợp AI đa module nhưng chỉ nhắm đến quản lý học tập, không phải luồng công việc cuộc thi.

### 1.3. LLM cho Sinh Văn bản Thể chế

Các nghiên cứu như AI-Powered Academic Advising Using LLMs và AI-Augmented Advising chứng minh LLM có thể sinh văn bản thể chế (phản hồi tư vấn, giải thích quy định) tương đương chất lượng văn bản con người với các truy vấn thông thường. Các nghiên cứu này thiết lập tính khả thi của truyền thông thể chế do LLM sinh ra.

### 1.4. Sinh Câu hỏi bằng AI

Các hệ thống AI-Powered Quiz Generation for LMS đã chỉ ra LLM có thể sinh câu hỏi kiểm tra từ nội dung khóa học có cấu trúc với tỷ lệ chấp nhận hơn 70% của giảng viên. Tuy nhiên, các hệ thống này sinh câu hỏi trắc nghiệm từ tài liệu có cấu trúc, không phải câu hỏi phỏng vấn mở từ bài đánh giá dạng văn bản tự do.

### 1.5. Ghép Expert / Mentor

Các hệ thống gợi ý giảng viên hướng dẫn chứng minh AI hỗ trợ ghép cặp người với nhiệm vụ, nhưng sử dụng TF-IDF hoặc phương pháp lọc đơn giản và không đề cập đến phân công mentor-bảng thi đặc thù cuộc thi có xác thực vai trò.

## 2. Những gì CHƯA Được Giải quyết

| Lĩnh vực khoảng trống | Khoảng trống cụ thể | Bằng chứng từ tài liệu |
|---|---|---|
| Sinh email LLM đặc thù cuộc thi | Không có hệ thống nào sinh 4 loại thông báo cuộc thi (vào chung kết, deadline, chưa nộp, phân công mentor) bằng LLM cho luồng cuộc thi học thuật | Không tìm thấy trong các bài đã xem xét |
| Sinh câu hỏi phỏng vấn từ bài đánh giá | Không có công trình nào sinh câu hỏi phỏng vấn từ bài đánh giá dự án trong bối cảnh cuộc thi | Công trình sinh quiz dùng tài liệu có cấu trúc, không phải bài review; sinh câu hỏi quiz chứ không phải câu hỏi phỏng vấn |
| Quản lý vòng đời cuộc thi tự động | Các hệ thống lập lịch hiện có nhắm đến sự kiện thông thường, không có cấu trúc đa bảng, hai vòng của cuộc thi học thuật | Các bài báo quản lý sự kiện thiếu luồng đặc thù cuộc thi |
| Nền tảng cuộc thi tích hợp AI | Không có nền tảng thống nhất nào kết hợp: đăng ký đội, tự động chia bảng, xác thực email mentor, chấm điểm hai vòng, email AI, sinh câu hỏi AI | Các module riêng lẻ tồn tại; không có hệ thống tích hợp |
| Đánh giá thực nghiệm truyền thông LLM trong cuộc thi | Không có nghiên cứu thực nghiệm nào so sánh email thông báo cuộc thi do LLM tạo với email viết tay bằng đánh giá mù chuyên gia | Không tìm thấy trong tài liệu quản lý cuộc thi |

## 3. Khoảng trống mà Công trình Này Lấp đầy

> Các hệ thống quản lý tích hợp AI hiện có chủ yếu tập trung vào quản lý học tập, sinh quiz hoặc lập lịch sự kiện thông thường. Rất ít chú ý được dành cho việc tích hợp LLM cho luồng truyền thông cuộc thi tự động và sinh câu hỏi phỏng vấn từ bài đánh giá trong bối cảnh hackathon học thuật và cuộc thi nghiên cứu. Không có công trình nào cung cấp nền tảng tích hợp giải quyết vòng đời đầy đủ của cuộc thi học thuật với các khả năng AI nhúng cho truyền thông, quản lý timeline và hỗ trợ chuẩn bị giám khảo.

## 4. Đóng góp của Chúng tôi cho Lấp đầy Khoảng trống

| Khoảng trống | Giải pháp của chúng tôi |
|---|---|
| Email LLM cho các mốc cuộc thi | Module Sinh Email LLM với 4 mẫu prompt chuyên biệt |
| Sinh câu hỏi phỏng vấn từ bài đánh giá | Module AI Review Reader: văn bản review + rubric → 5–7 câu hỏi qua LLM |
| Nền tảng cuộc thi tích hợp | ACMS-AI: hệ thống thống nhất bao phủ vòng đời cuộc thi đầy đủ |
| Tự động hóa timeline | Timeline AI Agent: thực thi mốc thời gian tự động bằng cron scheduler |
| Đánh giá chất lượng thực nghiệm | Nghiên cứu đánh giá mù chuyên gia: 80 cặp email + 30 bộ câu hỏi, AI vs. con người |
