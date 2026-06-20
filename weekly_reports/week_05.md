# Báo cáo Tuần - Tuần 05

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
| Nguyễn Đàm Chấn Đức | Implement Timeline AI Agent: node-cron (TypeScript), kiểm tra milestone mỗi 60 giây | Hoàn thành |
| Nguyễn Đàm Chấn Đức | Implement các hành động agent: đóng cổng nộp bài, kích hoạt sinh email, cập nhật trạng thái | Hoàn thành |
| Đặng Nhựt Trường | Hoàn thiện module sinh câu hỏi: fix JSON output format, thêm deduplication cosine similarity | Hoàn thành |
| Đặng Nhựt Trường | Tích hợp Gemini 1.5 Pro cho module sinh câu hỏi (thay Flash để tăng chất lượng) | Hoàn thành |
| Nguyễn Thế Văn | Viết API cho Timeline Agent, thêm Mongoose schema MilestoneExecution (predictedTime, actualTime, result) | Hoàn thành |
| Nguyễn Thế Văn | Viết unit tests cho database layer và API endpoints | Hoàn thành |
| Khuất Trường Huy | Xây dựng giao diện giám khảo: xem review, sinh câu hỏi AI, form chấm điểm | Hoàn thành |
| Khuất Trường Huy | Xây dựng cổng thông tin thí sinh: xem lịch thi, nộp bài, xem kết quả | Hoàn thành |

## Commit Git

| Commit ID | Nội dung commit | Tác giả |
|---|---|---|
| TBD | feat: implement Timeline AI Agent với APScheduler | Nguyễn Đàm Chấn Đức |
| TBD | feat: hoàn thiện module sinh câu hỏi, thêm deduplication | Đặng Nhựt Trường |
| TBD | feat: thêm bảng milestone_executions, API timeline agent | Nguyễn Thế Văn |
| TBD | feat: xây dựng giao diện giám khảo và cổng thí sinh | Khuất Trường Huy |

## Vấn đề Hiện tại

- Timeline Agent cần kiểm thử với dữ liệu milestone thực tế (hiện chỉ test với dữ liệu mock)
- Giao diện giám khảo cần thêm tính năng export câu hỏi ra PDF
- Cần tích hợp end-to-end: frontend → backend → AI service cho cả 3 module

## Kế hoạch Tuần tiếp theo (Tuần 06)

- Nguyễn Đàm Chấn Đức: Tích hợp end-to-end toàn bộ hệ thống, fix bugs tích hợp
- Đặng Nhựt Trường: Chuẩn bị 80 kịch bản email test và 30 bài review test cho đánh giá
- Nguyễn Thế Văn: Thiết lập môi trường production (deployment), viết hướng dẫn cài đặt
- Khuất Trường Huy: UI polish, thêm export PDF, fix responsive design
- Cập nhật `weekly_reports/week_06.md`
