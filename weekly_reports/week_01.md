# Báo cáo Tuần - Tuần 01

## Thông tin Nhóm

- Lớp: SE1822
- Nhóm: G03
- Trưởng nhóm: [TBD — trưởng nhóm điền vào]
- Thành viên: [TBD — liệt kê tên và mã số sinh viên tất cả thành viên]

## Công việc Đã hoàn thành Tuần này

| Thành viên | Công việc | Kết quả |
|---|---|---|
| [Trưởng nhóm] | Tạo nhánh nhóm SE1822_G03 trên Git repository | Hoàn thành |
| [Trưởng nhóm] | Đọc README.md và nắm toàn bộ yêu cầu | Hoàn thành |
| [Thành viên 1] | Nghiên cứu lĩnh vực quản lý cuộc thi và các trường hợp ứng dụng AI | Xác định 3 tính năng AI: sinh email, sinh câu hỏi, timeline agent |
| [Thành viên 2] | Đọc các file hiện có: ai_management_system_conference_paper_ideas.md và similar_conference_papers_ai_management_system.md | Trích xuất tài liệu tham khảo và hướng đề tài |
| [Cả nhóm] | Thống nhất chủ đề và phạm vi đề tài | Chọn ACMS-AI làm đề tài |
| [Cả nhóm] | Tạo cấu trúc thư mục đầy đủ theo yêu cầu README | Tất cả thư mục và file cần thiết đã tạo xong |
| [Cả nhóm] | Viết nội dung ban đầu: topic_proposal, problem_statement, research_gap, research_questions | Hoàn thành (bản nháp v1) |
| [Cả nhóm] | Viết tóm tắt 6 bài báo liên quan | paper_01 đến paper_06 hoàn thành |
| [Cả nhóm] | Điền literature review matrix | 8 bài báo được thêm vào |
| [Cả nhóm] | Viết tài liệu kiến trúc hệ thống, luồng dữ liệu, tích hợp AI | Hoàn thành (bản nháp v1) |
| [Cả nhóm] | Viết methodology, dataset, baseline, evaluation metrics | Hoàn thành (bản nháp v1) |
| [Cả nhóm] | Viết 07_paper_draft: tất cả các phần dạng bản nháp | Abstract, Giới thiệu, Tổng quan tài liệu, Phương pháp, Thảo luận, Kết luận — bản nháp v1 |

## Commit Git

| Commit ID | Nội dung commit | Tác giả |
|---|---|---|
| TBD | topic: đề xuất đề tài ban đầu và cấu trúc thư mục đầy đủ | TBD |
| TBD | docs: thêm tóm tắt bài báo paper_01 đến paper_06 | TBD |
| TBD | method: thêm kiến trúc hệ thống, luồng dữ liệu, tích hợp AI | TBD |
| TBD | method: thêm methodology, dataset, baseline, evaluation metrics | TBD |
| TBD | docs: thêm các phần bản nháp bài báo (abstract, giới thiệu, tổng quan tài liệu, phương pháp, thảo luận, kết luận) | TBD |

## Vấn đề Hiện tại

- Cần xác nhận tên thành viên nhóm và phân công vai trò/công việc cụ thể cho từng người
- Cần tìm và đọc file PDF thực tế của 6 bài báo đã tóm tắt để kiểm tra độ chính xác
- Cần làm rõ nguồn dữ liệu: sẽ dùng dữ liệu cuộc thi thực tế của FPT hay dữ liệu mô phỏng cho đánh giá?
- Cần quyết định: Gemini API (free tier) hay OpenAI API cho tích hợp LLM?
- Cần xác nhận cấu trúc cuộc thi tại FPT (số bảng, số vòng, các loại email) với giảng viên

## Kế hoạch Tuần tiếp theo (Tuần 02)

- Đọc đầy đủ file PDF của 6 bài báo đã tóm tắt và tinh chỉnh nội dung tóm tắt với thông tin chính xác
- Thêm 4 bài báo nữa để đạt tối thiểu 10 bài theo yêu cầu (ưu tiên: sinh câu hỏi tự động, phương pháp đánh giá sinh văn bản LLM)
- Điền `02_related_work/paper_list.md` với thông tin thư mục đầy đủ và chính xác
- Bắt đầu triển khai hệ thống cơ bản: thiết lập cấu trúc Git repository cho code
- Thảo luận quyết định công nghệ (Gemini vs. OpenAI, Node.js vs. Spring Boot)
- Cập nhật `weekly_reports/week_02.md`

## Câu hỏi Dành cho Giảng viên

1. Có được phép dùng dữ liệu cuộc thi mô phỏng (thay vì hồ sơ cuộc thi FPT thực tế) cho dataset đánh giá, xét đến ràng buộc về quyền riêng tư và quyền truy cập dữ liệu không?
2. Gemini API (free tier qua Google AI Studio) có được chấp nhận cho dự án này không, hay có yêu cầu cụ thể về LLM?
3. Bài báo có thể đề cập đến ba đóng góp AI riêng biệt (sinh email, sinh câu hỏi, tự động hóa timeline) không, hay nên tập trung vào một đóng góp chính để có góc nghiên cứu mạnh hơn?
4. Cấu trúc quản lý cuộc thi tại FPT có khớp với những gì được mô tả trong hệ thống của nhóm (30 đội, 3 bảng, 2 vòng) không? Có thông tin đặc thù nào khác cần bổ sung không?
5. Giảng viên đang hướng đến hội thảo hoặc tạp chí nào để nộp bài?
