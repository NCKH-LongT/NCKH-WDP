# Paper 05 Summary

## Citation

- **Tên bài:** DR-RAG: Applying Dynamic Document Relevance to Retrieval-Augmented Generation for Question-Answering.
- **Tác giả:** Zijian Hei, Weiling Liu, Wenjie Ou, Juyi Qiao, Junming Jiao, Guowen Song, Ting Tian, Yi Lin.
- **Năm:** 2024 (Ước tính dựa trên các tài liệu trích dẫn mới nhất trong bài như Llama 3 2024).
- **Nguồn:** Li Auto Inc., Sun Yat-sen University, Northeastern University, Sichuan University.
- **DOI/Link:** https://arxiv.org/abs/2406.07348

## Problem

**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết hai vấn đề lớn của RAG trong các tác vụ hỏi đáp phức tạp (multi-hop QA). Thứ nhất, các hệ thống RAG thường chỉ truy xuất được các **tài liệu có liên quan tĩnh (static-relevant)** – tức là những tài liệu chứa từ khóa giống trực tiếp với câu hỏi, nhưng lại bỏ sót các **tài liệu liên quan động (dynamic-relevant)** – những tài liệu chỉ liên quan gián tiếp nhưng cực kỳ quan trọng để suy luận ra câu trả lời cuối cùng. Thứ hai, nếu tăng số lượng tài liệu truy xuất (top-k) để cố lấy được tài liệu động, hệ thống sẽ gom nhầm rất nhiều thông tin rác (redundant information), làm giảm chất lượng sinh văn bản của LLM.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Bài báo đề xuất framework **DR-RAG (Dynamic-Relevant Retrieval-Augmented Generation)** hoạt động theo 2 giai đoạn:

1.  **Truy xuất 2 bước (Query Document Concatenation - QDC):** Bước 1, dùng câu hỏi gốc để tìm các tài liệu tĩnh. Bước 2, **nối (concatenate)** câu hỏi gốc với tài liệu tĩnh vừa tìm được để tạo thành một truy vấn mới dài hơn, từ đó truy xuất ra các tài liệu động nằm sâu trong cơ sở dữ liệu.
2.  **Bộ lọc phân loại (Classifier for Selection):** Sử dụng một mô hình phân loại cực nhỏ (như BigBird hoặc Longformer) để chấm điểm độc lập các tài liệu truy xuất được xem chúng có thực sự đóng góp cho câu trả lời hay không. Bài báo đề xuất 2 chiến lược lọc: _Classifier Inverse Selection (CIS)_ (loại bỏ tài liệu thừa ở cuối cùng) và _Classifier Forward Selection (CFS)_ (lọc ngay lập tức từng tài liệu trong quá trình truy xuất bước 2).

## Dataset

**Bài báo dùng dữ liệu gì?**
Hệ thống được đánh giá trên 3 bộ dữ liệu hỏi đáp đa bước (multi-hop QA datasets) nổi tiếng:

1.  **HotpotQA**.
2.  **2WikiMultiHopQA (2Wiki)**.
3.  **MuSiQue**.

## Evaluation

**Bài báo đánh giá bằng metric nào?**

- **Chất lượng câu trả lời:** Exact Match (EM), F1 Score, và Accuracy (Acc).
- **Hiệu suất hệ thống:** Recall rate (Tỷ lệ thu hồi tài liệu đúng), Actual numbers (Số lượng tài liệu thực tế đưa vào LLM), Number of steps (Số lần gọi LLM), và Time per Query (Thời gian xử lý mỗi câu hỏi).

## Results

**Kết quả chính là gì?**

- DR-RAG cải thiện đáng kể cả 3 chỉ số EM, F1 và Acc trên mọi bộ dữ liệu so với các framework tiên tiến như Self-RAG hay Adaptive-RAG.
- Phương pháp lọc CFS giúp **tăng tỷ lệ recall lên đến 86.75%** trong khi vẫn **giảm được số lượng tài liệu rác** thực tế đưa vào LLM.
- **Tốc độ cực nhanh:** Khác với các hệ thống suy luận đa bước phải gọi API LLM nhiều lần, DR-RAG chỉ mất 1 bước gọi LLM duy nhất (Single-step LLM call). Nhờ dùng classifier nhỏ để lọc tài liệu, thời gian phản hồi (Time per Query) của DR-RAG giảm trung bình **74.2%** so với Adaptive-RAG.

