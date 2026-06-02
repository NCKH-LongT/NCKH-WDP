# Đề xuất Đề tài

## 1. Thông tin Nhóm

- Lớp: SE1822
- Nhóm: G03
- Trưởng nhóm: [TBD]
- Thành viên: [TBD]

## 2. Tên Đề tài Dự kiến

Tên tiếng Anh: **AI-Enhanced Academic Competition Management System with LLM-Based Email Automation and Review-Driven Interview Question Generation**

Tên tiếng Việt: **Hệ thống Quản lý Cuộc thi Học thuật Tích hợp AI: Tự động hóa Email qua LLM và Sinh câu hỏi Phỏng vấn từ Bài đánh giá Dự án**

## 3. Lĩnh vực Ứng dụng

Quản lý cuộc thi học thuật / quản lý sự kiện / giáo dục đại học / ứng dụng AI trong giáo dục.

## 4. Mô tả Vấn đề Thực tế

Việc tổ chức các cuộc thi học thuật (hackathon, cuộc thi nghiên cứu) tại Đại học FPT hiện nay phụ thuộc vào nhiều quy trình thủ công:

- Quản trị viên phải theo dõi và thực thi thủ công thời hạn nộp bài cho hơn 30 đội thi.
- Email thông báo cho từng mốc thời gian của cuộc thi (thông báo vào chung kết, nhắc deadline, cảnh báo chưa nộp, phân công mentor) đều được soạn và gửi tay, dẫn đến chất lượng thông tin không đồng nhất.
- Giám khảo phải tự đọc báo cáo dự án và soạn câu hỏi phỏng vấn trước mỗi buổi chấm vấn đáp, tốn nhiều thời gian và chất lượng câu hỏi không đồng đều giữa các giám khảo.
- Không có nền tảng tích hợp nào kết hợp đăng ký, quản lý bảng thi, phân công mentor, chấm điểm và truyền thông trong một hệ thống duy nhất.

## 5. Lý do Cần Tích hợp AI

- Các mô hình ngôn ngữ lớn (LLM) như Gemini và GPT-4 đã chứng minh khả năng tạo văn bản phù hợp ngữ cảnh, chuyên nghiệp — phù hợp với tự động hóa soạn email trong môi trường tổ chức.
- AI agent có thể thực thi các tác vụ có lịch cố định một cách chính xác (tự động đóng cổng nộp bài đúng giờ), loại bỏ sai sót do con người giám sát thủ công.
- Sinh câu hỏi phỏng vấn từ bài đánh giá là ứng dụng mới: cho trước một bài review của giám khảo, LLM có thể tổng hợp câu hỏi phỏng vấn bám sát những điểm mạnh và yếu được chỉ ra trong đánh giá đó.

## 6. Đối tượng Người dùng

| Vai trò | Mô tả |
|---|---|
| Quản trị viên | Tạo/quản lý cuộc thi, giám sát tiến độ, xem xét nội dung AI tạo ra |
| Thí sinh / Đội thi | Đăng ký qua Gmail, xem thông tin đội/chủ đề/deadline, nộp bài |
| Mentor / Giám khảo | Review bài nộp, nhập điểm, nhận câu hỏi phỏng vấn do AI tạo |

## 7. Model AI Dự kiến Sử dụng

| Thành phần AI | Phương pháp | Mục đích |
|---|---|---|
| Bộ sinh Email | LLM (Gemini 1.5 Flash / GPT-4o-mini) | Tự động tạo 4 loại email thông báo cuộc thi |
| Bộ sinh Câu hỏi | LLM (Gemini 1.5 Pro / GPT-4) | Sinh câu hỏi phỏng vấn từ bài đánh giá của giám khảo |
| Timeline Agent | Scheduler tự động (cron-based) | Tự đóng cổng nộp bài và kích hoạt hành động tại các mốc thời gian |

## 8. Các Chức năng Chính của Hệ thống

