# Kế hoạch Đánh giá

## 1. Mục tiêu Đánh giá

1. Đo chất lượng email thông báo cuộc thi do LLM tạo so với email viết tay
2. Đo chất lượng câu hỏi phỏng vấn do LLM tạo so với câu hỏi do giám khảo soạn
3. Đánh giá độ tin cậy và chính xác của timeline agent tự động so với giám sát thủ công
4. Lượng hóa hiệu quả (thời gian tiết kiệm) cho quản trị viên và giám khảo
5. Đánh giá khả năng sử dụng tổng thể của hệ thống trên cả 3 vai trò người dùng

## 2. Tóm tắt Dữ liệu

- 80 cặp email AI và tay (20 mỗi loại thông báo)
- 30 bộ câu hỏi do AI tạo và do chuyên gia soạn
- 50 sự kiện mốc mô phỏng để kiểm tra timeline agent
- ≥ 30 người tham gia đánh giá khả năng sử dụng SUS

## 3. Baseline

Xem [baseline.md](baseline.md).

## 4. Chỉ số Đánh giá

### 4.1. Chỉ số Chất lượng Email (RQ1)

| Chỉ số | Thang đo | Mô tả | Lý do sử dụng |
|---|---|---|---|
| Mức độ liên quan | Likert 1–5 | Email có đề cập chính xác sự kiện cuộc thi và đội không? | Chiều chất lượng cốt lõi; email chung chung thất bại ở đây |
| Giọng điệu | Likert 1–5 | Giọng điệu email có phù hợp (trang trọng, chuyên nghiệp, lịch sự) không? | Giọng điệu kém làm mất tin tưởng |
| Rõ ràng | Likert 1–5 | Email có dễ hiểu, truyền đạt thông tin cần thiết rõ ràng không? | Rõ ràng quyết định người nhận có hiểu và hành động đúng không |
| Đầy đủ | Likert 1–5 | Email có bao gồm tất cả thông tin cần thiết để người nhận hành động không? | Thiếu thông tin gây nhầm lẫn và câu hỏi theo dõi |
| Chất lượng tổng thể | Likert 1–5 | Đánh giá tổng thể của email | Chỉ số tổng hợp để báo cáo trên bài báo |
| Thời gian sản xuất | Phút | Thời gian thực từ khi có thông tin ngữ cảnh đến khi email sẵn sàng gửi | Chỉ số hiệu quả |

### 4.2. Chỉ số Chất lượng Câu hỏi Phỏng vấn (RQ2)

| Chỉ số | Thang đo | Mô tả | Lý do sử dụng |
|---|---|---|---|
| Bao phủ | Likert 1–5 | Câu hỏi có bao phủ các chủ đề/vấn đề chính được xác định trong bài review không? | Đảm bảo giám khảo đề cập đến phản hồi quan trọng |
| Liên quan đến bài review | Likert 1–5 | Câu hỏi có được bám rõ vào nội dung review cụ thể (không chung chung) không? | Phân biệt câu hỏi có đích thực và câu hỏi chung |
| Chiều sâu | Likert 1–5 | Câu hỏi có thăm dò sự hiểu biết, không chỉ nhắc lại không? | Phỏng vấn phải kiểm tra năng lực thực sự |
| Tính hữu ích | Likert 1–5 | Bạn có dùng những câu hỏi này trong buổi vấn đáp thực tế không? | Kiểm tra khả năng ứng dụng thực tiễn |
| Thời gian sản xuất | Phút | Thời gian từ khi nhận bài review đến khi hoàn thành bộ câu hỏi | Chỉ số hiệu quả |

### 4.3. Chỉ số Timeline Agent (RQ3)

| Chỉ số | Đơn vị | Mô tả | Mục tiêu |
|---|---|---|---|
| Độ chính xác mốc | % | % mốc thực hiện đúng hành động | ≥ 98% |
| Sai lệch thời gian | Giây | thời_gian_thực_tế − thời_gian_dự_kiến | ≤ 60 giây |
| Tỷ lệ lỗi | % | % mốc bị bỏ sót hoặc thực hiện sai | ≤ 2% |
| Tỷ lệ khôi phục | % | % mốc thất bại được khôi phục trong 5 phút | ≥ 95% |

### 4.4. Chỉ số Hiệu quả Hệ thống (RQ4)

