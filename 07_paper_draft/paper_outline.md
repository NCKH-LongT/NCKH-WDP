# Đề cương Bài báo

## Tiêu đề Đề xuất

**AI-Enhanced Academic Competition Management System with LLM-Based Email Automation and Review-Driven Interview Question Generation**

*(Hệ thống Quản lý Cuộc thi Học thuật Tích hợp AI: Tự động hóa Email qua LLM và Sinh câu hỏi Phỏng vấn từ Bài đánh giá Dự án)*

## Hội thảo / Tạp chí Mục tiêu

| Ưu tiên | Hội thảo | Track | Deadline (ước tính) |
|---|---|---|---|
| 1 | CEUR Workshop Proceedings | Applied AI / EdTech | TBD |
| 2 | IEEE International Conference on IT Management | AI Systems | TBD |
| 3 | NILES Conference (New Trends in ICT Applications) | AI in Education | TBD |
| 4 | ACM AIED (Artificial Intelligence in Education) | Applied AI Systems | TBD |

## Loại Bài báo

Applied AI / System Paper — trình bày hệ thống mới tích hợp các mô hình AI hiện có vào luồng quản lý đặc thù theo lĩnh vực với đánh giá thực nghiệm.

## Câu định vị Bài báo

> Nghiên cứu này không nhằm đề xuất một mô hình AI hoàn toàn mới, mà tập trung khảo sát cách tích hợp các mô hình ngôn ngữ lớn hiện có vào luồng quản lý cuộc thi học thuật và đánh giá hiệu quả trong việc tự động hóa truyền thông, hỗ trợ chuẩn bị giám khảo và thực thi timeline cuộc thi.

---

## Đề cương Chi tiết

### Tóm tắt (~150–250 từ)

- Vấn đề: quản lý cuộc thi thủ công kém hiệu quả; truyền thông không đồng nhất; chuẩn bị giám khảo tốn thời gian
- Hệ thống đề xuất: ACMS-AI với 3 module AI (bộ sinh email, bộ sinh câu hỏi, timeline agent)
- Phương pháp: tích hợp LLM, đánh giá mù chuyên gia, khảo sát khả năng sử dụng SUS
- Kết quả chính: [TBD sau thực nghiệm]
- Câu kết luận

### 1. Giới thiệu (~1,5 trang)

- 1.1 Bối cảnh: cuộc thi học thuật tại FPT; quy mô và sự phức tạp
- 1.2 Vấn đề: 4 điểm đau cụ thể (thực thi timeline, chi phí truyền thông, chuẩn bị giám khảo, công cụ phân mảnh)
- 1.3 Động lực cho tích hợp AI: khả năng của LLM trong sinh văn bản có cấu trúc
- 1.4 Đóng góp: 5 đóng góp cụ thể
- 1.5 Cấu trúc bài báo

### 2. Tổng quan Tài liệu (~1,5 trang)

- 2.1 Hệ thống quản lý tích hợp AI (Aduvia, Smart Event Management System)
- 2.2 LLM sinh văn bản thể chế (AI-Powered Academic Advising, AI-Augmented Advising)
- 2.3 Hệ thống sinh câu hỏi AI (AI-Powered Quiz Gen for LMS)
- 2.4 Ghép mentor/chuyên gia (các bài báo gợi ý giảng viên hướng dẫn)
- 2.5 Khoảng trống nghiên cứu — những gì chưa được giải quyết trong quản lý cuộc thi

### 3. Hệ thống Đề xuất (~2 trang)

- 3.1 Tổng quan hệ thống: ACMS-AI, vai trò người dùng, các module
- 3.2 Kiến trúc hệ thống: 4 tầng với lớp AI Service; sơ đồ kiến trúc
- 3.3 Bộ sinh Email AI: 4 loại, thiết kế prompt, kiểm tra đầu ra
- 3.4 Bộ sinh Câu hỏi AI: schema đầu vào, thiết kế prompt, pipeline hậu xử lý
- 3.5 Timeline AI Agent: thiết kế scheduler, kích hoạt hành động, ghi log
- 3.6 Module hỗ trợ: đăng ký, quản lý bảng, chấm điểm, cổng thông tin

### 4. Phương pháp (~1,5 trang)

- 4.1 Lựa chọn LLM và lý do
- 4.2 Hướng tiếp cận prompt engineering (cho sinh email và câu hỏi)
- 4.3 Thiết kế đánh giá: nghiên cứu đánh giá mù chuyên gia
  - Đánh giá email: 80 cặp, 5 chiều, thang Likert 5 điểm
  - Đánh giá câu hỏi: 30 bộ, 4 chiều, thang Likert 5 điểm
- 4.4 Đo hiệu quả: tính giờ tác vụ (admin + giám khảo)
- 4.5 Nghiên cứu khả năng sử dụng: SUS, 3 vai trò, ≥ 10 người mỗi vai trò
- 4.6 Kế hoạch phân tích thống kê

### 5. Thiết lập Thực nghiệm (~0,5 trang)

- Kích thước dữ liệu và phương pháp xây dựng
- Cấu hình LLM API (temperature, max tokens)
- Hồ sơ người đánh giá chuyên gia và quy trình hiệu chỉnh
- Môi trường phần cứng/phần mềm

### 6. Kết quả (~1,5 trang)

- Bảng 1: Chất lượng email (AI vs. tay) — tất cả 5 chiều, cả 4 loại
- Bảng 2: Chất lượng câu hỏi (AI vs. chuyên gia) — tất cả 4 chiều
- Bảng 3: Độ chính xác timeline agent
- Bảng 4: Phân tích hiệu quả (thời gian tiết kiệm)
- Hình 1: Điểm SUS theo vai trò
- Phân tích ý nghĩa thống kê

### 7. Thảo luận (~0,75 trang)

- 7.1 Diễn giải kết quả chất lượng email — nơi AI sánh ngang/vượt trội thủ công
- 7.2 Diễn giải chất lượng câu hỏi — điểm mạnh và hạn chế
- 7.3 Hiệu quả: ý nghĩa thực tiễn cho quản trị viên cuộc thi FPT
- 7.4 Hạn chế: rủi ro hallucination, kích thước dataset, đặc thù domain, nhạy cảm prompt
- 7.5 Mối đe dọa tính hợp lệ

### 8. Kết luận và Hướng Nghiên cứu Tương lai (~0,5 trang)

- Tóm tắt 3 đóng góp AI và kết quả đánh giá
- Hướng phát triển: tích hợp RAG, đa ngôn ngữ (Việt/Anh), vòng lặp phản hồi, mở rộng sang bảo vệ luận văn

### Tài liệu Tham khảo (8–12 bài báo, định dạng IEEE/ACM)
