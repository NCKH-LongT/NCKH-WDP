# Báo cáo Tuần - Tuần 06

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
| Nguyễn Đàm Chấn Đức | Tích hợp end-to-end toàn bộ hệ thống (frontend ↔ backend ↔ AI service) | Hoàn thành |
| Nguyễn Đàm Chấn Đức | Fix bugs tích hợp: xử lý lỗi API, timeout, retry logic cho Gemini API | Hoàn thành |
| Nguyễn Đàm Chấn Đức | Cập nhật paper draft: phần System Design (Section 3) theo hệ thống thực tế | Hoàn thành |
| Đặng Nhựt Trường | Chuẩn bị 80 kịch bản email test (20 mỗi loại thông báo) cho đánh giá chuyên gia | Hoàn thành |
| Đặng Nhựt Trường | Chuẩn bị 30 bài project review test cho đánh giá module sinh câu hỏi | Hoàn thành |
| Nguyễn Thế Văn | Thiết lập môi trường production (Docker, MongoDB Atlas, deployment) | Hoàn thành |
| Nguyễn Thế Văn | Viết hướng dẫn cài đặt và vận hành hệ thống (README kỹ thuật) | Hoàn thành |
| Khuất Trường Huy | UI polish: cải thiện responsive design, thêm loading states và error handling | Hoàn thành |
| Khuất Trường Huy | Thêm tính năng export câu hỏi ra PDF cho giám khảo | Hoàn thành |
| Cả nhóm | Demo nội bộ toàn bộ hệ thống, xác định và log các bug còn lại | Hoàn thành |

## Commit Git

| Commit ID | Nội dung commit | Tác giả |
|---|---|---|
| TBD | feat: hoàn thiện tích hợp end-to-end, thêm error handling và retry logic | Nguyễn Đàm Chấn Đức |
| TBD | docs: cập nhật paper draft Section 3 (System Design) | Nguyễn Đàm Chấn Đức |
| TBD | test: thêm 80 kịch bản email test và 30 bài review test | Đặng Nhựt Trường |
| TBD | deploy: thiết lập Docker và môi trường production | Nguyễn Thế Văn |
| TBD | feat: UI polish, thêm export PDF cho câu hỏi giám khảo | Khuất Trường Huy |

## Vấn đề Hiện tại

- Cần liên hệ giảng viên FPT để mời chuyên gia đánh giá (blind evaluation)
- Timeline Agent cần chạy thử 50 synthetic milestones để đo độ chính xác
- Paper draft còn thiếu số liệu thực nghiệm (Section 5 — Results vẫn là TBD)

## Kế hoạch Tuần tiếp theo (Tuần 07)

- Nguyễn Đàm Chấn Đức: Liên hệ và mời chuyên gia đánh giá, chuẩn bị tài liệu hướng dẫn đánh giá
- Đặng Nhựt Trường: Chạy thử Timeline Agent với 50 synthetic milestones, ghi log kết quả
- Nguyễn Thế Văn: Chuẩn bị bộ câu hỏi SUS và thiết lập môi trường user testing
- Khuất Trường Huy: Fix các bug còn lại từ demo nội bộ, hỗ trợ chuẩn bị tài liệu đánh giá
- Cập nhật `weekly_reports/week_07.md`

## Câu hỏi Dành cho Giảng viên

1. Giảng viên có thể giới thiệu 3–5 chuyên gia (giảng viên FPT có kinh nghiệm chấm thi) để tham gia đánh giá mù không?
2. Thời gian dự kiến hoàn thành giai đoạn đánh giá và nộp bài báo là khi nào?
