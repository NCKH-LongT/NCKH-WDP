# Tóm tắt (Bản nháp v1)

## Từ khóa

mô hình ngôn ngữ lớn, quản lý cuộc thi, tự động hóa email, sinh câu hỏi phỏng vấn, cuộc thi học thuật, tự động hóa AI, hệ thống quản lý tích hợp AI

---

## Bản nháp

Quản lý các cuộc thi học thuật tại các trường đại học đòi hỏi nhiều quy trình lặp lại và dễ mắc lỗi: quản trị viên phải soạn thủ công email thông báo cho từng mốc cuộc thi, giám khảo tốn nhiều thời gian soạn câu hỏi phỏng vấn từ bài review dự án, và deadline nộp bài được giám sát bằng tay thay vì hệ thống tự động. Những kém hiệu quả này làm giảm chất lượng vận hành và khả năng mở rộng khi số đội thi tăng lên.

Bài báo này giới thiệu **ACMS-AI**, một Hệ thống Quản lý Cuộc thi Học thuật Tích hợp AI tích hợp khả năng của mô hình ngôn ngữ lớn (LLM) vào nền tảng quản lý cuộc thi đầy đủ. Hệ thống đề xuất ba module được hỗ trợ bởi AI: (1) **Bộ sinh Email LLM** tự động soạn bốn loại thông báo cuộc thi (thông báo vào chung kết, nhắc deadline, cảnh báo chưa nộp bài và thông báo phân công mentor) qua prompt engineering đặc thù theo ngữ cảnh; (2) **Bộ sinh Câu hỏi từ Bài đánh giá** — module AI mới tổng hợp câu hỏi phỏng vấn có mục tiêu từ bài đánh giá dự án của giám khảo; và (3) **Timeline AI Agent** tự động thực thi các mốc cuộc thi mà không cần can thiệp thủ công.

Chúng tôi đánh giá chất lượng email và câu hỏi phỏng vấn do AI tạo thông qua nghiên cứu đánh giá mù chuyên gia, so sánh đầu ra AI với đầu ra viết tay, đồng thời đo hiệu quả thời gian cho quản trị viên và giám khảo. Kết quả cho thấy [TBD — dự kiến: nội dung AI đạt ≥ 3,5/5 theo đánh giá chuyên gia với tiết kiệm thời gian đáng kể]. Các phát hiện chứng minh rằng tích hợp LLM có thể giảm đáng kể gánh nặng quản trị và hỗ trợ chuẩn bị nhất quán, chất lượng cao cho giám khảo trong bối cảnh cuộc thi học thuật.

---

## Ghi chú Chỉnh sửa

- Thay [TBD] bằng số liệu kết quả thực tế sau khi hoàn thành thực nghiệm
- Nén xuống 150–250 từ cho bản nộp cuối
- Xác nhận yêu cầu từ khóa của hội thảo mục tiêu
