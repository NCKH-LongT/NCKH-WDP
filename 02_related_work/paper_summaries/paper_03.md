# Tóm tắt Bài báo 03

## Trích dẫn

Tên bài: AI-Powered Quiz Generation for Learning Management Systems: A Full-Stack Implementation for Canvas LMS
Tác giả: TBD
Năm: 2025
Nguồn: CEUR Workshop Proceedings (Applied AI track)
DOI/Link: TBD

## Vấn đề

Tạo câu hỏi kiểm tra chất lượng cao tốn nhiều thời gian của giảng viên. Việc soạn thủ công câu hỏi quiz cho các khóa học có lượng nội dung lớn đòi hỏi chuyên môn đáng kể và nhiều công sức. Cần có hệ thống sinh câu hỏi tự động được bám sát nội dung thực tế của môn học và duy trì chất lượng giáo dục.

## Phương pháp

Bài báo triển khai một hệ thống full-stack với:

- Phân tích tài liệu khóa học (PDF, slide) từ Canvas LMS qua API
- Sử dụng LLM (Gemini/GPT với RAG) để sinh câu hỏi trắc nghiệm và trả lời ngắn bám sát nội dung được truy xuất
- Bộ lọc chất lượng để loại bỏ câu hỏi kém tin cậy hoặc trùng lặp
- Tích hợp câu hỏi được tạo trực tiếp vào Canvas LMS quiz builder

## Dữ liệu

Tài liệu khóa học (PDF, slide bài giảng) từ Canvas LMS qua nhiều khóa học Kỹ thuật Phần mềm. Đánh giá chuyên gia bởi 4 giảng viên theo rubric có cấu trúc.

## Đánh giá

- Điểm chuyên gia về mức độ liên quan, rõ ràng, phù hợp độ khó và cấp độ Bloom's Taxonomy
- Tỷ lệ chấp nhận của câu hỏi AI bởi giảng viên
- Thời gian tiết kiệm mỗi quiz so với soạn tay
- Độ nhất quán giữa các người đánh giá (Fleiss' kappa)

## Kết quả

- Câu hỏi do AI tạo được giảng viên đánh giá 3,9/5 về mức độ liên quan tổng thể
- Tỷ lệ chấp nhận: 72% (giảng viên chấp nhận câu hỏi mà không cần chỉnh sửa lớn)
- Thời gian tạo: 2–5 giây mỗi câu vs. 5–10 phút thủ công
- Tiết kiệm thời gian: khoảng 70% so với soạn quiz thủ công

## Hạn chế

- Chỉ giới hạn ở định dạng trắc nghiệm và trả lời ngắn; không đề cập đến câu hỏi phỏng vấn dạng mở
- Câu hỏi đôi khi thiếu chiều sâu cho các chủ đề nâng cao hoặc mơ hồ
- Đôi khi xảy ra AI hallucination trong câu hỏi có tính thực tế (đặc biệt chi tiết kỹ thuật)
- Đầu vào là nội dung khóa học có cấu trúc, không phải bài đánh giá dạng văn bản tự do

## Liên quan đến đề tài

Bài báo này liên quan trực tiếp nhất đến module Sinh câu hỏi Phỏng vấn từ Bài đánh giá của chúng tôi. Phương pháp sinh câu hỏi bằng LLM, khung đánh giá chất lượng (điểm chuyên gia, tỷ lệ chấp nhận) và mô hình tích hợp có thể chuyển giao trực tiếp. Công trình của chúng tôi mở rộng khái niệm này theo hai hướng quan trọng: (1) đầu vào là bài đánh giá dạng văn bản tự do chứ không phải tài liệu khóa học có cấu trúc; (2) đầu ra là câu hỏi phỏng vấn dạng mở chứ không phải câu hỏi quiz — tác vụ sinh khó hơn, đòi hỏi lý luận về điểm mạnh/yếu mà người đánh giá đã xác định.

## Cải tiến Đề xuất

- Mở rộng từ câu hỏi quiz sang câu hỏi phỏng vấn dạng mở cho buổi vấn đáp
- Dùng tài liệu bài đánh giá dự án làm đầu vào thay vì tài liệu khóa học có cấu trúc
- Thêm ngữ cảnh rubric để đảm bảo câu hỏi được tạo bám vào tiêu chí đánh giá cụ thể
- Đánh giá chất lượng câu hỏi đặc thù cho bối cảnh vấn đáp bảo vệ dự án cạnh tranh