| Chỉ số | Đo lường cho | Phương pháp |
|---|---|---|
| Thời gian tiết kiệm sinh email | Admin (tác vụ sinh email) | Bấm giờ: đường AI vs. baseline thủ công |
| Thời gian tiết kiệm sinh câu hỏi | Giám khảo (tác vụ sinh câu hỏi) | Bấm giờ: đường AI vs. baseline thủ công |
| % giảm thời gian | Cả 2 vai trò | (thời_gian_thủ_công − thời_gian_ai) / thời_gian_thủ_công × 100 |

### 4.5. Khả năng Sử dụng Hệ thống (SUS)

| Vai trò | Cách tiến hành SUS | Số người tham gia tối thiểu |
|---|---|---|
| Quản trị viên | Sau khi hoàn thành: tạo cuộc thi + duyệt email | 10 |
| Giám khảo | Sau khi hoàn thành: nhập review + dùng câu hỏi AI + chấm điểm | 10 |
| Thí sinh | Sau khi hoàn thành: đăng nhập + điều hướng cổng thông tin | 10 |

Giải thích điểm SUS: < 51 = không chấp nhận được, 51–67 = biên, 68 = trung bình, > 80 = xuất sắc

## 5. Quy trình Đánh giá

**Bước 1 — Chuẩn bị (Tuần 10–11)**

- Sinh 80 kịch bản email và sản xuất cả phiên bản AI và tay
- Thu thập 30 bài review; sản xuất bộ câu hỏi AI và giám khảo
- Cấu hình 50 mốc kiểm thử timeline mô phỏng

**Bước 2 — Đánh giá Mù Chuyên gia (Tuần 12)**

- Tuyển 3–5 giảng viên FPT có kinh nghiệm chấm thi
- Cung cấp rubric đánh giá và buổi tập huấn (30 phút)
- Mỗi người đánh giá chấm tất cả item mà không biết nhãn AI hay con người
- Mỗi item được ít nhất 2 người đánh giá; tính độ nhất quán giữa người đánh giá (Fleiss' kappa)

**Bước 3 — Kiểm tra Timeline Agent (Tuần 12)**

- Triển khai agent với 50 mốc tổng hợp trong môi trường kiểm thử
- Ghi lại: thời gian dự kiến, thời gian thực tế, kết quả hành động
- Tính độ chính xác, sai lệch, tỷ lệ lỗi

**Bước 4 — Đo Hiệu quả (Tuần 12)**

- 5 người tham gia admin: hoàn thành tác vụ sinh email có và không có AI (counterbalanced)
- 5 người tham gia giám khảo: hoàn thành chuẩn bị câu hỏi có và không có AI (counterbalanced)
- Ghi lại thời gian thực mỗi tác vụ

**Bước 5 — Nghiên cứu Khả năng Sử dụng SUS (Tuần 13)**

- Triển khai prototype ACMS-AI
- ≥ 10 người tham gia mỗi vai trò hoàn thành tác vụ được giao
- Phát bảng khảo sát SUS 10 item sau khi hoàn thành tác vụ

**Bước 6 — Phân tích (Tuần 14)**

- Tính trung bình và độ lệch chuẩn cho tất cả chỉ số đánh giá
- Kiểm định Mann–Whitney U hoặc t-test cho so sánh AI vs. tay
- Cohen's d cho kích thước hiệu ứng
- Báo cáo kappa giữa người đánh giá cho đánh giá mù

## 6. Kết quả Dự kiến

| Chỉ số | Kết quả Dự kiến | Cơ sở |
|---|---|---|
| Chất lượng email tổng thể (AI) | ≥ 3,5/5 | Dựa trên AI-Augmented Advising (AI đạt 3,8–3,9/5) |
| Bao phủ câu hỏi (AI) | ≥ 3,5/5 | Dựa trên tài liệu sinh quiz (3,9/5) |
| Độ chính xác timeline | ≥ 98% | Lập lịch xác định; ngoại trừ lỗi hệ thống |
| Thời gian tiết kiệm admin (email) | ≥ 40% | Dựa trên tài liệu quản lý sự kiện |
| Thời gian tiết kiệm giám khảo (câu hỏi) | ≥ 50% | Sinh LLM (~5 giây) vs. thủ công (~20 phút) |
| SUS tổng thể | ≥ 68 | Mục tiêu khả năng sử dụng "trên trung bình"; mục tiêu ≥ 80 "xuất sắc" |
