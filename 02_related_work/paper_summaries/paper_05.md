# Tóm tắt Bài báo 05

## Trích dẫn

Tên bài: AI-Augmented Advising
Tác giả: TBD
Năm: 2025
Nguồn: Journal of Learning Analytics, Vol. 12
DOI/Link: TBD

## Vấn đề

Tư vấn học tập ở quy mô lớn tiêu tốn nhiều nguồn lực. Các trường đại học thiếu cố vấn để cung cấp hướng dẫn kịp thời, cá nhân hóa cho toàn bộ sinh viên. Câu hỏi đặt ra là liệu LLM (cụ thể GPT-4) có thể tạo ra phản hồi tư vấn tương đương chất lượng cố vấn con người có đào tạo hay không và trong điều kiện nào.

## Phương pháp

Nghiên cứu so sánh phản hồi tư vấn do GPT-4 tạo với phản hồi của cố vấn học tập con người cho cùng một tập yêu cầu tư vấn:

- 50 yêu cầu tư vấn thực tế đã ẩn danh trên 5 danh mục (chọn môn, yêu cầu tốt nghiệp, tình trạng học tập, giải thích quy định, lập kế hoạch nghề nghiệp)
- GPT-4 với tài liệu quy định được chèn vào ngữ cảnh (không dùng RAG, chỉ dùng prompt)
- 5 người đánh giá chuyên gia (cố vấn học tập) đánh giá cả phản hồi AI và con người một cách mù quáng
- Thang đánh giá Likert 5 điểm trên: độ chính xác, tính đầy đủ, giọng điệu, tính hữu ích và chất lượng tổng thể

## Dữ liệu

50 yêu cầu tư vấn sinh viên thực tế đã ẩn danh từ văn phòng hỗ trợ học tập của trường đại học. Phản hồi cố vấn con người được thu thập song song. Phản hồi GPT-4 được tạo từ cùng yêu cầu đó.

## Đánh giá

- Đánh giá chuyên gia mù (1–5) trên 5 chiều
- Độ tin cậy giữa người đánh giá (Cohen's kappa)
- Phân tích theo danh mục yêu cầu
- Phân tích lỗi: các loại sai lầm trong phản hồi AI

## Kết quả

- GPT-4 đạt 3,9/5 so với con người 4,3/5 về chất lượng tổng thể
- GPT-4 đạt điểm cao hơn về giọng điệu (3,8 vs. 3,6) — nhất quán chính thức và lịch sự hơn
- GPT-4 thấp hơn về độ chính xác với câu hỏi quy định cụ thể (3,4 vs. 4,5)
- Với lập kế hoạch nghề nghiệp (dạng mở, dựa trên ý kiến), khoảng cách chất lượng không đáng kể (3,9 vs. 4,0)
- Kappa giữa người đánh giá: 0,71 (nhất quán đáng kể)

## Hạn chế

- GPT-4 được dùng không có RAG; hiệu suất có thể thấp hơn hệ thống có RAG tăng cường
- Chỉ 50 yêu cầu tư vấn; mẫu nhỏ
- Đánh giá bởi cố vấn học tập có thể có thiên kiến nghiêng về phong cách viết của con người
- Nghiên cứu không triển khai hệ thống sản xuất đầy đủ

## Liên quan đến đề tài

Bài báo cung cấp phương pháp đánh giá thực nghiệm mạnh mẽ nhất để so sánh văn bản thể chế do AI tạo với của con người. Thiết kế đánh giá mù chuyên gia (cùng kịch bản, cả hai phiên bản AI và con người được đánh giá không có nhãn) chính xác là thiết kế đánh giá mà chúng tôi dự định dùng cho email cuộc thi. Phát hiện rằng AI cho điểm tương đương về giọng điệu (thậm chí cao hơn) trong khi thua về độ chính xác thực tế cho truy vấn quy định cụ thể cho thấy quyết định đúng của chúng tôi khi thêm bước xem xét thủ công cho thông báo quan trọng.

## Cải tiến Đề xuất

- Áp dụng khung đánh giá này cho email thông báo cuộc thi (không phải phản hồi tư vấn)
- Tích hợp RAG để chèn ngữ cảnh đặc thù cuộc thi và giảm lỗi thực tế
- Đo độ nhất quán giữa người đánh giá đặc thù cho các chiều chất lượng email cuộc thi (liên quan, giọng điệu, đầy đủ, chuyên nghiệp)
