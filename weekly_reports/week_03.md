# Báo cáo Tuần - Tuần 03

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
| Nguyễn Đàm Chấn Đức | Triển khai backend API (TypeScript): Google OAuth 2.0 authentication + kiểm tra domain FPT | Hoàn thành |
| Nguyễn Đàm Chấn Đức | Triển khai CRUD API cho competition, team, round (TypeScript + Express) | Hoàn thành |
| Đặng Nhựt Trường | Thiết lập AI Service (Node.js/TypeScript), tích hợp Gemini 1.5 Flash API | Hoàn thành |
| Đặng Nhựt Trường | Viết prompt template v1 cho 4 loại email thông báo | Hoàn thành (cần tinh chỉnh) |
| Nguyễn Thế Văn | Định nghĩa Mongoose schemas (collections: users, competitions, teams, rounds, milestones) | Hoàn thành |
| Nguyễn Thế Văn | Viết seed data và kết nối MongoDB cho môi trường development | Hoàn thành |
| Khuất Trường Huy | Thiết lập project React.js + Tailwind CSS + Ant Design, cấu hình routing và layout cơ bản | Hoàn thành |
| Khuất Trường Huy | Xây dựng trang login (Google OAuth) và dashboard admin skeleton | Hoàn thành |

## Commit Git

| Commit ID | Nội dung commit | Tác giả |
|---|---|---|
| TBD | feat: thêm Google OAuth 2.0 authentication với FPT domain check | Nguyễn Đàm Chấn Đức |
| TBD | feat: thêm CRUD API cho competition, team, round | Nguyễn Đàm Chấn Đức |
| TBD | feat: thiết lập AI Service FastAPI + tích hợp Gemini API | Đặng Nhựt Trường |
| TBD | feat: viết prompt template v1 cho 4 loại email | Đặng Nhựt Trường |
| TBD | feat: định nghĩa Mongoose schemas, kết nối MongoDB | Nguyễn Thế Văn |
| TBD | feat: thiết lập React.js + Tailwind + Ant Design, routing, dashboard skeleton | Khuất Trường Huy |

## Vấn đề Hiện tại

- Prompt email v1 chưa ổn định — đầu ra đôi khi còn placeholder chưa được thay thế
- Cần thống nhất API contract giữa backend Node.js và AI Service FastAPI
- Frontend chưa kết nối được với backend (CORS chưa cấu hình)

## Kế hoạch Tuần tiếp theo (Tuần 04)

- Nguyễn Đàm Chấn Đức: Cấu hình CORS, kết nối backend — AI Service, viết API docs
- Đặng Nhựt Trường: Tinh chỉnh prompt email (pilot 20 mẫu), bắt đầu module sinh câu hỏi
- Nguyễn Thế Văn: Thêm bảng email_drafts, question_sets vào schema; viết API cho AI content
- Khuất Trường Huy: Xây dựng trang quản lý cuộc thi và trang sinh email cho admin
- Cập nhật `weekly_reports/week_04.md`
