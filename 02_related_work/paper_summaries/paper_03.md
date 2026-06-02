# Paper 04 Summary

## Citation

- **Tên bài:** Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.
- **Tác giả:** Patrick Lewis, Ethan Perez, Aleksandra Piktus, Fabio Petroni, Vladimir Karpukhin, Naman Goyal, Heinrich Küttler, Mike Lewis, Wen-tau Yih, Tim Rocktäschel, Sebastian Riedel, Douwe Kiela.
- **Năm:** 2020.
- **Nguồn:** Facebook AI Research, University College London, New York University.
- **DOI/Link:** https://arxiv.org/abs/2005.11401

## Problem

**Bài báo giải quyết vấn đề gì?**
Các Mô hình Ngôn ngữ Lớn (LLMs) có khả năng lưu trữ thông tin thực tế nhưng gặp hạn chế trong việc truy cập và thao tác chính xác kiến thức đó, dẫn đến hiện tượng "ảo giác" (hallucinations) và hiệu suất kém ở các tác vụ đòi hỏi lượng kiến thức chuyên sâu. Ngoài ra, các mô hình thuần tham số (parametric models) không thể cung cấp nguồn gốc minh chứng (provenance) cho các quyết định của chúng và rất khó để cập nhật kiến thức mới mà không phải huấn luyện lại.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Bài báo đề xuất framework **RAG (Retrieval-Augmented Generation)**, kết hợp sức mạnh của:

1.  **Bộ nhớ tham số (Parametric memory):** Một mô hình ngôn ngữ sinh văn bản (cụ thể là mô hình seq2seq BART-large).
2.  **Bộ nhớ phi tham số (Non-parametric memory):** Một cơ sở dữ liệu vector dày đặc (dense vector index) từ Wikipedia, được truy xuất bằng bộ truy xuất mạng nề (Dense Passage Retriever - DPR).

Bài báo đề xuất hai biến thể của mô hình này:

- **RAG-Sequence:** Sử dụng cùng một tài liệu được truy xuất để làm ngữ cảnh sinh ra toàn bộ câu trả lời.
- **RAG-Token:** Có khả năng trích xuất các tài liệu khác nhau cho từng token (từng từ) được sinh ra, cho phép mô hình nhặt và kết hợp thông tin từ nhiều nguồn tài liệu khác nhau cho một câu trả lời.

## Dataset

**Bài báo dùng dữ liệu gì?**
RAG được đánh giá trên một loạt các tác vụ chuyên biệt về kiến thức:

- **Hỏi đáp miền mở (Open-domain QA):** Natural Questions (NQ), TriviaQA, WebQuestions, và CuratedTrec.
- **Sinh văn bản (Abstractive QA & Generation):** MS-MARCO NLG và Jeopardy Question Generation.
- **Kiểm chứng sự thật (Fact Verification):** Tập dữ liệu FEVER.

## Evaluation

**Bài báo đánh giá bằng metric nào?**

- **Exact Match (EM):** Đo lường độ chính xác cho các tác vụ hỏi đáp.
- **Q-BLEU-1 và Đánh giá của con người (Human Evaluation):** So sánh về tính chính xác (factuality) và tính cụ thể (specificity) cho tác vụ sinh văn bản.
- **Label Accuracy:** Đo lường độ chuẩn xác cho tác vụ phân loại kiểm chứng sự thật.

## Results

**Kết quả chính là gì?**

- RAG thiết lập kỷ lục State-of-the-Art (SotA) mới trên 3 bộ dữ liệu hỏi đáp miền mở, vượt qua hoàn toàn các mô hình seq2seq thuần túy và các cấu trúc trích xuất truyền thống.
- Đối với tác vụ sinh văn bản, RAG tạo ra các câu trả lời cụ thể, đa dạng và bám sát thực tế hơn mô hình seq2seq (BART) tiêu chuẩn.
- **Tính linh hoạt cực cao:** Nhờ cơ chế "Index hot-swapping", kiến thức thế giới của RAG có thể được cập nhật ngay lập tức bằng cách thay thế cơ sở dữ liệu phi tham số mà không cần phải huấn luyện lại bất kỳ tham số nào của mô hình AI.

