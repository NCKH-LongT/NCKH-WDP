# Paper 10 Summary

## Citation

- **Tên bài:** Retrieval-Augmented Generation (RAG) Chatbots for Education: A Survey of Applications.
- **Tác giả:** Jakub Swacha và Michał Gracel.
- **Năm:** 2025.
- **Nguồn:** Tạp chí Applied Sciences (MDPI).
- **DOI/Link:** https://doi.org/10.3390/app15084234.

## Problem

**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết rào cản lớn nhất khi ứng dụng các mô hình ngôn ngữ lớn (LLMs) vào môi trường giáo dục: **hiện tượng ảo giác (hallucinations)**. Mặc dù phương pháp RAG đã được chứng minh là một giải pháp hiệu quả để khắc phục điểm yếu này, nhưng hiện tại vẫn chưa có một nghiên cứu tổng quan nào đánh giá tiến độ và thực trạng ứng dụng RAG trong lĩnh vực giáo dục. Bài báo lấp đầy khoảng trống này bằng cách tổng hợp và phân loại các chatbot RAG giáo dục theo mục đích, phạm vi chủ đề, mô hình LLM và phương pháp đánh giá.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Bài báo sử dụng phương pháp **Nghiên cứu khảo sát (Survey / Systematic Review)**. Nhóm tác giả thu thập tài liệu kết hợp phương pháp tìm kiếm chuỗi (string search) và phương pháp vết dầu loang (snowballing) để lọc ra các nghiên cứu liên quan đến chatbot RAG trong giáo dục, sau đó phân loại các hệ thống này thành các nhóm mục tiêu hỗ trợ khác nhau (như học tập, truy cập tri thức nguồn, hỗ trợ quản lý tổ chức...).

## Dataset

**Bài báo dùng dữ liệu gì?**
Tập dữ liệu của nghiên cứu là **47 bài báo khoa học, preprint và luận văn** xuất bản từ năm 2022 đến đầu năm 2025. Các tài liệu này được thu thập từ 3 cơ sở dữ liệu thư mục lớn: Scopus, Web of Science và Google Scholar.

## Evaluation

**Bài báo đánh giá bằng metric nào?**
Do đây là bài khảo sát, tác giả tổng hợp lại toàn bộ các metric mà 47 nghiên cứu trước đó đã sử dụng, bao gồm:

- Đánh giá truy xuất: Accuracy, Precision, Recall, F1 Score.
- Chất lượng ngôn ngữ sinh ra: Coherence, Fluency, Relevance.
- Đánh giá của hệ thống RAGAS: **Faithfulness (Độ trung thực), Answer Relevance (Độ liên quan của câu trả lời) và Context Relevance (Độ liên quan ngữ cảnh)**.
- Đánh giá phần mềm: User Acceptance (Sự chấp nhận của người dùng), Response time (Thời gian phản hồi).

## Results

**Kết quả chính là gì?**

- Phần lớn chatbot RAG được phát triển để **truy cập nguồn tri thức (access to source knowledge)** và **hỗ trợ học tập (learning)**.
- **OpenAI GPT** là kiến trúc lõi thống trị trong số các mô hình LLM được sử dụng (chiếm 36/47 hệ thống), bỏ xa mô hình đứng thứ hai là LLaMA (15 hệ thống).
- Phát hiện quan trọng nhất là **chưa có một nghiên cứu nào** đo lường tác động thực tế của chatbot RAG đối với chính mục tiêu mà nó được tạo ra (ví dụ: chưa đo lường xem điểm số hay kết quả học tập của học sinh có thực sự tăng lên nhờ chatbot hay không).

## Limitations

**Hạn chế của bài báo là gì?**

- Chỉ tìm kiếm tài liệu từ 3 nền tảng (Scopus, Web of Science, Google Scholar) và bỏ qua các nghiên cứu không xuất bản bằng tiếng Anh, có thể dẫn đến việc bỏ sót các hệ thống RAG được phát triển cục bộ cho các ngôn ngữ khác.
- Bài báo chịu ảnh hưởng của "publication bias" (thiên kiến công bố), vì các tác giả thường ngại công bố các dự án ứng dụng RAG thất bại.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo khảo sát này thuộc nhóm **Domain ứng dụng** và liên kết mật thiết với bối cảnh dự án **AI Study Hub** trong file `REPORT.md`:

1.  **Xác nhận mức độ phổ biến của hệ thống:** Báo cáo `REPORT.md` của nhóm mô tả AI Study Hub cung cấp "Document Library" nơi sinh viên tải tài liệu cá nhân lên để hỏi đáp. Bài báo khảo sát này chỉ ra rằng nhóm tính năng _cung cấp quyền truy cập vào kiến thức nguồn (access to source knowledge)_ là ứng dụng phổ biến và cốt lõi nhất của RAG trong giáo dục (với 20 bài nghiên cứu). Điều này chứng minh hướng đi của nhóm là rất chuẩn xác so với thực tiễn.
2.  **Củng cố tính năng Benchmarking:** Module _RAG Evaluation and Benchmarking_ của AI Study Hub đang đo lường các chỉ số như _correctness, faithfulness, relevance, completeness_. Bài báo khảo sát làm nổi bật lên rằng việc đánh giá tổng hợp các mặt (từ khả năng truy xuất đến chất lượng sinh văn bản) là khâu cực kỳ quan trọng đối với RAG chatbot, đồng thời cũng chỉ ra sự thiếu hụt trầm trọng trong việc đánh giá hiệu quả RAG. Vì vậy, việc dự án của nhóm có sẵn mô-đun đánh giá sẽ là một điểm sáng lớn về mặt kiến trúc.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**
Dựa trên kiến trúc hiện hành của AI Study Hub và đề xuất từ nhóm tác giả bài báo, nhóm có thể bổ sung các hướng sau:

1.  **Bổ sung đánh giá tác động học tập (Learning Outcomes Evaluation):** Theo bài báo, hiện thiếu hụt các đánh giá đo lường tác động thực sự. Trên trang `Admin Dashboard` của hệ thống, thay vì chỉ đo độ chính xác của RAG mode (Correctness, Faithfulness), nhóm có thể làm thêm một bước đối chiếu (A/B testing): so sánh điểm số, hoặc thời gian hoàn thành bài tập của nhóm sinh viên dùng AI Study Hub so với nhóm không dùng.
2.  **Mở rộng bộ dữ liệu sang "Institutional Knowledge" (Tri thức nội bộ nhà trường):** Trong danh mục phân loại lĩnh vực (Thematic Scope), bài báo đề cập "Institutional-domain knowledge" (hỗ trợ giải đáp quy chế nội bộ, tài nguyên sinh viên) chiếm tỉ trọng rất lớn. Hiện AI Study Hub đang chỉ tập trung vào tài liệu do người dùng tự tải (slide, bài tập). Nhóm có thể crawl thêm quy chế đào tạo, sổ tay sinh viên của trường tích hợp thẳng vào Pinecone vector database để chatbot giải đáp song song chuyện học thuật lẫn quy trình.
3.  **Tích hợp chuẩn RAGAS vào Evaluation Routes:** Báo cáo hiện tại ghi nhận nhóm tự định nghĩa các score đánh giá cho các API `Evaluation routes`. Nhóm có thể chuẩn hóa bộ metric này bằng cách điều chỉnh prompt đánh giá của Groq SDK dựa theo quy tắc RAGAS (bao gồm Faithfulness, Answer Relevance và Context Relevance) – một chuẩn quốc tế đang rất được ủng hộ trong các bài luận được bài báo liệt kê.
