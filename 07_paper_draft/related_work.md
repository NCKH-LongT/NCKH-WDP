# Tổng quan Tài liệu (Bản nháp)

## 2.1 Hệ thống Quản lý Tích hợp AI

Một số nghiên cứu đã đề xuất các nền tảng quản lý tích hợp AI. Smart Event Management System Using Machine Learning [TRÍCH DẪN] chứng minh ML có thể tối ưu hóa lịch sự kiện và phân tích hành vi người tham gia, giảm 40% thời gian lập kế hoạch so với quy trình thủ công. Aduvia [TRÍCH DẪN] tích hợp nhiều thành phần AI (chatbot LLM, sinh quiz, gợi ý cá nhân hóa) vào Hệ thống Quản lý Học tập, thiết lập kiến trúc khả thi cho nền tảng quản lý đặc thù theo lĩnh vực tích hợp nhiều module AI. Kết quả SUS của Aduvia đạt 71 xác nhận rằng tích hợp AI đa module trong hệ thống quản lý được người dùng chấp nhận.

## 2.2 LLM cho Sinh Văn bản Thể chế

Việc sử dụng LLM để sinh văn bản thể chế đã được khám phá chủ yếu trong bối cảnh tư vấn học tập. AI-Powered Academic Advising Using Large Language Models [TRÍCH DẪN] chứng minh hệ thống dựa trên GPT-4 với RAG có thể sinh phản hồi tư vấn được chuyên gia đánh giá 3,8/5, so với 4,2/5 cho phản hồi của con người. AI-Augmented Advising [TRÍCH DẪN] tiến hành so sánh mù có hệ thống giữa GPT-4 và cố vấn học tập con người, phát hiện LLM đạt điểm tương đương về giọng điệu (đôi khi cao hơn) trong khi thua về độ chính xác thực tế cho truy vấn quy định cụ thể. Các nghiên cứu này thiết lập tính khả thi của văn bản thể chế do LLM sinh ra và phương pháp đánh giá — đánh giá mù chuyên gia với các chiều có cấu trúc — mà chúng tôi áp dụng cho đánh giá email cuộc thi.

## 2.3 Hệ thống Sinh Câu hỏi AI

AI-Powered Quiz Generation for Learning Management Systems [TRÍCH DẪN] trình bày triển khai full-stack sinh câu hỏi quiz bằng LLM tích hợp với Canvas LMS. Hệ thống đạt tỷ lệ chấp nhận 72% của giảng viên với giảm 70% thời gian tạo quiz. Tuy nhiên, công trình này tập trung vào câu hỏi trắc nghiệm được sinh từ nội dung khóa học có cấu trúc, không phải câu hỏi phỏng vấn mở được tổng hợp từ bài đánh giá tự do. Nhu cầu nhận thức của loại sau — yêu cầu mô hình xác định chủ đề từ bài review, đánh giá những gì người đánh giá nhận thấy là đáng chú ý và sinh câu hỏi thăm dò — cao hơn đáng kể. Công trình của chúng tôi mở rộng dòng nghiên cứu này sang tác vụ mới và phức tạp hơn là tổng hợp câu hỏi phỏng vấn.

## 2.4 Ghép Expert và Mentor

Research Supervisor Recommendation System Based on Topic Conformity [TRÍCH DẪN] và Research Supervisor Recommendation Using a Hybrid Filtering Approach [TRÍCH DẪN] đề cập đến ghép AI hỗ trợ giữa sinh viên và chuyên gia hướng dẫn sử dụng TF-IDF và phương pháp lọc, đạt precision hơn 80% trong ghép cặp chuyên môn. Các công trình này liên quan đến module phân công mentor-bảng thi của chúng tôi. Hệ thống của chúng tôi đơn giản hóa thành phân công do admin điều khiển với xác thực domain email FPT, nhận ra rằng phân công mentor cuộc thi khác với ghép cặp giám sát dài hạn.

## 2.5 Khoảng trống Nghiên cứu

Mặc dù có nhiều ứng dụng AI trong hệ thống quản lý, sinh văn bản LLM và tổng hợp câu hỏi, nhưng không có công trình nào trước đây giải quyết các thách thức cụ thể về: (1) sinh tự động email thông báo đặc thù cuộc thi trên bốn loại mốc chính bằng LLM; (2) tổng hợp câu hỏi phỏng vấn bằng LLM từ bài đánh giá dự án trong bối cảnh cuộc thi; hoặc (3) nền tảng tích hợp kết hợp các khả năng này với quản lý vòng đời cuộc thi đầy đủ. Công trình của chúng tôi lấp đầy cả ba khoảng trống, với đánh giá thực nghiệm so sánh nội dung AI với đầu ra viết tay.
