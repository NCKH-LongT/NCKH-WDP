# Phương pháp (Bản nháp)

## 3.1 Kiến trúc Hệ thống

ACMS-AI theo kiến trúc đa tầng với lớp AI Service riêng biệt tách rời khỏi backend chính. Frontend (React.js/Next.js) phục vụ ba giao diện phân quyền: dashboard admin, cổng thông tin thí sinh và giao diện giám khảo. Backend API (Node.js + Express) xử lý logic nghiệp vụ, xác thực và điều phối gọi AI Service. AI Service (Python + FastAPI) chịu trách nhiệm tất cả gọi LLM API và timeline agent nền. PostgreSQL lưu trữ tất cả dữ liệu cuộc thi, bao gồm bản nháp nội dung AI. Xác thực sử dụng Google OAuth 2.0 cho tất cả vai trò, với kiểm tra bắt buộc domain email FPT cho truy cập giám khảo.

## 3.2 Bộ sinh Email LLM

Cho từng bốn loại thông báo, chúng tôi thiết kế mẫu prompt có cấu trúc chứa: (1) hướng dẫn hệ thống thiết lập ngữ cảnh tổ chức và yêu cầu giọng điệu; (2) biến ngữ cảnh đặc thù cuộc thi (tên đội, ngày deadline, thông tin bảng, tên mentor); và (3) đặc tả định dạng đầu ra. Prompt được tinh chỉnh lặp qua pilot 20 mẫu: email được tạo ra được 2 người đánh giá, và prompt được điều chỉnh cho đến khi điểm trung bình pilot đạt ≥ 3,5/5.

Gemini 1.5 Flash được chọn cho sinh email dựa trên độ trễ thấp và hiệu quả chi phí. Đầu ra được kiểm tra trước khi lưu: tiêu đề phải dài 10–80 ký tự, nội dung 100–300 từ, và không có dấu ngoặc vuông placeholder (ví dụ "[TÊN ĐỘI]") còn lại.

## 3.3 Bộ sinh Câu hỏi Phỏng vấn từ Bài đánh giá

Pipeline sinh câu hỏi nhận ba đầu vào: (1) bài đánh giá dạng văn bản tự do của giám khảo về bài nộp dự án; (2) rubric cuộc thi (5–6 tiêu chí đánh giá kèm mô tả); và (3) mô tả dự án (≤ 200 từ). Prompt có cấu trúc hướng dẫn Gemini 1.5 Pro xác định các chủ đề chính từ bài review, lập bản đồ chúng vào tiêu chí rubric và sinh 5–7 câu hỏi mở thăm dò — mỗi câu được bám rõ ràng vào một quan sát cụ thể trong bài review. Đầu ra được trả về dạng JSON array với các trường: cau_hoi, tieu_chi (tiêu chí rubric) và dua_tren (đoạn trích bài review). Hậu xử lý loại câu hỏi trùng lặp với cosine similarity > 0,85 và đảm bảo bao phủ ít nhất các tiêu chí rubric chính được đề cập trong bài review.

## 3.4 Timeline AI Agent

Timeline agent là dịch vụ nền Python sử dụng APScheduler, kiểm tra bảng mốc cuộc thi mỗi 60 giây. Khi khớp thời gian mục tiêu của một mốc, agent thực thi hành động liên quan: đóng cổng nộp bài (cập nhật cờ database), kích hoạt sinh email, cập nhật trạng thái cuộc thi hoặc kiểm tra đội chưa nộp bài. Tất cả thực thi được ghi log với thoi_gian_du_kien, thoi_gian_thuc_te và ket_qua_hanh_dong cho mục đích đánh giá.

## 3.5 Thiết kế Đánh giá

**Chất lượng Email (RQ1)**: 80 kịch bản email cuộc thi (20 mỗi loại thông báo) được chuẩn bị. Cho mỗi kịch bản, cả hệ thống AI và quản trị viên (không nhìn thấy đầu ra AI) đều sản xuất một email. Ba đến năm người đánh giá chuyên gia (giảng viên FPT có kinh nghiệm chấm thi) mù quáng đánh giá cả hai phiên bản trên năm chiều — liên quan, giọng điệu, rõ ràng, đầy đủ và chất lượng tổng thể — sử dụng thang Likert 5 điểm. So sánh thống kê dùng kiểm định Mann-Whitney U; kích thước hiệu ứng được báo cáo là Cohen's d.

**Chất lượng Câu hỏi (RQ2)**: 30 bài đánh giá dự án được dùng làm đầu vào. Cả bộ sinh AI và giám khảo có kinh nghiệm đều sản xuất bộ câu hỏi từ cùng tài liệu. Người đánh giá chuyên gia đánh giá cả hai bộ trên bốn chiều: bao phủ, liên quan đến bài review, chiều sâu và tính hữu ích. Cùng quy trình đánh giá mù và phương pháp thống kê được áp dụng.

**Độ Chính xác Timeline (RQ3)**: 50 mốc tổng hợp (dịch thời gian cho kiểm thử) được xử lý bởi cả agent tự động và quản trị viên dùng nhắc lịch. Sai lệch thời gian (|thực_tế − dự_kiến| tính bằng giây) và tỷ lệ lỗi (bỏ sót hoặc sai hành động) được ghi lại.

**Hiệu quả (RQ4)**: Năm quản trị viên hoàn thành tác vụ sinh email có và không có hỗ trợ AI (thứ tự A/B counterbalanced). Năm giám khảo hoàn thành chuẩn bị câu hỏi có và không có AI. Thời gian thực được ghi lại cho mỗi điều kiện.

**Khả năng Sử dụng (SUS)**: ≥ 10 người tham gia mỗi vai trò (admin, giám khảo, thí sinh) hoàn thành tác vụ được giao trong prototype hệ thống rồi điền bảng khảo sát SUS 10 item.
