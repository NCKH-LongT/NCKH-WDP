# Báo cáo Tuần - Tuần 04

## Thông tin Nhóm

- Lớp: SE1822
- Nhóm: G03
- Trưởng nhóm: Nguyễn Đàm Chấn Đức
- Thành viên:
  - Nguyễn Đàm Chấn Đức — SE182150 (Trưởng nhóm)
  - Đặng Nhựt Trường — SE182203
  - Nguyễn Thế Văn — SE183679
  - Khuất Trường Huy — SE180717

## Công việc Đã hoàn thành Tuần này

| Thành viên | Công việc | Kết quả |
|---|---|---|
| Nguyễn Đàm Chấn Đức | Cấu hình CORS, kết nối backend Node.js với AI Service FastAPI | Hoàn thành |
| Nguyễn Đàm Chấn Đức | Viết API documentation (Swagger/OpenAPI) cho toàn bộ endpoint | Hoàn thành |
| Đặng Nhựt Trường | Tinh chỉnh prompt email qua pilot 20 mẫu — đạt điểm trung bình ≥ 3.5/5 | Hoàn thành |
| Đặng Nhựt Trường | Implement output validation: kiểm tra độ dài tiêu đề, nội dung, không còn placeholder | Hoàn thành |
| Đặng Nhựt Trường | Bắt đầu xây dựng module sinh câu hỏi phỏng vấn từ bài review (prompt v1) | Hoàn thành (bản nháp) |
| Nguyễn Thế Văn | Thêm Mongoose schemas: EmailDraft, QuestionSet, MilestoneLog | Hoàn thành |
| Nguyễn Thế Văn | Viết API endpoints cho lưu/lấy AI content (email drafts, question sets) | Hoàn thành |
| Khuất Trường Huy | Xây dựng trang quản lý cuộc thi (tạo, chỉnh sửa, xem danh sách) | Hoàn thành |
| Khuất Trường Huy | Xây dựng trang sinh email cho admin (form nhập ngữ cảnh + hiển thị kết quả AI) | Hoàn thành |

## Commit Git

| Commit ID | Nội dung commit | Tác giả |
|---|---|---|
| TBD | feat: cấu hình CORS và kết nối backend-AI service | Nguyễn Đàm Chấn Đức |
| TBD | docs: thêm Swagger API documentation | Nguyễn Đàm Chấn Đức |
| TBD | feat: tinh chỉnh prompt email v2, thêm output validation | Đặng Nhựt Trường |
| TBD | feat: bắt đầu module sinh câu hỏi từ review (prompt v1) | Đặng Nhựt Trường |
| TBD | feat: cập nhật database schema, thêm email_drafts và question_sets | Nguyễn Thế Văn |
| TBD | feat: xây dựng trang quản lý cuộc thi và trang sinh email admin | Khuất Trường Huy |

## Vấn đề Hiện tại

- Module sinh câu hỏi từ review chưa ổn định — đầu ra JSON đôi khi không đúng format
- Cần implement deduplication (cosine similarity) cho câu hỏi trùng lặp
- Trang sinh email frontend cần thêm bước xem trước trước khi gửi

## Kế hoạch Tuần tiếp theo (Tuần 05)

- Nguyễn Đàm Chấn Đức: Implement Timeline AI Agent (APScheduler, logic kiểm tra milestone)
- Đặng Nhựt Trường: Hoàn thiện module sinh câu hỏi — fix JSON output, thêm deduplication
- Nguyễn Thế Văn: Viết API cho Timeline Agent, thêm bảng milestone_executions
- Khuất Trường Huy: Xây dựng giao diện giám khảo (xem review, sinh câu hỏi, giao diện chấm điểm)
- Cập nhật `weekly_reports/week_05.md`
