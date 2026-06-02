# Paper 09 Summary

## Citation

- **Tên bài:** How to Build an Adaptive AI Tutor for Any Course: Using Knowledge Graph-Enhanced Retrieval-Augmented Generation (KG-RAG).
- **Tác giả:** Chenxi Dong, Yimin Yuan, Kan Chen, Shupei Cheng, Chujie Wen.
- **Năm:** 2024 (Dựa trên việc sử dụng các mô hình mới như DeepSeek-V3 và Qwen2.5).
- **Nguồn:** The Education University of Hong Kong, The University of Adelaide, Chongqing University of Posts and Telecommunications, Wuhan University of Technology.
- **DOI/Link:** https://arxiv.org/abs/2311.17696

## Problem

**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết hai thách thức lớn khi tích hợp các Mô hình Ngôn ngữ Lớn (LLMs) vào Hệ thống Gia sư Thông minh (Intelligent Tutoring Systems - ITS): (1) **Ảo giác thông tin (Information Hallucination)** và (2) **Tính mạch lạc về mặt khái niệm (Conceptual coherence)**. Trong khi phương pháp RAG truyền thống có thể giải quyết vấn đề ảo giác bằng cách truy xuất văn bản, nó lại chỉ dựa vào "độ tương đồng ngữ nghĩa" (semantic similarity). Điều này khiến RAG thường lấy ra các đoạn văn bản (chunks) rời rạc, làm mất đi các mối liên hệ cấu trúc, nguyên nhân - kết quả giữa các khái niệm quan trọng trong môi trường giáo dục.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Bài báo đề xuất khung hệ thống **KG-RAG (Knowledge Graph-enhanced Retrieval-Augmented Generation)**. Kiến trúc này tích hợp:

1.  **Large Language Model (LLM):** Sử dụng DeepSeek-V3 vì khả năng suy luận xuất sắc và chi phí vận hành cực rẻ (chỉ bằng 7% so với GPT-4).
2.  **Đồ thị tri thức (Knowledge Graph - KG):** Tự động trích xuất các bộ ba (triples) thực thể và mối quan hệ từ tài liệu học tập thông qua LLM, sau đó được chuyên gia kiểm duyệt.
3.  **Truy xuất dựa trên tri thức (Knowledge-Guided Retrieval - KGR):** Khi sinh viên đặt câu hỏi, hệ thống không chỉ dùng vector để tìm văn bản tương đồng, mà còn duyệt qua đồ thị tri thức (traversing the knowledge graph) để lấy thêm các khái niệm liên quan, giúp mở rộng ngữ cảnh (expanded context) một cách có cấu trúc trước khi đưa cho LLM sinh câu trả lời.

## Dataset

**Bài báo dùng dữ liệu gì?**

- **Dữ liệu xây dựng hệ thống:** Tài liệu từ khóa học Lý thuyết Tài chính (Finance Theory I) của MIT OpenCourseWare.
- **Dữ liệu đánh giá:** Thử nghiệm đối chứng trên **76 sinh viên đại học** năm nhất chưa có kiến thức nền tảng về tài chính.

## Evaluation

**Bài báo đánh giá bằng metric nào?**

- **Định tính (Qualitative):** Phân tích sự cải thiện trong câu trả lời về Tính đầy đủ (Completeness), Độ chính xác (Precision), và Khả năng bảo toàn mối quan hệ (Relationship Preservation).
- **Phản hồi của sinh viên (Student Feedback):** Sử dụng thang đo Likert 5 điểm để đánh giá các tiêu chí: Độ liên quan (Relevance), Chi tiết (Detail), Sự cải thiện hiểu biết (Understanding), Tính dễ sử dụng (Ease of use), và So sánh với gia sư con người.
- **Định lượng (Quantitative):** So sánh điểm bài kiểm tra trắc nghiệm (thang điểm 10) giữa nhóm dùng RAG chuẩn (Control Group) và nhóm dùng KG-RAG (Experimental Group).

## Results

**Kết quả chính là gì?**

- **Điểm số học tập tăng vọt:** Nhóm sử dụng hệ thống KG-RAG đạt điểm kiểm tra cao hơn đáng kể (Trung bình 6.37 điểm) so với nhóm dùng RAG truyền thống (4.71 điểm) – tương đương mức tăng 35% hiệu suất học tập.
- **Trải nghiệm người dùng vượt trội:** 84% sinh viên đồng ý rằng câu trả lời của hệ thống rất sát với ngữ cảnh, và phần lớn đánh giá AI Tutor này tốt hơn cả gia sư con người.
- **Tính khả thi kinh tế:** Việc sử dụng DeepSeek-V3 thay cho mô hình của OpenAI giúp giảm mạnh rào cản chi phí cho các tổ chức giáo dục, đồng thời giải quyết vấn đề giới hạn quyền truy cập theo khu vực (Global Accessibility).

