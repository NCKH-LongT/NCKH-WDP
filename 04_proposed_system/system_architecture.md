# Kiến trúc Hệ thống

## 1. Tổng quan

ACMS-AI theo kiến trúc đa tầng với một lớp AI Service riêng biệt, tách rời khỏi backend chính:

```
[Trình duyệt: Thí sinh / Quản trị viên / Giám khảo]
              |
      [Tầng Frontend]
     (React.js / Next.js)
              |
      [Tầng Backend API]
    (Node.js + Express / Spring Boot)
         |         |         |
  [PostgreSQL]  [AI Service]  [Email Service]
   (DB chính)  (Python/FastAPI) (SendGrid/SMTP)
                     |
            [LLM API: Gemini / GPT]
            [Timeline Agent (Cron)]
```

## 2. Các Thành phần Chính

| Thành phần | Công nghệ | Mô tả |
|---|---|---|
| **Frontend** | React.js / Next.js | Giao diện web phân quyền cho 3 vai trò: quản trị viên, thí sinh, giám khảo |
| **Backend API** | Node.js + Express (hoặc Spring Boot) | Xử lý nghiệp vụ: đăng ký, chia bảng, chấm điểm, điều phối gọi AI |
| **Database** | PostgreSQL | Lưu trữ: cuộc thi, đội, bảng, điểm, bài review, nội dung AI tạo ra, log kiểm toán |
| **AI Service** | Python + FastAPI | Microservice gọi LLM API; xử lý sinh email, sinh câu hỏi, chạy timeline agent |
| **Xác thực** | Google OAuth 2.0 | Gmail SSO cho tất cả vai trò; kiểm tra domain email FPT cho mentor/giám khảo |
| **Email Service** | SendGrid API / SMTP | Gửi email do AI tạo và thông báo hệ thống |
| **LLM API** | Gemini API (Google) hoặc OpenAI API | Sinh nội dung email và câu hỏi phỏng vấn |
| **Timeline Agent** | Python APScheduler / Cron | Scheduler nền; kiểm tra mốc, kích hoạt hành động, ghi log |

## 3. Sơ đồ Kiến trúc

Xem [diagrams/architecture.png] (sẽ thêm vào Tuần 6).

Sơ đồ logic:

```
┌───────────────────────────────────────────────────────┐
│              FRONTEND (React.js/Next.js)               │
│  Trang admin | Cổng thí sinh | Giao diện giám khảo    │
└───────────────────────────┬───────────────────────────┘
                            │ REST API / WebSocket
┌───────────────────────────▼───────────────────────────┐
│                  BACKEND API (Node.js)                 │
│  Auth | Cuộc thi | Đội thi | Điểm | Khiếu nại | Email │
└──────────┬─────────────────────┬─────────────────────┘
           │                     │
    ┌──────▼──────┐     ┌────────▼────────┐
    │  PostgreSQL  │     │   AI Service    │
    │  (dữ liệu)  │     │ (Python/FastAPI) │
    └─────────────┘     │ ┌─────────────┐ │
                        │ │ Sinh Email  │ │
                        │ ├─────────────┤ │
                        │ │ Sinh Câu hỏi│ │
                        │ ├─────────────┤ │
                        │ │  Timeline   │ │
                        │ │  Agent Cron │ │
                        │ └─────────────┘ │
                        └────────┬────────┘
                                 │
                    ┌────────────▼──────────┐
                    │ Dịch vụ Bên ngoài     │
                    │ • Gemini / OpenAI API  │
                    │ • SendGrid (email)     │
                    │ • Google OAuth 2.0     │
                    └───────────────────────┘
```

## 4. Tóm tắt Luồng Dữ liệu

1. **Quản trị viên** tạo cuộc thi → Backend lưu cuộc thi + mốc vào DB
2. **Đội thi** đăng ký → Backend gửi email xác nhận đến tất cả thành viên
3. Sau deadline đăng ký: Backend tự động chia đội vào bảng, gán chủ đề
4. **Timeline Agent** giám sát mốc mỗi phút → kích hoạt hành động khi khớp mốc
5. **Bộ sinh Email AI**: khi có trigger → Backend gửi ngữ cảnh đến AI Service → LLM sinh email → Email Service gửi đi
6. **Cổng thông tin thí sinh**: lấy dữ liệu cuộc thi từ Backend API qua request có xác thực
7. **Giám khảo** đăng nhập (email FPT) → nhập review + điểm → Backend lưu → kích hoạt Bộ sinh Câu hỏi AI
8. **Bộ sinh Câu hỏi AI**: văn bản review + rubric → AI Service → LLM → câu hỏi trả về giao diện giám khảo
9. Tổng hợp điểm → Backend tính xếp hạng → đội top vào chung kết

## 5. Các Điểm Tích hợp AI

| Điểm trong hệ thống | Thành phần AI | Kích hoạt |
|---|---|---|
| Mốc email được kích hoạt | Bộ sinh Email LLM | Timeline Agent trigger hoặc quản trị viên kích hoạt thủ công |
| Giám khảo hoàn thành review | Bộ sinh Câu hỏi LLM | POST /reviews endpoint → gọi AI Service bất đồng bộ |
| Đến deadline cuộc thi | Timeline Agent | Cron job mỗi 60 giây |

## 6. Cân nhắc Bảo mật

- Google OAuth 2.0 cho xác thực thí sinh
- Whitelist domain email FPT cho truy cập giám khảo/mentor
- Kiểm soát truy cập dựa trên vai trò (RBAC) trên tất cả endpoint API
- Email do AI tạo ra có thể qua bước xem xét của quản trị viên trước khi gửi (có thể cấu hình)
- API key LLM lưu trong biến môi trường, không trong codebase
