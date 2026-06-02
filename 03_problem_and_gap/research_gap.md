# Research Gap and Contributions (Khoảng trống nghiên cứu và Đóng góp của đề tài)

**Các bài trước đã giải quyết như thế nào?**
Các nghiên cứu trước đây chủ yếu sử dụng kiến trúc **Retrieval-Augmented Generation (RAG)**, kết hợp LLM với cơ sở dữ liệu vector bên ngoài để truy xuất ngữ cảnh trước khi sinh câu trả lời,. Để nâng cao hiệu quả, nhiều kỹ thuật phức tạp đã được đề xuất:

- **SELF-RAG:** Huấn luyện LLM tự phản ngẫm (self-reflection) thông qua các token đặc biệt để quyết định khi nào cần truy xuất và đánh giá chất lượng câu trả lời,.
- **CRAG (Corrective RAG):** Sử dụng một bộ đánh giá (evaluator) để chấm điểm tài liệu truy xuất, tự động lọc bỏ thông tin nhiễu hoặc kích hoạt tìm kiếm web bổ sung nếu tài liệu bị sai lệch,.
- **DR-RAG:** Đề xuất truy xuất 2 bước (nối câu hỏi với tài liệu ban đầu) để tìm ra các tài liệu có liên quan động (dynamic-relevant) nằm ẩn sâu trong hệ thống.
- **Tích hợp Code Interpreter:** Kết hợp RAG với môi trường chạy mã Python để giải quyết điểm yếu về tính toán toán học và suy luận logic nhiều bước của LLM,.
- **KG-RAG:** Ứng dụng Đồ thị tri thức (Knowledge Graph) để duy trì tính mạch lạc về mặt khái niệm của tài liệu,.

**Các bài trước còn hạn chế gì?**

- **Nhiễu thông tin:** Các hệ thống RAG cơ bản thường truy xuất một số lượng tài liệu cố định một cách bừa bãi và đưa vào LLM, bất kể tài liệu đó có thực sự liên quan hay không, làm giảm chất lượng câu trả lời,.
- **Lỗ hổng khi kiến thức thay đổi:** Khi đối mặt với sự mâu thuẫn kiến thức (knowledge shifts) giữa tài liệu mới và kiến thức cũ của LLM, hiệu suất của các hệ thống RAG hiện tại bị sụt giảm nghiêm trọng (từ 22% đến 27%) do LLM thường thiên vị kiến thức nội tại của nó,.
- **Chi phí tính toán:** Các phương pháp RAG suy luận đa bước (multi-step) hoặc dùng cây quyết định tiêu tốn quá nhiều tài nguyên tính toán và làm tăng thời gian phản hồi,.
- **Hạn chế tổng hợp:** Các mô hình hiện tại vẫn gặp khó khăn trong việc tổng hợp kiến thức liên môn, xử lý dữ liệu đa phương thức (văn bản kết hợp hình ảnh/biểu đồ) hoặc chưa được đánh giá hiệu quả tác động thực tế tới học sinh,,.

**Nhóm sẽ cải tiến điểm nào?**
Dựa trên kiến trúc của dự án **AI Study Hub**, nhóm sẽ khắc phục các hạn chế trên bằng cách thiết kế luồng xử lý **Corrective RAG** tối ưu và gọn nhẹ hơn so với Basic RAG thông thường. Cụ thể, luồng xử lý này sẽ:

1.  **Tự động viết lại câu hỏi (query rewriting)** để tăng độ chuẩn xác khi tìm kiếm.
2.  **Lọc các đoạn văn bản theo độ liên quan (filters chunks by relevance)** để loại bỏ thông tin rác trước khi đưa vào LLM.
3.  **Thực hiện truy xuất dự phòng (fallback retrieval)** và **kiểm tra độ bám sát tài liệu (grounding checks)** để kiềm chế ảo giác.
    Bên cạnh đó, nhóm nâng cấp khả năng lập chỉ mục (indexing) để hỗ trợ đa dạng định dạng tệp (PDF, DOCX, PPTX, XLSX, TXT) và tối ưu hóa hệ thống đặc thù cho **hỏi đáp giáo dục bằng tiếng Việt**,.

**Đóng góp của nhóm là gì?**
Nhóm xây dựng thành công **AI Study Hub**, một nền tảng ứng dụng web full-stack (React, Node.js, Express, MongoDB) cho phép sinh viên tự do tải tài liệu học tập lên và tương tác với AI trên chính nguồn tài nguyên an toàn đó,.
Đóng góp học thuật và thực tiễn lớn nhất của nhóm là việc phát triển một **hệ thống RAG Evaluation and Benchmarking (Đánh giá và Chấm điểm RAG)** được tích hợp thẳng vào backend. Hệ thống này tự động lưu trữ và đo lường các chỉ số cốt lõi như: độ chính xác (correctness), độ trung thực (faithfulness), độ liên quan (relevance), độ hoàn thiện (completeness) và thời gian phản hồi (response time). Nhờ giao diện Admin Dashboard, dự án không chỉ dừng lại ở một chatbot hộp đen mà trở thành một **hệ thống quản lý học tập có khả năng đo lường, đối chiếu hiệu suất (A/B testing giữa các mode RAG) và kiểm soát hoàn toàn rủi ro ảo giác AI**,.
