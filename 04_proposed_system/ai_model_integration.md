# Tích hợp Model AI

## 1. Tổng quan Các Thành phần AI

| Thành phần | Model | Nguồn | Phương thức Tích hợp |
|---|---|---|---|
| Bộ sinh Email | Gemini 1.5 Flash / GPT-4o-mini | Google AI Studio / OpenAI API | REST API call từ AI Service (Python) |
| Bộ sinh Câu hỏi | Gemini 1.5 Pro / GPT-4 | Google AI Studio / OpenAI API | REST API call từ AI Service (Python) |
| Timeline Agent | Cron scheduler rule-based | Built-in (Python APScheduler) | Tiến trình nền, không gọi LLM ngoài |

## 2. Lý do Chọn Model

| Tiêu chí | Bộ sinh Email | Bộ sinh Câu hỏi |
|---|---|---|
| Loại tác vụ | Sinh văn bản có cấu trúc | Phân tích văn bản + lý luận + tổng hợp câu hỏi |
| Độ sâu lý luận | Thấp–Trung bình (tạo mẫu phù hợp ngữ cảnh) | Trung bình–Cao (xác định chủ đề review, lập bản đồ rubric, sinh câu hỏi sâu) |
| Model được chọn | Gemini 1.5 Flash (nhanh, tiết kiệm chi phí) | Gemini 1.5 Pro (lý luận tốt hơn) |
| Đầu vào | Các trường ngữ cảnh cuộc thi | Văn bản review + rubric cuộc thi |
| Đầu ra | Tiêu đề + nội dung email (HTML/text) | Danh sách 5–7 câu hỏi phỏng vấn |
| Yêu cầu chất lượng | Giọng điệu, rõ ràng, liên quan | Chiều sâu, bao phủ, đặc thù review |
| Độ trễ | Chấp nhận được (bất đồng bộ) | Chấp nhận được (xử lý nền) |

## 3. Nguồn LLM

- Gemini API (Google) hoặc OpenAI API
- Mẫu prompt lưu trong database, có thể cấu hình theo từng cuộc thi

## 4. Đặc tả Đầu vào/Đầu ra

### Bộ sinh Email

**4 loại email và ngữ cảnh cần thiết:**

| Loại email | Kích hoạt | Biến ngữ cảnh chính |
|---|---|---|
| Thông báo vào chung kết | Timeline Agent: sau khi hoàn thành chấm điểm sơ khảo | tên_cuộc_thi, tên_bảng, tên_đội, số_đội_vào_chung_kết, ngày_chung_kết |
| Nhắc deadline | Timeline Agent: N ngày trước hạn nộp | tên_cuộc_thi, tên_đội, ngày_deadline, link_nộp_bài |
| Cảnh báo chưa nộp | Timeline Agent: X giờ trước deadline, nếu chưa có bài nộp | tên_cuộc_thi, tên_đội, thời_gian_deadline, liên_hệ_admin |
| Phân công mentor | Admin kích hoạt sau phân công | tên_đội, tên_mentor, email_mentor, chủ_đề_bảng, hướng_dẫn_gặp |

**Cấu trúc mẫu Prompt (Bộ sinh Email):**

```
System: Bạn là điều phối viên cuộc thi học thuật tại Đại học FPT.
Hãy viết một email chuyên nghiệp, rõ ràng và khuyến khích
cho tình huống sau. Sử dụng tiếng Việt trang trọng (hoặc tiếng Anh theo yêu cầu).
Không bao gồm dấu ngoặc vuông placeholder. Giữ trong 150–250 từ.

User:
Cuộc thi: {tên_cuộc_thi}
Loại email: {loại_email}
Người nhận: Đội "{tên_đội}" ({danh_sách_thành_viên})
Ngữ cảnh: {các_trường_đặc_thù}
Giọng điệu: {hướng_dẫn_giọng_điệu}

Định dạng trả về:
Tiêu đề: ...
Nội dung: ...
```

**Quy tắc Kiểm tra Đầu ra:**

- Tiêu đề: 10–80 ký tự
- Nội dung: 100–300 từ
- Bắt buộc chứa: tên cuộc thi, tên đội, ít nhất một hành động cụ thể
- Không có placeholder (ví dụ: "[NHẬP NGÀY]")

### Bộ sinh Câu hỏi

**Đầu vào:**

