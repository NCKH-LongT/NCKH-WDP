# Paper 01 Summary

## Citation

Tên bài: EduChat: A Large-Scale Language Model-based Chatbot System for Intelligent Education
Tác giả: Yuhao Dan và các cộng sự
Năm: 2023
Nguồn: arXiv
DOI/Link: https://arxiv.org/abs/2308.02773

## Problem

Bài báo tập trung giải quyết vấn đề xây dựng một chatbot giáo dục thông minh dựa trên Large Language Model (LLM). Các hệ thống chatbot thông thường trong giáo dục còn hạn chế ở:

- Khả năng cá nhân hóa cho từng học sinh.
- Thiếu hiểu biết chuyên sâu về lĩnh vực giáo dục.
- Khó hỗ trợ các tác vụ như: hỏi đáp học thuật, chấm bài luận, dạy học kiểu Socratic, hỗ trợ cảm xúc/tâm lý cho học sinh.

EduChat được đề xuất nhằm tạo ra một hệ thống AI giáo dục toàn diện hơn cho học sinh, giáo viên và phụ huynh.

## Method

Bài báo xây dựng hệ thống EduChat, một chatbot dựa trên LLM với các thành phần chính:

- **Domain-specific pretraining**: Tiền huấn luyện trên dữ liệu giáo dục để mô hình hiểu ngữ cảnh học tập tốt hơn.
- **Instruction tuning**: Fine-tune bằng các instruction/prompt dành riêng cho giáo dục.
- **System prompts**: Thiết kế prompt theo lý thuyết giáo dục và tâm lý học để cải thiện hỏi đáp, hỗ trợ học tập, tương tác cảm xúc.
- **Tool usage**: Kết hợp khả năng sử dụng công cụ để hỗ trợ nhiều tác vụ giáo dục khác nhau.

Hệ thống hướng đến việc tạo trải nghiệm học tập thông minh và cá nhân hóa hơn.

## Dataset

Bài báo sử dụng:

- Educational corpus (dữ liệu giáo dục chuyên ngành).
- Instruction datasets cho chatbot giáo dục.
- Dữ liệu hội thoại và tác vụ học tập, bao gồm: hỏi đáp học thuật, bài luận, đối thoại giáo dục, hỗ trợ tâm lý/học tập.

Lưu ý: bài báo không công bố đầy đủ chi tiết toàn bộ dataset trong phần abstract.

## Evaluation

Bài báo đánh giá hệ thống qua:

- Chất lượng trả lời câu hỏi.
- Khả năng hỗ trợ học tập và chấm bài.
- Hiệu quả hội thoại giáo dục.
- Đánh giá định tính (qualitative evaluation): độ hữu ích, tính tự nhiên, khả năng tương tác với người học.

## Results

EduChat đạt được các kết quả chính:

- Có khả năng xử lý tốt các tác vụ giáo dục đa dạng.
- Cải thiện chất lượng hỏi đáp học thuật.
- Hỗ trợ dạy học theo kiểu Socratic khá hiệu quả.
- Có thể hỗ trợ cảm xúc và tư vấn học tập cơ bản.
- Hoạt động như một trợ lý học tập cá nhân hóa.

Nhóm tác giả cũng public code, model và demo online để thúc đẩy nghiên cứu AI trong giáo dục.

## Limitations

- Chưa đánh giá sâu trên môi trường giáo dục thực tế quy mô lớn.
- Vẫn có nguy cơ hallucination của LLM.
- Chưa đảm bảo hoàn toàn tính chính xác học thuật.
- Việc cá nhân hóa người học còn phụ thuộc dữ liệu huấn luyện.
- Tốn tài nguyên tính toán khi triển khai mô hình lớn.

## Relevance to our topic

Bài báo liên quan mạnh đến đề tài nhóm vì hệ thống của nhóm cũng xây dựng chatbot / trợ lý AI hỗ trợ học sinh/sinh viên, bao gồm:

- Chatbot hỗ trợ học tập cá nhân hóa.
- AI trả lời câu hỏi học thuật.
- Ứng dụng LLM trong môi trường giáo dục.
- Hỗ trợ cảm xúc hoặc mentoring người học.

EduChat cung cấp nền tảng kiến trúc và phương pháp (pretraining + instruction tuning + system prompts + tool usage) để nhóm tham khảo khi thiết kế hệ thống.

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng so với EduChat:

- **RAG (Retrieval-Augmented Generation)**: Giúp chatbot trả lời chính xác hơn bằng cách tra cứu dữ liệu thật, giảm hallucination.
- **Hồ sơ người học (Learner Profile)**: Theo dõi tiến độ và cá nhân hóa mạnh hơn theo từng học sinh.
- **Voice + Speech**: Hỗ trợ tương tác bằng giọng nói trực tiếp.
- **Emotion Detection**: Phân tích cảm xúc người học để phản hồi phù hợp hơn.
- **Fine-tune cho tiếng Việt**: Tối ưu riêng cho môi trường giáo dục Việt Nam.
- **Tích hợp LMS**: Kết nối Moodle, Canvas hoặc hệ thống quản lý học tập của trường.
- **Giảm hallucination**: Kết hợp knowledge base hoặc fact-checking module.
