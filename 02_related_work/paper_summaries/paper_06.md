# Paper 06 Summary

## Citation

- **Tên bài:** SELF-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection.
- **Tác giả:** Akari Asai, Zeqiu Wu, Yizhong Wang, Avirup Sil, Hannaneh Hajishirzi.
- **Năm:** 2023.
- **Nguồn:** University of Washington, Allen Institute for AI, IBM Research AI.
- **DOI/Link:** https://arxiv.org/abs/2310.11511

## Problem

**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết vấn đề ảo giác (factual inaccuracies/hallucinations) ở các Mô hình Ngôn ngữ Lớn (LLMs). Mặc dù phương pháp RAG truyền thống giúp giảm thiểu lỗi này, nhưng nó có một nhược điểm lớn: RAG thường truy xuất một lượng tài liệu cố định một cách bừa bãi (indiscriminately) bất kể câu hỏi có cần truy xuất thông tin hay không, hoặc tài liệu có liên quan hay không. Điều này có thể làm giảm tính linh hoạt của mô hình, đưa vào các thông tin nhiễu (off-topic) làm giảm chất lượng sinh văn bản, và không đảm bảo rằng câu trả lời cuối cùng thực sự dựa trên các tài liệu đã truy xuất.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Tác giả đề xuất framework **SELF-RAG (Self-Reflective Retrieval-Augmented Generation)**. Phương pháp này huấn luyện một LLM (như Llama 2) học cách tự truy xuất theo yêu cầu (on-demand) và tự đánh giá (self-reflection) quá trình sinh văn bản của chính nó thông qua các "token phản ngẫm" (reflection tokens) đặc biệt, bao gồm:

1.  `Retrieve`: Đánh giá xem câu hỏi có cần gọi bộ truy xuất (retriever) hay không.
2.  `ISREL`: Đánh giá xem tài liệu được truy xuất có liên quan (relevant) hay không.
3.  `ISSUP`: Đánh giá xem câu trả lời được sinh ra có được hỗ trợ/chứng minh (fully supported/partially supported) bởi tài liệu hay không.
4.  `ISUSE`: Đánh giá mức độ hữu ích tổng thể của câu trả lời.
    Hệ thống xử lý song song nhiều tài liệu và sử dụng thuật toán tìm kiếm (segment-level beam search) kết hợp với điểm số từ các token phản ngẫm trên để chọn ra đoạn văn bản tốt nhất.

## Dataset

**Bài báo dùng dữ liệu gì?**
Mô hình được huấn luyện trên một tập dữ liệu gồm 150.000 cặp câu hỏi - câu trả lời đa dạng (từ Open-Instruct, KILT, ASQA, v.v.) đã được chèn sẵn các token phản ngẫm.
Việc đánh giá được thực hiện trên 6 bộ dữ liệu đại diện cho 3 nhóm tác vụ:

- Đóng (Closed-set): PubHealth, ARC-Challenge.
- Hỏi đáp ngắn (Short-form QA): PopQA, TriviaQA-unfiltered.
- Sinh văn bản dài (Long-form generation): Sinh tiểu sử (Biography generation) và ALCE-ASQA.

## Evaluation

**Bài báo đánh giá bằng metric nào?**
Các số đo đánh giá bao gồm:

- **Accuracy (Độ chính xác):** Dùng cho các tập PubHealth và ARC-Challenge.
- **FactScore:** Đánh giá độ chính xác về mặt sự thật cho tác vụ sinh tiểu sử.
- **Correctness (str-em, ROUGE), Fluency (MAUVE), và Citation precision/recall:** Đánh giá độ chuẩn xác của trích dẫn và chất lượng văn bản dài cho tác vụ ASQA.

## Results

**Kết quả chính là gì?**

- SELF-RAG (ở cả bản 7B và 13B tham số) vượt trội hơn hẳn các LLM hiện đại có nhiều tham số hơn (như ChatGPT, Llama2-chat) cũng như các hệ thống RAG tiêu chuẩn trong các tác vụ QA mở, suy luận và xác minh sự thật.
- Đặc biệt trong các tác vụ sinh văn bản dài, SELF-RAG cho thấy sự cải thiện đáng kể về mặt trung thực của dữ kiện (factuality) và độ chính xác của các trích dẫn (citation precision).
- Cơ chế "truy xuất theo yêu cầu" giúp mô hình giữ được sự linh hoạt (versatility) của một AI hội thoại thông thường mà vẫn chính xác khi cần.

