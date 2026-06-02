# Paper 08 Summary

## Citation

- **Tên bài:** A novel framework for educational Q&A: Leveraging RAG and Code Interpreters for knowledge retrieval and logical computation.
- **Tác giả:** Jin Lu, Ji Li.
- **Năm:** 2025.
- **Nguồn:** Tạp chí PLoS ONE.
- **DOI/Link:** https://doi.org/10.1371/journal.pone.0337361.

## Problem

**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết những hạn chế của các hệ thống hỏi đáp (Q&A) giáo dục truyền thống và các Mô hình ngôn ngữ lớn (LLMs) hiện tại. Cụ thể, các hệ thống này gặp khó khăn trong việc **cập nhật kiến thức mới, tính chính xác khi suy luận và khả năng xử lý các bài toán tính toán phức tạp**. Mặc dù LLMs có khả năng sinh văn bản tốt, chúng thường mắc lỗi "ảo giác" (hallucination) và thiếu khả năng suy luận logic hay giải toán (multi-step calculations) thực sự.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Bài báo đề xuất một hệ thống kết hợp giữa **Retrieval-Augmented Generation (RAG)** và **LLM Code Interpreter (Trình thông dịch mã LLM)**.

1.  **RAG:** Đảm nhận việc truy xuất động các thông tin mới nhất từ cơ sở dữ liệu bên ngoài để làm ngữ cảnh, giúp giảm thiểu ảo giác của LLMs.
2.  **Code Interpreter:** Khi câu hỏi yêu cầu tính toán hoặc suy luận nhiều bước, LLM sẽ tự động sinh mã Python. Trình thông dịch sau đó sẽ thực thi mã này trong một môi trường hộp cát (sandbox) an toàn, lấy kết quả tính toán chính xác để tổng hợp thành câu trả lời cuối cùng.

## Dataset

**Bài báo dùng dữ liệu gì?**
Hệ thống được đánh giá trên **5 bộ dữ liệu giáo dục** đại diện cho nhiều lĩnh vực và độ khó khác nhau:

1.  **AI2_ARC:** Câu hỏi khoa học K-12.
2.  **OpenBookQA:** Đánh giá khả năng suy luận khoa học nhiều bước.
3.  **E-EVAL:** Bộ dữ liệu giáo dục đa môn học K-12 của Trung Quốc.
4.  **TQA (Textbook Question Answering):** Bộ dữ liệu từ sách giáo khoa khoa học gồm cả văn bản và hình ảnh.
5.  **ScienceQA:** Bộ dữ liệu câu hỏi trắc nghiệm khoa học kết hợp đa phương thức (hình ảnh và văn bản).

## Evaluation

**Bài báo đánh giá bằng metric nào?**
Bài báo sử dụng **Accuracy (Độ chính xác)** làm thước đo chính. Nghiên cứu tiến hành so sánh hệ thống kết hợp (RAG + Code Interpreter) với nhiều LLMs nền tảng khác nhau như GPT-4o, Claude-3.5-Sonnet, Gemini-pro-1.5, Gemma2-9B và Llama-3.5-8B trong nhiều thiết lập (0-shot, 1-shot, 3-shot, Chain-of-Thought).

## Results

**Kết quả chính là gì?**

- Hệ thống kết hợp RAG và Code Interpreter giúp **tăng độ chính xác trung bình từ 10-15%** so với các mô hình LLM thông thường.
- Trong số các mô hình được thử nghiệm, **GPT-4o và Gemini-pro-1.5** thể hiện hiệu suất mạnh mẽ nhất, đặc biệt xuất sắc trong các tác vụ suy luận khoa học và tính toán nhiều bước. Ví dụ: trên bộ dữ liệu AI2_ARC, GPT-4o đạt độ chính xác lên tới 92.1%.
- Hệ thống cung cấp tính minh bạch cao hơn nhờ việc hiển thị toàn bộ quá trình thực thi code và logs cho người dùng.

## Limitations

**Hạn chế của bài báo là gì?**

- **Lỗi hệ thống:** Thi thoảng hệ thống vẫn gặp lỗi truy xuất do dữ liệu chưa kịp cập nhật, hoặc lỗi thực thi code do LLM viết sai cú pháp ngôn ngữ lập trình.
- **Hạn chế đa phương thức (Multi-modal):** Các mô hình hiện tại vẫn gặp khó khăn trong việc kết hợp và hiểu sâu các bài toán có cả văn bản lẫn hình ảnh đan xen.
- **Rủi ro đạo đức & Sư phạm:** Học sinh có nguy cơ ỷ lại vào AI (thinking inertia) khi hệ thống giải bài quá chi tiết, làm giảm khả năng tư duy phản biện. Giảng viên cũng có thể phụ thuộc quá nhiều vào AI mà bỏ qua kinh nghiệm sư phạm cá nhân.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này được xếp vào nhóm **5 bài báo liên quan trực tiếp (Ứng dụng AI vào hệ thống)**.
Nghiên cứu này mô tả một hệ thống Q&A giáo dục cực kỳ sát với mô hình **AI Study Hub** của nhóm bạn. Cả hai dự án đều áp dụng luồng xử lý RAG để giúp sinh viên hỏi đáp trên tài liệu học tập. Tuy nhiên, bài báo chỉ ra một điểm yếu mà AI Study Hub (hiện đang dùng LLM của Groq sinh text) sẽ gặp phải: khi sinh viên tải lên bài tập tính toán (như toán học, tài chính), LLM sẽ dễ sinh ảo giác (tính sai). Giải pháp Code Interpreter của bài báo chính là lời giải hoàn hảo cho vấn đề này.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**
Dựa vào kiến trúc của **AI Study Hub** và đề xuất từ bài báo, nhóm có thể mở rộng các điểm sau:

1.  **Tích hợp Python Sandbox (Code Interpreter) để giải bài tập:** Theo báo cáo, hệ thống của nhóm hỗ trợ tải lên các tệp XLSX và TXT. Nếu sinh viên tải lên một tệp Excel chứa dữ liệu thống kê và yêu cầu tính toán, nhóm có thể xây dựng thêm một service `Code Execution` bằng Python ở backend. Khi `Groq SDK` phát hiện câu hỏi cần tính toán, nó sẽ sinh code Python, đẩy sang service này chạy để lấy kết quả chính xác thay vì tự "đoán" kết quả.
2.  **Mở rộng bộ dữ liệu Benchmarking:** AI Study Hub đã xây dựng sẵn các `Evaluation routes` và module Benchmark để đánh giá RAG. Thay vì chỉ test bằng các câu hỏi tự tạo, nhóm có thể tải các bộ dữ liệu công khai được bài báo sử dụng (ví dụ: E-EVAL hoặc OpenBookQA) và đưa vào database MongoDB để có một thước đo chuẩn mực đối chiếu giữa `Basic RAG` và `Corrective RAG`.
3.  **Hỗ trợ truy xuất đa phương thức (Images in Documents):** Báo cáo hiện tại ghi nhận AI Study Hub thực hiện "extracted text" (trích xuất văn bản) từ file PDF, DOCX. Theo bài báo, xử lý đa phương thức (text + images) trong học liệu (như bộ dữ liệu TQA) rất quan trọng. Nhóm có thể cải tiến module `Upload and Indexing Flow` bằng cách sử dụng các mô hình Vision (như GPT-4o hoặc Gemini Vision) để mô tả lại hình ảnh/biểu đồ trong slide thành văn bản, sau đó lưu vào Pinecone, giúp AI có thể trả lời các câu hỏi liên quan đến hình ảnh.