## Limitations

**Hạn chế của bài báo là gì?**

- Quy mô thử nghiệm còn nhỏ (chỉ 76 sinh viên) và mới chỉ áp dụng giới hạn trong một môn học (Tài chính), cần mở rộng ra nhiều ngành học để chứng minh tính khái quát.
- Chưa sử dụng các số đo tự động hóa (quantitative text quality metrics) để đánh giá chất lượng văn bản như BLEU hay ROUGE.
- Khâu xây dựng Đồ thị tri thức (KG Construction) vẫn đòi hỏi sự can thiệp và thẩm định thủ công của chuyên gia (lecturer validation), chưa thể tự động hóa 100%.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này thuộc nhóm **Bài báo liên quan trực tiếp (Ứng dụng AI vào hệ thống)** và là minh chứng hoàn hảo cho giá trị thực tiễn của dự án **AI Study Hub**.
Giống như ứng dụng AI Tutor trong bài báo, AI Study Hub của nhóm hỗ trợ sinh viên học tập bằng cách tạo ra các luồng hỏi đáp trên chính tài liệu (slide, bài tập) của họ. Bài báo chỉ ra một "điểm mù" mà luồng `Basic RAG` của AI Study Hub có thể đang gặp phải: nếu sinh viên hỏi một câu hỏi tổng hợp đòi hỏi sự liên kết giữa chương 1 và chương 3, bộ truy xuất vector (Pinecone) hiện tại có thể chỉ lấy ngẫu nhiên các đoạn văn bản (chunks) có từ khóa giống nhất mà không kết nối được tính logic của hệ thống kiến thức. Điều này tạo nền tảng lý luận vững chắc để nhóm thiết kế các chế độ như `Corrective RAG` nhằm tối ưu ngữ cảnh.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**
Dựa trên các kỹ thuật của bài báo và cấu trúc kỹ thuật hiện tại của `AI Study Hub`, nhóm có thể ứng dụng trực tiếp các tính năng sau:

1.  **Cơ chế Tái sử dụng lịch sử Chat (Semantic Cache để tiết kiệm chi phí):** AI Study Hub đang gọi API Groq cho mọi câu hỏi. Bài báo đề xuất mô hình "Chat history re-usage" (Hình 6) cực kỳ hiệu quả. Vì AI Study Hub đã lưu trữ `Chat History` trong MongoDB, nhóm có thể viết thêm một `Middleware/Service` nhỏ: Trước khi nhúng (embed) câu hỏi mới và tìm kiếm trên Pinecone, hệ thống sẽ dùng `Jina Embeddings` để so sánh vector của câu hỏi mới với các câu hỏi cũ trong lịch sử. Nếu độ tương đồng > 0.85, backend sẽ trả về luôn câu trả lời cũ. Điều này giúp giảm tải đáng kể số lần gọi Groq SDK và giảm _response time_ (thời gian phản hồi).
2.  **Mở rộng "Knowledge-Guided" bằng Metadata:** Thay vì xây dựng hẳn một Đồ thị tri thức phức tạp, quá trình tải file (Upload and Indexing Flow) của AI Study Hub có thể được cải tiến. Nhóm có thể yêu cầu Groq LLM tự động trích xuất "Danh sách từ khóa cốt lõi" (Key entities) của file tài liệu và lưu vào Pinecone Metadata. Khi sinh viên hỏi, hệ thống truy xuất cả chunk văn bản lẫn các chunk chứa từ khóa liên quan, mô phỏng lại cách KG-RAG mở rộng ngữ cảnh học tập.
3.  **Tích hợp DeepSeek hoặc các LLM chi phí thấp:** Hiện tại dự án đang cấu hình Groq SDK làm "generation engine". Như bài báo đã phân tích về "Economic Feasibility", chi phí vận hành RAG trong giáo dục là rào cản lớn. Nhóm có thể đưa ra đề xuất trong báo cáo về việc hỗ trợ API của DeepSeek (hoặc thay đổi model trên Groq) như một chiến lược tối ưu chi phí (cost efficiency) nếu AI Study Hub muốn triển khai quy mô lớn thực tế.