```json
{
  "van_ban_review": "Đội đã thể hiện kỹ năng phân tích vấn đề tốt...
                     Tuy nhiên, lý do kỹ thuật chọn PostgreSQL thay vì NoSQL chưa rõ...",
  "tieu_chi_rubric": ["Phân tích vấn đề", "Kiến trúc kỹ thuật",
                       "Tích hợp AI", "Chất lượng demo", "Trình bày nhóm"],
  "mo_ta_du_an": "Hệ thống quản lý tồn kho thông minh sử dụng LSTM...",
  "vong_thi": "Sơ khảo"
}
```

**Cấu trúc mẫu Prompt (Bộ sinh Câu hỏi):**

```
System: Bạn là giám khảo học thuật giàu kinh nghiệm tại Đại học FPT.
Dựa trên bài đánh giá dự án được cung cấp, hãy tạo 5–7 câu hỏi phỏng vấn
để hỏi đội trong buổi bảo vệ vấn đáp.
Câu hỏi PHẢI được bám sát các quan sát cụ thể trong bài đánh giá.
Lập bản đồ mỗi câu hỏi vào một tiêu chí rubric.
Câu hỏi phải kiểm tra sự hiểu biết, không chỉ nhắc lại.

User:
Mô tả dự án: {mo_ta_du_an}
Bài đánh giá: {van_ban_review}
Tiêu chí rubric: {tieu_chi_rubric}

Trả về dưới dạng JSON array:
[
  {"cau_hoi": "...", "tieu_chi": "Kiến trúc kỹ thuật", "dua_tren": "..."},
  ...
]
```

**Hậu xử lý:**

1. Phân tích đầu ra JSON
2. Loại trùng lặp câu hỏi có cosine similarity > 0,85
3. Đảm bảo ít nhất một câu hỏi cho mỗi tiêu chí rubric chính xuất hiện trong review
4. Sắp xếp theo thứ tự tiêu chí rubric
5. Lưu vào database, hiển thị trong giao diện giám khảo

## 5. Timeline Agent — Đặc tả

```python
# Chạy mỗi 60 giây (APScheduler)
def kiem_tra_moc():
    cac_moc = db.lay_moc_cho_xu_ly(thoi_gian_hien_tai)
    for moc in cac_moc:
        if moc.loai == "DONG_CONG_NOP_BAI":
            dong_cong_nop_bai(moc.id_cuoc_thi)
            danh_dau_hoan_thanh(moc.id)
        elif moc.loai == "THONG_BAO_CHUNG_KET":
            tong_hop_diem(moc.id_cuoc_thi)
            kich_hoat_sinh_email("CHUNG_KET", moc.id_cuoc_thi)
            danh_dau_hoan_thanh(moc.id)
        elif moc.loai == "NHAC_DEADLINE":
            kich_hoat_sinh_email("NHAC", moc.id_cuoc_thi)
            danh_dau_hoan_thanh(moc.id)
        elif moc.loai == "CANH_BAO_CHUA_NOP":
            cac_doi = lay_doi_chua_nop(moc.id_cuoc_thi)
            for doi in cac_doi:
                kich_hoat_sinh_email("CHUA_NOP", moc.id_cuoc_thi, doi.id)
            danh_dau_hoan_thanh(moc.id)
        ghi_log(moc.id, "da_thuc_hien", thoi_gian_hien_tai)
```

## 6. So sánh với Baseline

| Thành phần | Hệ thống của chúng tôi | Baseline |
|---|---|---|
| Sinh email | LLM sinh, phù hợp ngữ cảnh | Admin viết tay hoặc dùng mẫu cố định |
| Sinh câu hỏi | LLM từ văn bản review | Giám khảo soạn tay |
| Quản lý timeline | Agent tự động | Theo dõi thủ công bằng lịch |

## 7. Hạn chế và Biện pháp Giảm thiểu

| Hạn chế | Biện pháp giảm thiểu |
|---|---|
| LLM hallucination trong email | Bước xem xét của admin trước khi gửi; quy tắc kiểm tra đầu ra |
| Câu hỏi chung chung không bám review | Prompt yêu cầu rõ ràng câu hỏi "dựa trên quan sát cụ thể" |
| Chi phí LLM API | Dùng Flash model cho email (chi phí thấp), Pro model chỉ cho câu hỏi |
| Độ trễ LLM API | Xử lý bất đồng bộ; câu hỏi sinh nền, không chặn giám khảo |
| Downtime API | Fallback: trả về kết quả rỗng có thông báo lỗi, cho phép giám khảo tiếp tục thủ công |
