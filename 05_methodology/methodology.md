# Phương pháp Nghiên cứu

## 1. Hướng tiếp cận Nghiên cứu

Nghiên cứu này áp dụng phương pháp **Design Science Research** kết hợp với **đánh giá thực nghiệm**. Chúng tôi (1) thiết kế và triển khai hệ thống ACMS-AI, (2) triển khai trong môi trường đánh giá có kiểm soát, và (3) đo lường thực nghiệm chất lượng và hiệu quả của các thành phần AI so với baseline thủ công.

Nghiên cứu này không nhằm đề xuất một mô hình AI hoàn toàn mới, mà tập trung khảo sát cách tích hợp các LLM hiện có vào một luồng quản lý cuộc thi đặc thù và đánh giá hiệu quả trong việc tự động hóa truyền thông và hỗ trợ chuẩn bị giám khảo.

## 2. Phương pháp Phát triển Hệ thống

### 2.1. Hướng tiếp cận Phát triển

- **Phát triển agile lặp lại**: Sprint 2 tuần
- **Phát triển theo module**: Xây dựng và kiểm thử từng module độc lập trước khi tích hợp
- **Vòng lặp prompt engineering**: Tinh chỉnh lặp lại prompt LLM qua các pilot đánh giá quy mô nhỏ

### 2.2. Công nghệ Sử dụng

| Tầng | Công nghệ |
|---|---|
| Frontend | React.js / Next.js, Tailwind CSS |
| Backend | Node.js + Express |
| Database | PostgreSQL |
| AI Service | Python 3.11, FastAPI |
| LLM | Gemini 1.5 Flash (email), Gemini 1.5 Pro (câu hỏi) |
| Xác thực | Google OAuth 2.0 |
| Gửi Email | SendGrid API |
| Triển khai | Docker + Cloud VM (GCP hoặc tương tự) |

## 3. Phát triển Các Thành phần AI

### 3.1. Pipeline Sinh Email

**Bước 1: Xác định loại email và các trường ngữ cảnh cần thiết**

- Xác định 4 loại thông báo và điều kiện kích hoạt của từng loại
- Lập bản đồ từng loại vào các trường ngữ cảnh bắt buộc (tên đội, deadline, tên mentor, v.v.)

**Bước 2: Prompt engineering**

- Viết mẫu prompt cơ bản cho từng loại email
- Chạy pilot 20 mẫu: sinh email → đánh giá chuyên gia → tinh chỉnh prompt
- Hoàn thiện prompt sau khi đạt điểm trung bình ≥ 3,5/5 trong pilot

**Bước 3: Tích hợp**

- Triển khai endpoint `POST /sinh-email` trong AI Service (FastAPI)
- Kết nối Backend với AI Service qua REST call nội bộ
- Thêm lớp kiểm tra đầu ra (độ dài tiêu đề, độ dài nội dung, không có placeholder)

**Bước 4: Giao diện xem xét của admin**

- Xây dựng giao diện xem xét bản nháp email trong dashboard admin
- Cho phép admin duyệt/chỉnh sửa trước khi gửi
- Ghi log tất cả lần gửi với timestamp và nội dung đã tạo

### 3.2. Pipeline Sinh Câu hỏi Phỏng vấn

**Bước 1: Xác định schema đầu vào**

- Văn bản review (dạng tự do, ≤ 1000 từ)
- Rubric cuộc thi (5–6 tiêu chí kèm mô tả)
- Mô tả dự án (≤ 200 từ)

**Bước 2: Prompt engineering cho sinh câu hỏi**

- Thiết kế prompt hướng dẫn LLM: xác định chủ đề chính trong review → lập bản đồ vào rubric → sinh câu hỏi thăm dò
- Pilot: 10 bài review → giám khảo chuyên gia đánh giá câu hỏi → tinh chỉnh prompt

**Bước 3: Hậu xử lý**

- Phân tích đầu ra JSON
- Loại trùng lặp câu hỏi bằng cosine similarity (ngưỡng 0,85)
- Đảm bảo bao phủ tất cả tiêu chí rubric chính xuất hiện trong review
- Sắp xếp theo thứ tự tiêu chí rubric

**Bước 4: Tích hợp giao diện giám khảo**

- Hiển thị câu hỏi được tạo sau khi giám khảo gửi review
- Cho phép giám khảo ẩn/hiện, đánh dấu đã dùng, thêm câu hỏi tùy chỉnh

### 3.3. Timeline Agent

**Bước 1: Định nghĩa schema mốc**

```
moc: {
  id, id_cuoc_thi, loai_moc, thoi_gian_muc_tieu, hanh_dong, trang_thai
}
```

**Bước 2: Triển khai scheduler**

- Python APScheduler chạy mỗi 60 giây
- Truy vấn: `SELECT * FROM moc WHERE thoi_gian_muc_tieu <= NOW() AND trang_thai = 'CHO_XU_LY'`
- Thực thi hành động theo loại mốc
- Cập nhật trạng thái thành ĐÃ THỰC THI kèm thoi_gian_thuc_te

**Bước 3: Ghi log và xử lý lỗi**

- Ghi log tất cả thực thi mốc (thời gian dự kiến, thực tế, kết quả hành động)
- Khi thất bại: thử lại 1 lần sau 60 giây, sau đó cảnh báo admin
- Theo dõi sai lệch thời gian cho mục đích đánh giá

## 4. Phương pháp Đánh giá

Xem các file riêng:

- [evaluation_metrics.md](evaluation_metrics.md) — chỉ số và quy trình
- [baseline.md](baseline.md) — định nghĩa baseline
- [dataset.md](dataset.md) — nguồn và kích thước dữ liệu
