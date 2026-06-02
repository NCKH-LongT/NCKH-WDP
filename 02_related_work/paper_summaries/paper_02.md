# Paper 02 Summary

## Citation

- **Tên bài:** Dense Passage Retrieval for Open-Domain Question Answering.
- **Tác giả:** Vladimir Karpukhin, Barlas Oğuz, Sewon Min, Patrick Lewis, Ledell Wu, Sergey Edunov, Danqi Chen, Wen-tau Yih.
- **Năm:** 2020.
- **Nguồn:** Facebook AI, University of Washington, Princeton University.
- **DOI/Link:** https://aclanthology.org/2020.emnlp-main.550/

## Problem

**Bài báo giải quyết vấn đề gì?**
Trong các hệ thống Hỏi đáp Miền mở (Open-domain QA), việc truy xuất tài liệu truyền thống phụ thuộc vào **các mô hình không gian vector thưa thớt (sparse vector) như TF-IDF hoặc BM25**. Các phương pháp này tìm kiếm dựa trên sự trùng khớp từ khóa (keyword matching), dẫn đến việc thất bại khi câu hỏi sử dụng từ đồng nghĩa hoặc cách diễn đạt khác so với tài liệu. Các nỗ lực trước đó để sử dụng **vector dày đặc (dense representations)** nhằm bắt ngữ nghĩa thường đòi hỏi các bước huấn luyện trước (pre-training) cực kỳ phức tạp và tốn kém tài nguyên máy tính.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Bài báo đề xuất mô hình **DPR (Dense Passage Retriever)**, chứng minh rằng có thể huấn luyện một bộ truy xuất vector dày đặc cực tốt chỉ bằng các cặp câu hỏi - đoạn văn bản thông thường.
Kiến trúc sử dụng khung **bộ mã hóa kép (dual-encoder)** với hai mạng BERT độc lập: một để mã hóa câu hỏi và một để mã hóa tài liệu thành các vector 768 chiều. Độ tương đồng được tính đơn giản bằng tích vô hướng (dot product) giữa hai vector. Điểm đột phá của phương pháp nằm ở **chiến lược huấn luyện**: hệ thống tận dụng các tài liệu của câu hỏi khác trong cùng một lô (in-batch negatives) kết hợp với một tài liệu nhiễu có độ trùng lặp từ khóa cao (BM25 hard negative) để dạy cho mô hình cách phân biệt đâu là tài liệu thực sự liên quan về mặt ngữ nghĩa. Tài liệu sau đó được lập chỉ mục (index) và truy xuất cực nhanh bằng thư viện FAISS.

## Dataset

**Bài báo dùng dữ liệu gì?**
DPR được đánh giá trên 5 bộ dữ liệu hỏi đáp phổ biến: Natural Questions (NQ), TriviaQA, WebQuestions, CuratedTREC, và SQuAD v1.1. Tập tài liệu nguồn (corpus) là một bản sao chép của Wikipedia tiếng Anh, được chia nhỏ thành hơn 21 triệu đoạn văn bản (passages) chứa 100 từ.

## Evaluation

**Bài báo đánh giá bằng metric nào?**

- **Top-k Retrieval Accuracy (Độ chính xác truy xuất Top-k):** Tỷ lệ phần trăm trong đó top 20 hoặc 100 tài liệu được truy xuất có chứa chuỗi câu trả lời đúng.
- **Exact Match (EM):** Độ chính xác khớp hoàn toàn câu trả lời, dùng để đánh giá hệ thống QA end-to-end (kết hợp cả hệ thống đọc hiểu để trích xuất câu trả lời).

## Results

**Kết quả chính là gì?**

- **Vượt trội so với BM25:** DPR đánh bại hoàn toàn hệ thống BM25 truyền thống với khoảng cách từ **9% đến 19% độ chính xác truy xuất Top-20** trên nhiều bộ dữ liệu (ví dụ trên Natural Questions: 78.4% so với 59.1%).
- **Tạo ra kỷ lục mới (State-of-the-Art):** Khi kết hợp DPR với một mô hình đọc hiểu (reader), hệ thống QA thiết lập thành tích cao nhất mới trên 4/5 bộ dữ liệu mở.
- **Tốc độ thực thi cực nhanh:** Nhờ sử dụng FAISS cho không gian vector dày đặc, ở môi trường thực tế, hệ thống có thể xử lý gần **1.000 câu hỏi mỗi giây**.

## Limitations

**Hạn chế của bài báo là gì?**