## Limitations

**Hạn chế của bài báo là gì?**

- Đòi hỏi phải huấn luyện (train) trước một mô hình classifier (bộ phân loại) riêng biệt. Điều này có thể gặp khó khăn nếu áp dụng vào các lĩnh vực quá ngách (niche domains) vì thiếu dữ liệu để huấn luyện.
- Hệ thống chưa có cơ chế kiểm duyệt nội dung đầu vào, có thể bị ảnh hưởng bởi các câu hỏi chứa nội dung độc hại hoặc khi truy xuất trúng các tài liệu có thông tin không phù hợp.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này cung cấp giải pháp tối ưu trực tiếp cho tính năng **Corrective RAG** và **luồng Question Answering** trong kiến trúc của dự án AI Study Hub.
Trong tài liệu báo cáo `REPORT.md`, nhóm ghi rõ Corrective RAG của AI Study Hub có tính năng _"filters chunks by relevance"_ (lọc các đoạn văn bản theo độ liên quan) và dùng _"Groq SDK"_ để sinh cũng như đánh giá câu trả lời. Tuy nhiên, nếu dùng Groq (một LLM lớn) để chấm điểm từng đoạn văn bản (chunk), thời gian chờ của người dùng sẽ bị kéo dài và chi phí API sẽ tăng cao. DR-RAG chứng minh rằng việc dùng một mô hình phân loại cực nhẹ (125M tham số) để làm bộ lọc không chỉ tăng tốc độ hệ thống lên gấp nhiều lần mà còn giúp LLM trả lời chính xác hơn các câu hỏi mang tính tổng hợp (ví dụ: sinh viên hỏi một câu cần kết nối kiến thức từ slide chương 1 và chương 3).

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**

1.  **Tích hợp QDC (Query Document Concatenation) cho Luồng Truy xuất đa bước:** Hiện tại AI Study Hub chỉ nhúng (embed) câu hỏi gốc để tìm trên Pinecone. Nếu sinh viên hỏi câu phức tạp, Backend có thể triển khai chiến lược QDC: Lấy ra đoạn văn bản (chunk) liên quan nhất ở lần tìm đầu tiên, nối chunk đó vào đuôi câu hỏi của sinh viên, rồi gọi Jina Embeddings để query Pinecone thêm một lần nữa. Cách này giúp hệ thống tìm được các khái niệm liên đới mà cách tìm thông thường bị bỏ sót.
2.  **Xây dựng Service Bộ lọc nhẹ (Lightweight Classifier Microservice):** Để tránh phụ thuộc hoàn toàn vào Groq SDK cho khâu _"filters chunks by relevance"_, nhóm có thể sử dụng một mô hình mã nguồn mở cực nhỏ (ví dụ: mô hình classify tiếng Việt dựa trên PhoBERT hoặc ONNX-based model) chạy trực tiếp trên Node.js Backend. Mô hình này đóng vai trò thực thi luồng CFS (Classifier Forward Selection), tự động loại bỏ các slide rác trước khi nhồi (inject) vào prompt cho Groq. Việc này giúp giảm số lượng token gửi đi và tăng tốc `response_time`.
3.  **Bổ sung "Redundancy Ratio" vào Evaluation Dashboard:** Module `RAG Evaluation and Benchmarking` của nhóm đã rất chi tiết với các trường như `retrieved_chunk_count` và `relevant_chunk_count`. Lấy cảm hứng từ phép đo của bài báo, nhóm có thể bổ sung thêm một metric là **Redundancy Ratio** (Tỷ lệ nhiễu = 1 - (relevant_chunks / retrieved_chunks)) hiển thị trực quan lên trang `/admin/activity` để admin đánh giá xem Pinecone có đang trả về quá nhiều tài liệu vô ích hay không.