## Limitations

**Hạn chế của bài báo là gì?**

- Dù cải thiện đáng kể, mô hình thỉnh thoảng vẫn sinh ra các câu trả lời không được hỗ trợ hoàn toàn bởi tài liệu trích dẫn.
- Việc sử dụng thuật toán tạo văn bản có sự đánh giá từ critique tokens (segment-level beam search) khiến quá trình inference (suy luận) phức tạp và có thể đòi hỏi tài nguyên tính toán cao hơn so với giải mã tham lam (greedy decoding) thông thường.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này có liên kết mật thiết với cấu trúc hệ thống của dự án **AI Study Hub**. Nhóm đang phát triển một luồng xử lý "Corrective RAG" tích hợp khả năng "filters chunks by relevance" (lọc các đoạn văn bản theo độ liên quan) và "performs grounding checks" (kiểm tra mức độ dựa dẫm vào tài liệu).
Khái niệm self-reflection với các token `ISREL` (đánh giá độ liên quan) và `ISSUP` (đánh giá độ hỗ trợ) của SELF-RAG chính là cơ sở học thuật vững chắc cho hệ thống của nhóm. Đồng thời, mô-đun **RAG Evaluation and Benchmarking** của dự án đang lưu trữ các chỉ số như _relevance score_, _confidence score_, và _grounding result_. Việc áp dụng nguyên lý đánh giá này cho thấy hệ thống thực tế của nhóm hoàn toàn bắt kịp với kiến trúc RAG hiện đại nhất được đề xuất trong giới nghiên cứu AI.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**
Dựa trên kiến trúc của AI Study Hub và các nguyên lý của SELF-RAG, nhóm có thể thực hiện 3 điểm cải tiến:

1.  **Tích hợp Truy xuất Thích ứng (Adaptive Retrieval):** Theo bài báo, không phải truy vấn nào cũng cần tìm kiếm tài liệu (thể hiện qua token `Retrieve`). Hiện tại, AI Study Hub thực hiện quá trình nhúng (embedding) và truy xuất Pinecone cho mọi câu hỏi. Nhóm có thể thêm một bước kiểm tra nhỏ ở Backend bằng Groq LLM trước khi gọi Pinecone để xác định: nếu sinh viên chỉ chào hỏi hoặc hỏi kiến thức phổ thông đơn giản, hệ thống có thể bỏ qua bước truy xuất để trả lời ngay, giúp tiết kiệm chi phí API và tăng tốc độ phản hồi (response time).
2.  **Đánh giá độ trích dẫn ở cấp độ câu (Sentence-level Citation):** Theo cơ chế sinh văn bản của bài báo, mô hình đánh giá từng "phân đoạn" (segment) xem nó là _Fully supported_ hay _Partially supported_. Frontend của AI Study Hub (`assistant-ui`) có thể được nâng cấp để highlight (bôi màu) từng câu trả lời của Chatbot. Những câu có `grounding_score` cao sẽ hiển thị màu xanh (được hỗ trợ hoàn toàn bởi slide bài giảng), giúp sinh viên tự tin hơn vào câu trả lời.
3.  **Tối ưu chiến lược chọn Chunk (Segment-level Beam Search):** Thay vì truy xuất một lượng lớn chunks từ Pinecone rồi nhồi tất cả vào prompt cho Groq sinh câu trả lời một lần (indiscriminate retrieval), backend có thể mô phỏng SELF-RAG bằng cách đưa các chunk chạy song song (parallel) qua một vòng LLM đánh giá nhỏ để sinh ra điểm `ISREL`. Sau đó, hệ thống chỉ gộp những chunk có điểm cao nhất vào Context cuối cùng. Điều này giúp làm giảm độ nhiễu và loại bỏ hoàn toàn các slide/tài liệu không liên quan khỏi câu trả lời của AI Study Hub.