1. Quản trị viên tạo và quản lý vòng đời cuộc thi
2. Form đăng ký đội thi trực tuyến với xác nhận email từ tất cả thành viên
3. Tự động chia đội vào bảng thi (ví dụ: 30 đội → 3 bảng × 10 đội)
4. Giao chủ đề cho từng bảng qua Google Drive link hoặc nền tảng tương tự
5. Cổng thông tin thí sinh (đăng nhập Gmail SSO): thông tin đội, chủ đề được giao, đồng hồ đếm ngược
6. Bộ sinh Email AI — 4 loại: thông báo vào chung kết, nhắc deadline, cảnh báo chưa nộp, phân công mentor
7. Phân công mentor/giám khảo với xác thực email domain FPT
8. Hệ thống chấm điểm 2 vòng: sơ khảo (cross-judging) + chung kết (hội đồng riêng), theo dõi tiến độ chấm
9. AI đọc bài đánh giá → sinh câu hỏi phỏng vấn: đọc review của giám khảo, xuất 5–7 câu hỏi
10. Module tiếp nhận và xử lý khiếu nại

## 9. Đóng góp Dự kiến

1. Thiết kế và triển khai nền tảng quản lý cuộc thi học thuật tích hợp AI đầy đủ (ACMS-AI)
2. Pipeline sinh email tự động bằng LLM cho 4 loại thông báo cuộc thi đặc thù
3. Module sinh câu hỏi phỏng vấn từ bài đánh giá dự án — ứng dụng mới, lần đầu áp dụng trong bối cảnh cuộc thi học thuật
4. Đánh giá thực nghiệm chất lượng nội dung AI tạo ra so với nội dung con người viết tay (đánh giá mù bởi chuyên gia)
5. Minh chứng về tự động hóa quản lý timeline cho cuộc thi học thuật đa bảng

## 10. Kế hoạch Đánh giá

- **Dữ liệu**: Dữ liệu cuộc thi và bài đánh giá từ FPT (thật hoặc mô phỏng); 80 cặp email AI/tay (20 mỗi loại); 30 bộ câu hỏi AI/chuyên gia
- **Baseline**: Email viết tay bởi quản trị viên; câu hỏi soạn tay bởi giám khảo; giám sát deadline thủ công
- **Chỉ số**: Điểm đánh giá chuyên gia (thang Likert 1–5: mức độ liên quan, giọng điệu, rõ ràng, độ bao phủ, chiều sâu); thời gian tiết kiệm; độ chính xác của timeline agent; điểm SUS
- **Đánh giá chuyên gia**: 3–5 giảng viên FPT có kinh nghiệm chấm thi đánh giá nội dung AI và tay trong điều kiện mù

## 11. Bài báo Liên quan

| STT | Tên bài báo | Năm | Nguồn | Link / DOI |
|---|---|---|---|---|
| 1 | Smart Event Management System Using Machine Learning | 2023 | International Conference on IT Management | TBD |
| 2 | Aduvia: A Multi-Purpose AI-Powered Learning Management System | 2025 | NILES 2025 | TBD |
| 3 | AI-Powered Quiz Generation for Learning Management Systems: A Full-Stack Implementation for Canvas LMS | 2025 | CEUR Workshop Proceedings | TBD |
| 4 | AI-Powered Academic Advising Using Large Language Models | 2024 | International Conference on AI in Education | TBD |
| 5 | AI-Augmented Advising | 2025 | Journal of Learning Analytics | TBD |
| 6 | Research Supervisor Recommendation System Based on Topic Conformity | 2023 | Research Conference | TBD |
| 7 | Research Supervisor Recommendation System Using a Hybrid Filtering Approach | 2025 | ICAITech 2025 | TBD |
| 8 | Smart Inventory Management System with Real-Time Package Tracking Using Machine Learning | 2026 | IEEE ICoECIT 2026 | TBD |