- **Lép vế khi có sự trùng lặp từ vựng cao:** Trên bộ dữ liệu SQuAD, BM25 lại thắng DPR. Lý do là vì bộ dữ liệu SQuAD được tạo ra bằng cách cho người đọc nhìn trực tiếp vào đoạn văn để đặt câu hỏi, dẫn đến từ khóa bị bê nguyên xi từ văn bản vào câu hỏi (lexical overlap). Trong trường hợp này, tìm từ khóa chuẩn xác hơn tìm ngữ nghĩa.
- **Chi phí tạo chỉ mục (Index Building):** Việc nhúng và xây dựng chỉ mục vector cho 21 triệu tài liệu tốn đến 8.5 giờ trên nhiều GPU, tốn kém tài nguyên và thời gian hơn rất nhiều so với việc lập chỉ mục từ khóa ngược (inverted index) bằng Lucene (chỉ mất 30 phút).

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này thuộc nhóm **Bài báo về model AI hoặc phương pháp AI**, và là một mảnh ghép nền tảng giải thích cho toàn bộ luồng xử lý `Upload and Indexing Flow` của **AI Study Hub**.
Hệ thống của nhóm sử dụng `Jina Embeddings` để chuyển đổi tài liệu học tập thành vector và lưu trữ vào `Pinecone` vector database. Kiến trúc này chính là sự kế thừa trực tiếp từ khung "Dense Passage Retrieval" được Facebook AI đề xuất trong bài báo này. Bài báo cung cấp cơ sở học thuật vững chắc để giải thích trong đồ án của bạn lý do tại sao AI Study Hub lại chọn cách tiếp cận "nhúng vector" thay vì dùng tìm kiếm full-text search thông thường: đó là để giải quyết bài toán sinh viên hỏi các khái niệm tương đương (ngữ nghĩa) nhưng không dùng chính xác từ khóa có trong slide bài giảng.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**
Dựa trên kiến trúc `REPORT.md` của nhóm và các phát hiện từ DPR, bạn có thể cân nhắc các định hướng mở rộng sau:

1.  **Triển khai Hybrid Search (Tích hợp Dense + Sparse):** Bảng 2 và Bảng 4 của bài báo cho thấy việc kết hợp điểm số của BM25 và DPR (BM25 + DPR) cho ra kết quả cao nhất trong hầu hết các trường hợp. Hiện tại, AI Study Hub thuần túy dùng tìm kiếm vector trên Pinecone. Nhóm có thể nâng cấp bằng cách sử dụng API "Hybrid Search" của Pinecone (hoặc tích hợp thêm một engine như Elasticsearch) để kết hợp tìm kiếm ngữ nghĩa (Jina) với tìm kiếm từ khóa (BM25). Điều này cực kỳ quan trọng trong môi trường học thuật, vì đôi khi sinh viên muốn tìm kiếm các từ khóa có tính tuyệt đối như mã môn học, tên riêng, hoặc công thức hóa học.
2.  **Chiến lược huấn luyện "Hard Negatives" (Đề xuất định hướng):** Mặc dù nhóm hiện đang dùng mô hình Jina có sẵn, nếu sau này nhóm muốn huấn luyện tinh chỉnh (fine-tune) một mô hình embedding chuyên biệt cho giáo dục đại học tại Việt Nam, bài báo cung cấp một phương pháp luận chuẩn xác: Nhóm có thể trích xuất `Chat History` từ MongoDB, chọn cặp câu hỏi - tài liệu đúng làm positive, và dùng thuật toán BM25 tìm các đoạn slide có từ khóa giống nhau nhưng sai ngữ cảnh để làm "hard negative" đưa vào huấn luyện mô hình.
3.  **Bổ sung phân tích hành vi đặt câu hỏi trên Admin Dashboard:** Phát hiện của bài báo về sự suy giảm hiệu suất trên bộ dữ liệu SQuAD là một cơ sở rất tốt cho module `RAG Evaluation and Benchmarking` của nhóm. Trên trang Admin Dashboard `/admin/activity`, nhóm có thể thống kê tỷ lệ phần trăm các câu hỏi của sinh viên có chứa chính xác các từ khóa trong tài liệu. Nếu tỷ lệ này cao (nghĩa là sinh viên có thói quen copy/paste câu hỏi bài tập), hệ thống có thể được cấu hình ưu tiên trọng số cho tìm kiếm từ khóa. Nếu tỷ lệ thấp, hệ thống ưu tiên cho `Corrective RAG` và tìm kiếm ngữ nghĩa sâu.
