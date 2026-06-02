# Baseline

## 1. Mục đích của Baseline

Baseline xác định "trạng thái hiện tại" hoặc cách tiếp cận đơn giản nhất trước đây cho từng thành phần AI. So sánh ACMS-AI với các baseline này chứng minh giá trị cụ thể mà tích hợp AI mang lại.

## 2. Baseline cho Từng Thành phần AI

### 2.1. Baseline Bộ sinh Email

**Baseline chính**: Email viết tay bởi quản trị viên

- Quản trị viên viết từng email từ đầu dựa trên kinh nghiệm và ngữ cảnh cuộc thi
- Thực hành thông thường: viết từ trí nhớ, tham khảo email mẫu cũ, hoặc soạn mới
- Cùng 80 kịch bản được dùng cho cả sản xuất email AI và thủ công
- Quản trị viên được cung cấp cùng thông tin ngữ cảnh như LLM

**Lý do chọn baseline này**: Đây là thực hành hiện tại tại các cuộc thi FPT. Đây là so sánh liên quan nhất để chứng minh tiết kiệm thời gian và cải thiện chất lượng trong thực tế.

**Baseline phụ** (tùy chọn): Email theo mẫu cố định — mẫu điền thông tin với không có AI, chỉ chèn các trường. Dùng để tách biệt đóng góp của việc sinh LLM so với chỉ điền mẫu đơn giản.

### 2.2. Baseline Bộ sinh Câu hỏi Phỏng vấn

**Baseline A**: Câu hỏi do giám khảo soạn (chính)

- Giám khảo có kinh nghiệm nhận 30 bài đánh giá tương tự
- Giám khảo chuẩn bị câu hỏi phỏng vấn như thường lệ, không có hỗ trợ AI
- Tính giờ từ lúc nhận bài review đến khi hoàn thành danh sách câu hỏi
- Đầu ra: bộ câu hỏi do giám khảo soạn dùng để so sánh chất lượng

**Baseline B**: Danh sách câu hỏi chung (phụ)

- Một danh sách cố định 10 câu hỏi cuộc thi chung (không được điều chỉnh cho bài review cụ thể nào)
- Dùng để chứng minh câu hỏi do AI tạo có tính đặc thù hơn câu hỏi chung
- Đại diện cho tình huống giám khảo không có thời gian chuẩn bị

**Lý do chọn baseline này**: Baseline A là hiệu suất tốt nhất của con người; Baseline B là thực hành hiện tại với nỗ lực tối thiểu.

### 2.3. Baseline Timeline Agent

**Baseline**: Theo dõi deadline thủ công

- Quản trị viên tự kiểm tra thời gian hiện tại đối chiếu với lịch mốc
- Dùng nhắc lịch (Google Calendar, chuông điện thoại) làm công cụ chính
- Phải thực hiện hành động thủ công: đóng cổng, gửi thông báo, cập nhật trạng thái
- Kiểm thử trên cùng 50 sự kiện mốc như agent tự động

**Đo lường**:

- **Độ chính xác**: % mốc thực hiện đúng hành động
- **Sai lệch thời gian**: |thời_gian_thực_tế − thời_gian_mốc_dự_kiến| tính bằng phút
- **Tỷ lệ lỗi**: % mốc bị bỏ sót hoặc thực hiện sai

**Lý do chọn baseline này**: Theo dõi thủ công là cách tiếp cận hiện tại và đại diện cho độ tin cậy để đánh giá agent tự động.

## 3. Bảng So sánh Đánh giá

| Thành phần | Hệ thống của chúng tôi | Baseline chính | Baseline phụ | Chỉ số |
|---|---|---|---|---|
| Email thông báo vào chung kết | LLM sinh (Gemini Flash) | Admin viết tay | Mẫu cố định | Điểm chuyên gia (5 chiều), thời gian sản xuất |
| Email nhắc deadline | LLM sinh | Admin viết tay | Mẫu cố định | Điểm chuyên gia, thời gian |
| Email cảnh báo chưa nộp | LLM sinh | Admin viết tay | Mẫu cố định | Điểm chuyên gia, thời gian |
| Email phân công mentor | LLM sinh | Admin viết tay | Mẫu cố định | Điểm chuyên gia, thời gian |
| Câu hỏi phỏng vấn từ review | LLM sinh (Gemini Pro) | Giám khảo soạn tay | Danh sách câu hỏi chung | Điểm chuyên gia (4 chiều), thời gian, bao phủ |
| Thực thi timeline | Agent tự động | Theo dõi thủ công | Nhắc lịch đơn giản | Độ chính xác, sai lệch thời gian, tỷ lệ lỗi |

## 4. Lưu ý về So sánh Công bằng

- Tất cả baseline sử dụng **cùng thông tin đầu vào** như hệ thống AI (cùng ngữ cảnh kịch bản cho email; cùng bài review cho câu hỏi)
- Tác giả email và người soạn câu hỏi baseline không nhìn thấy đầu ra AI trong khi làm việc
- Đánh giá là **mù**: người đánh giá không biết phiên bản nào là AI hay con người
- Thời gian được đo là thời gian thực (đồng hồ bấm tay) từ khi bắt đầu đến khi hoàn thành cho cả AI và baseline
