# Tóm tắt Bài báo 04

## Trích dẫn

Tên bài: AI-Powered Academic Advising Using Large Language Models
Tác giả: TBD
Năm: 2024
Nguồn: International Conference on Artificial Intelligence in Education (AIED 2024)
DOI/Link: TBD

## Vấn đề

Cố vấn học tập tốn nhiều thời gian để trả lời câu hỏi thường gặp của sinh viên về chọn môn, yêu cầu tốt nghiệp và quy định học vụ. Điều này thu hẹp thời gian dành cho tư vấn chuyên sâu có giá trị cao hơn. Mở rộng tư vấn cá nhân hóa cho hàng nghìn sinh viên là thách thức nếu không có hỗ trợ AI.

## Phương pháp

Hệ thống tích hợp:

- LLM (GPT-4) làm engine sinh chính
- RAG để truy xuất tài liệu quy định và hồ sơ học tập sinh viên
- Kỹ thuật prompt engineering nhận thức ngữ cảnh để duy trì lịch sử hội thoại
- Lớp kiểm tra thực tế để phát hiện và đánh dấu nội dung có thể là hallucination

## Dữ liệu

Hồ sơ học tập sinh viên (đã ẩn danh), tài liệu quy định trường đại học (sổ tay chương trình đào tạo, yêu cầu tốt nghiệp), bản ghi buổi tư vấn (làm baseline so sánh).

## Đánh giá

- Điểm chuyên gia: 3 cố vấn học tập đánh giá phản hồi AI về độ chính xác, liên quan và phù hợp (thang Likert 1–5)
- So sánh mù: cố vấn đánh giá phản hồi AI và con người mà không biết cái nào là AI
- Khảo sát mức độ hài lòng sinh viên
- Đo lường hiệu quả thời gian

## Kết quả

- Phản hồi AI được đánh giá 3,8/5 so với cố vấn con người 4,2/5 về chất lượng tổng thể
- Với câu hỏi thông thường, phản hồi AI được ưa thích hơn về tốc độ (2 giây vs. 15 phút qua email)
- 67% sinh viên thấy tư vấn AI "hữu ích" hoặc "rất hữu ích"
- Người đánh giá chỉ xác định đúng phản hồi AI trong 58% trường hợp (gần mức ngẫu nhiên), cho thấy chất lượng gần như con người với câu hỏi thông thường

## Hạn chế

- Rủi ro đưa ra tư vấn sai cho các trường hợp ngoại lệ không có trong tài liệu truy xuất
- Không xử lý được các tình huống tư vấn nhạy cảm về cảm xúc
- Sinh viên lo ngại về quyền riêng tư dữ liệu và sự tin tưởng vào tổ chức
- Chất lượng giảm đối với các kịch bản tư vấn đa bước phức tạp

## Liên quan đến đề tài

Bài báo chứng minh LLM có thể sinh văn bản thể chế phù hợp ngữ cảnh, chất lượng tương đương nội dung con người viết cho các tác vụ truyền thông thông thường. Thiết kế đánh giá so sánh mù (chuyên gia đánh giá AI và con người mà không biết nhãn) áp dụng trực tiếp để đánh giá email cuộc thi do LLM tạo ra. Thảo luận về rủi ro hallucination và prompt engineering rất liên quan đến thiết kế pipeline sinh email.

## Cải tiến Đề xuất

- Áp dụng pipeline LLM tương tự cho thông báo cuộc thi (thông báo vào chung kết, nhắc deadline, cảnh báo chưa nộp, phân công mentor)
- Sử dụng prompt có cấu trúc đặc thù cho từng vai trò với mỗi loại email cuộc thi
- Đánh giá email cuộc thi do AI tạo so với mẫu email viết tay bằng cùng phương pháp đánh giá mù
- Thêm bước xem xét của con người cho thông báo quan trọng (ví dụ: thông báo vào chung kết)