## Limitations

**Hạn chế của bài báo là gì?**

- Quá trình giải mã (decoding) của mô hình RAG-Sequence khá phức tạp và đòi hỏi phải chạy (forward pass) qua nhiều tài liệu, tiêu thụ nhiều tài nguyên hơn mô hình tiêu chuẩn.
- Trong một số tác vụ, mô hình có thể gặp hiện tượng "sụp đổ truy xuất" (retrieval collapse), trong đó bộ sinh văn bản học cách phớt lờ hoàn toàn các tài liệu được truy xuất và chỉ tự trả lời bằng kiến thức tham số của nó.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Đây là bài báo nền tảng, "khai sinh" ra kỹ thuật Retrieval-Augmented Generation, và là **lý thuyết gốc cho toàn bộ hệ thống AI Study Hub** của nhóm.
Cụ thể, kiến trúc của AI Study Hub hoàn toàn sao chép lại mô hình được bài báo mô tả: nhóm sử dụng Pinecone làm "bộ nhớ phi tham số" (non-parametric memory) và Groq SDK đóng vai trò "bộ nhớ tham số" (parametric memory / generator). Đồng thời, khả năng cung cấp nguồn (provenance) nhằm khắc phục "ảo giác" mà bài báo giải quyết chính là tính năng cốt lõi của AI Study Hub để cung cấp câu trả lời có tính xác thực cao (grounded answers) thông qua việc lưu trữ `source chunks` vào database `Chat History` cho mỗi lần giải đáp.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**

1.  **Triển khai "Hot-swapping" cho thư viện tài liệu (Document Library):** Bài báo chứng minh có thể thay đổi kiến thức bằng cách hoán đổi index (hot-swapping) rất dễ dàng. Trong AI Study Hub, người dùng có thể tải lên nhiều loại tài liệu (PDF, DOCX). Nhóm có thể thêm tính năng "Toggles" trên giao diện Chat (`/aichatbox`) để người dùng bật/tắt các file hoặc subject cụ thể (ví dụ: chỉ tìm trong slide "Toán", bỏ qua slide "Lý"). Backend sẽ linh hoạt lọc metadata (namespaces/filters) trên Pinecone, mô phỏng lại cơ chế hot-swapping này nhằm thu hẹp phạm vi không gian vector ngay tức thì mà không cần re-index.
2.  **Ứng dụng RAG cho tính năng "Fact-Checking/Auto-Grader":** Bài báo đã dùng RAG thành công cho tác vụ kiểm chứng sự thật (FEVER dataset). Hệ thống của nhóm đã có sẵn module `Evaluation routes`. Thay vì chỉ dùng để đối chiếu 2 mode RAG (Basic vs Corrective), nhóm có thể tạo một tính năng mở rộng cho sinh viên tự điền câu trả lời của họ vào, sau đó dùng RAG truy xuất tài liệu học tập để đưa ra phán quyết (supports/refutes/not enough info) xem sinh viên đã làm bài đúng hay sai.
3.  **Thử nghiệm chiến lược RAG-Token (Kết hợp mảnh kiến thức):** Hiện tại, luồng truy xuất của hệ thống dường như đang gộp tất cả các chunks lại và đưa vào Groq để sinh trả lời một lần (tương tự RAG-Sequence). Theo bài báo, biến thể RAG-Token rất mạnh trong việc tổng hợp các ý nhỏ từ các tài liệu khác nhau. Nhóm có thể nghiên cứu các phương pháp prompt nâng cao hoặc gọi LLM nhiều lần (chain-of-thought) để AI có thể nhặt từng ý (token-level) từ nhiều slide bài giảng khác nhau nhằm giải quyết các câu hỏi so sánh hoặc tổng hợp phức tạp của sinh viên.
