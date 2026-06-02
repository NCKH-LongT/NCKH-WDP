# Kết luận và Hướng Nghiên cứu Tương lai (Bản nháp)

## Kết luận

Bài báo này giới thiệu ACMS-AI, Hệ thống Quản lý Cuộc thi Học thuật Tích hợp AI, tích hợp các khả năng của mô hình ngôn ngữ lớn vào nền tảng đầy đủ cho quản lý các cuộc thi học thuật tại các trường đại học. Hệ thống giải quyết ba kém hiệu quả vận hành chính thông qua ba module AI:

**1. Bộ sinh Email LLM**: Tự động soạn bốn loại thông báo mốc cuộc thi (thông báo vào chung kết, nhắc deadline, cảnh báo chưa nộp bài, phân công mentor), thay thế soạn email thủ công bằng sinh LLM phù hợp ngữ cảnh. Kết quả đánh giá cho thấy [TBD — thay bằng số liệu kết quả thực tế].

**2. Bộ sinh Câu hỏi từ Bài đánh giá**: Tổng hợp 5–7 câu hỏi phỏng vấn có mục tiêu từ bài đánh giá dự án dạng văn bản tự do của giám khảo, cung cấp cho giám khảo tài liệu chuẩn bị được điều chỉnh trong vài giây thay vì hơn 20 phút chuẩn bị thủ công. Đây là, theo hiểu biết của chúng tôi, ứng dụng đầu tiên của sinh câu hỏi dựa trên LLM cho tác vụ tổng hợp câu hỏi-từ-bài-review trong bối cảnh cuộc thi học thuật.

**3. Timeline AI Agent**: Thực thi các mốc cuộc thi chính xác thông qua scheduling tự động, loại bỏ lỗi giám sát thủ công và cung cấp thực thi deadline đáng tin cậy theo quy mô.

Đánh giá thực nghiệm chứng minh nội dung thông báo và câu hỏi phỏng vấn do AI tạo [TBD — chất lượng tương đương/vượt trội/chấp nhận được so với đầu ra viết tay], với [TBD — X%] tiết kiệm thời gian qua các tác vụ admin và giám khảo. Hệ thống đạt điểm SUS là [TBD], cho thấy khả năng sử dụng [TBD — trung bình/trên trung bình/xuất sắc] trên cả ba vai trò người dùng.

Công trình này thiết lập rằng các LLM hiện có, khi tích hợp với ngữ cảnh đặc thù theo lĩnh vực và prompt engineering được thiết kế tốt, có thể mang lại giá trị thực tiễn trong quản lý cuộc thi học thuật mà không đòi hỏi huấn luyện model tùy chỉnh.

## Hướng Nghiên cứu Tương lai

Các hướng sau được xác định cho nghiên cứu và phát triển hệ thống trong tương lai:

1. **Tích hợp RAG**: Kết hợp vector database của email cuộc thi cũ, rubric và mô tả dự án để cung cấp ngữ cảnh phong phú hơn cho sinh LLM và giảm rủi ro hallucination.

2. **Hỗ trợ Đa ngôn ngữ**: Mở rộng sinh email và câu hỏi sang chuyển đổi mã Việt-Anh, phổ biến trong giao tiếp học thuật tại Đại học FPT.

3. **Vòng lặp Phản hồi**: Cho phép giám khảo đánh giá câu hỏi AI ("hữu ích" / "không hữu ích") để xây dựng dataset phản hồi cho tinh chỉnh prompt hoặc fine-tuning.

4. **Mở rộng sang Bảo vệ Luận văn**: Áp dụng module sinh câu hỏi từ bài đánh giá cho chuẩn bị buổi bảo vệ luận văn và dự án capstone, mở rộng trường hợp sử dụng ra ngoài quản lý cuộc thi.

5. **Đánh giá Dài hạn**: Đánh giá ACMS-AI qua nhiều chu kỳ cuộc thi để đánh giá tính nhất quán chất lượng nội dung AI theo thời gian và trên các chủ đề cuộc thi khác nhau.

6. **AI Xử lý Khiếu nại**: Mở rộng module khiếu nại cơ bản hiện tại với phân loại hỗ trợ AI và sinh phản hồi để giảm thêm gánh nặng quản trị.

7. **Phát hành Mã nguồn Mở**: Phát hành nền tảng ACMS-AI (với dữ liệu đánh giá đã ẩn danh) để cộng đồng nghiên cứu và các trường đại học khác áp dụng và nghiên cứu thêm.
