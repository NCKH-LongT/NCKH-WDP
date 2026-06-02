# Thiết lập Thực nghiệm

## 1. Môi trường

### 1.1. Môi trường Phần mềm

| Thành phần | Thông số |
|---|---|
| Hệ điều hành (máy chủ) | Ubuntu 22.04 LTS (Docker container) |
| Frontend | React.js 18 + Next.js 14, Node.js 18 |
| Backend | Node.js 20 + Express 4 |
| Database | PostgreSQL 16 |
| AI Service | Python 3.11, FastAPI 0.111, APScheduler 3.10 |
| LLM (sinh email) | Gemini 1.5 Flash (qua Google AI Studio API) |
| LLM (sinh câu hỏi) | Gemini 1.5 Pro (qua Google AI Studio API) |
| Gửi email | SendGrid API (free tier cho kiểm thử) |
| Xác thực | Google OAuth 2.0 |
| Triển khai | Docker Compose (local) / Google Cloud Run (kiểm thử production) |

### 1.2. Môi trường Phần cứng

| Môi trường | Thông số |
|---|---|
| Phát triển | Windows 11 / macOS, 16GB RAM, Docker local |
| Máy chủ đánh giá | Google Cloud VM (e2-standard-2: 2 vCPU, 8GB RAM) |

## 2. Cấu hình Dữ liệu Đánh giá

### 2.1. Đánh giá Email (RQ1)

| Tham số | Giá trị |
|---|---|
| Tổng số cặp kịch bản | 80 (AI và tay) |
| Kịch bản mỗi loại email | 20 |
| Phiên bản AI | Sinh bởi Gemini 1.5 Flash với prompt đã hoàn thiện |
| Phiên bản tay | Viết bởi 2 nhân viên quản trị FPT |
| Người đánh giá | 3–5 giảng viên FPT có kinh nghiệm chấm thi |
| Chiều đánh giá | 5 (liên quan, giọng điệu, rõ ràng, đầy đủ, tổng thể) |
| Thang đo | Likert 1–5 |
| Đánh giá mù | Có — người đánh giá không biết AI hay tay |

### 2.2. Đánh giá Sinh Câu hỏi (RQ2)

| Tham số | Giá trị |
|---|---|
| Bài đánh giá dự án | 30 (thực tế hoặc mô phỏng) |
| Bộ câu hỏi AI | 30 (5–7 câu mỗi bộ) |
| Bộ câu hỏi chuyên gia | 30 (từ 3–5 giám khảo, cùng bài review) |
| Người đánh giá | Cùng 3–5 giảng viên như đánh giá email |
| Chiều đánh giá | 4 (bao phủ, liên quan đến review, chiều sâu, tính hữu ích) |
| Thang đo | Likert 1–5 |
| Đánh giá mù | Có |

### 2.3. Kiểm tra Timeline Agent (RQ3)

| Tham số | Giá trị |
|---|---|
| Tổng mốc kiểm thử | 50 |
| Loại mốc | 4 (DONG_CONG, THONG_BAO_CK, NHAC_DEADLINE, CANH_BAO_CHUA_NOP) |
| Mỗi loại | ~12–13 mốc |
| Dịch chỉnh thời gian | Mốc đặt trước 5–60 phút trong môi trường kiểm thử |
| Đo lường | Thời gian thực tế vs. dự kiến, kết quả hành động |
| Baseline thủ công | 2 admin giám sát cùng mốc bằng nhắc lịch |

### 2.4. Đo Hiệu quả (RQ4)

| Tác vụ | Điều kiện AI | Điều kiện thủ công | Số người tham gia |
|---|---|---|---|
| Sinh email (cả 4 loại) | Dùng bộ sinh email ACMS-AI | Viết tay từ cùng ngữ cảnh | 5 admin |
| Chuẩn bị câu hỏi | Dùng bộ sinh câu hỏi ACMS-AI | Chuẩn bị tay từ cùng bài review | 5 giám khảo |
| Thiết kế | Counterbalanced (A/B → B/A) | | |

### 2.5. Nghiên cứu Khả năng Sử dụng

| Vai trò | Bộ tác vụ | Thời điểm SUS | Số người tham gia |
|---|---|---|---|
| Admin | Tạo cuộc thi + cấu hình mốc + xem xét email AI | Sau tác vụ | ≥ 10 |
| Giám khảo | Đăng nhập + nhập review + dùng câu hỏi AI + nộp điểm | Sau tác vụ | ≥ 10 |
| Thí sinh | Đăng nhập + xem cổng thông tin + điều hướng thông tin đội/chủ đề/countdown | Sau tác vụ | ≥ 10 |

## 3. Cấu hình LLM API

| Cài đặt | Bộ sinh Email | Bộ sinh Câu hỏi |
|---|---|---|
| Model | gemini-1.5-flash-latest | gemini-1.5-pro-latest |
| Temperature | 0,3 (thấp hơn cho định dạng nhất quán) | 0,5 (sáng tạo vừa phải) |
| Max output tokens | 512 (email) | 1024 (câu hỏi) |
| Top-P | 0,95 | 0,95 |
| Thử lại khi thất bại | Có (tối đa 2 lần) | Có (tối đa 2 lần) |

## 4. Quy trình Độ tin cậy Giữa Người đánh giá

- Tất cả người đánh giá tham dự buổi hiệu chỉnh 30 phút trước khi đánh giá
- Thực hành với item mẫu (5 email, 5 bộ câu hỏi) được xem xét và thảo luận chung
- Các item được đánh giá độc lập (không thảo luận trong khi đánh giá)
- Độ nhất quán giữa người đánh giá được tính bằng Fleiss' kappa
- Ngưỡng chấp nhận: kappa ≥ 0,6 (nhất quán đáng kể)
- Các item có bất đồng cao (khoảng cách ≥ 3 điểm) được xem xét lại trong buổi đồng thuận
