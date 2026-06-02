# Paper 4 Summary

## Citation

- **Tên bài:** KNOWSHIFTQA: How Robust are RAG Systems when Textbook Knowledge Shifts in K-12 Education?
- **Tác giả:** Tianshi Zheng, Weihan Li, Jiaxin Bai, Weiqi Wang, Yangqiu Song.
- **Năm:** 2024.
- **Nguồn:** The Hong Kong University of Science and Technology (HKUST) và The University of Tokyo.
- **DOI/Link:** https://arxiv.org/abs/2412.08985

## Problem

**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết bài toán về độ tin cậy (robustness) của các hệ thống RAG trong giáo dục khi đối mặt với **sự sai lệch/thay đổi kiến thức (knowledge discrepancies/shifts)**. Trong môi trường giáo dục, câu trả lời phải bám sát tuyệt đối vào sách giáo khoa chính thống. Tuy nhiên, sách giáo khoa thường xuyên được cập nhật, tạo ra sự mâu thuẫn với kiến thức nội tại (parametric knowledge) đã được huấn luyện sẵn của các Mô hình Ngôn ngữ Lớn (LLMs). Nghiên cứu đặt câu hỏi: Liệu các hệ thống RAG có ưu tiên thông tin mới từ tài liệu hay vẫn bị "ảo giác" đi theo kiến thức cũ của LLM?.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**

- **Phương pháp Cập nhật tri thức giả định (Hypothetical Knowledge Update):** Bài báo chủ động thay đổi các sự thật trong sách giáo khoa thành một đáp án khác hợp lý nhưng sai thực tế (ví dụ: đổi "Ấn Độ có dân số cao nhất" thành "Trung Quốc có dân số cao nhất") để ép LLM phải đối mặt với mâu thuẫn.
- **Đánh giá đa mô hình:** Bài báo thử nghiệm hàng loạt phương pháp truy xuất từ Lexical (BM25, TF-IDF), Dense (Contriever, Ada-002) đến Ensemble (Hybrid Rerank). Ở khâu sinh văn bản, hệ thống kiểm tra các LLMs hiện đại nhất (như Llama 3, GPT-4o, Claude 3.5, Gemini, o1) kết hợp với kỹ thuật prompt "Locate-and-Answer".

## Dataset

**Bài báo dùng dữ liệu gì?**
Nghiên cứu tạo ra bộ dữ liệu mới mang tên **KNOWSHIFTQA** gồm 3.005 câu hỏi trắc nghiệm. Dữ liệu này được trích xuất từ các sách giáo khoa mã nguồn mở (OpenStax, OER Commons) dành cho học sinh trung học (K-12), bao phủ 5 môn học: Vật lý, Hóa học, Sinh học, Địa lý và Lịch sử. Các câu hỏi được chia thành 5 mức độ suy luận phức tạp khác nhau.

## Evaluation

**Bài báo đánh giá bằng metric nào?**

- **Khả năng truy xuất (Retrieval):** Đánh giá bằng Recall@1 và Recall@5.
- **Khả năng trả lời (Question Answering):** Đánh giá bằng Accuracy (Độ chính xác) ở môi trường zero-shot.

## Results

**Kết quả chính là gì?**

- **Sự sụt giảm nghiêm trọng:** Khi có sự sai lệch kiến thức, độ chính xác của các hệ thống RAG giảm mạnh từ 22% đến 27%, chứng tỏ hệ thống RAG hiện tại rất dễ bị tổn thương và thường thiên vị kiến thức nội tại của LLM thay vì tài liệu được cung cấp.
- **Truy xuất từ khóa chiếm ưu thế:** Trong miền giáo dục, các mô hình truy xuất truyền thống như BM25 lại thể hiện cực kỳ tốt nhờ bắt đúng các thuật ngữ học thuật, trong khi các mô hình truy xuất vector (dense retrieval) chỉ thực sự mạnh nếu được huấn luyện tinh chỉnh (fine-tuned) trên chính tập dữ liệu đó.
- **Hạn chế trong việc tích hợp tri thức:** Các LLM gặp khó khăn lớn nhất ở các câu hỏi "Implicit" (Ngầm định), nơi chúng phải kết hợp kiến thức từ tài liệu với kiến thức nền của chính mình để đưa ra suy luận.

## Limitations

**Hạn chế của bài báo là gì?**

- **Dữ liệu mô phỏng:** Việc tạo ra các sai lệch kiến thức mang tính giả định (hypothetical) thay vì sử dụng các sự thay đổi có thật theo thời gian (temporal misalignment), do dữ liệu thực tế quá thưa thớt và khó thu thập ở quy mô lớn.
- **Thiếu cấu trúc truy xuất phân tầng:** Bài báo chưa tích hợp các kiến trúc truy xuất cấu trúc đồ thị tiên tiến như GraphRAG hay HippoRAG, những công cụ có thể tỏ ra rất hiệu quả với tài liệu giáo dục có cấu trúc rõ ràng.
- Nghiên cứu mới chỉ dừng ở việc đánh giá sự yếu kém (robustness evaluation) chứ chưa đề xuất được một framework prompt hay thuật toán tinh chỉnh nào để khắc phục triệt để điểm yếu này.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này hoàn thiện mảnh ghép thứ 10 cho bộ tài liệu của bạn, thuộc nhóm **Domain ứng dụng (Lĩnh vực Giáo dục)**. Nó mô tả chính xác vấn đề thực tiễn mà dự án **AI Study Hub** của nhóm sẽ gặp phải.
Hệ thống AI Study Hub cho phép sinh viên tải lên các file bài giảng cá nhân (PDF, PPTX) và dùng `Groq SDK` để sinh câu trả lời. Tuy nhiên, bài giảng của một giảng viên cụ thể có thể chứa các quy ước, định nghĩa, hoặc số liệu đã được cập nhật khác hoàn toàn với kiến thức chung mà mô hình của Groq đã học. Bài báo cung cấp minh chứng khoa học vững chắc rằng: luồng RAG của AI Study Hub có nguy cơ thất bại (sụt giảm độ chính xác 27%) nếu sinh viên hỏi những thông tin có sự mâu thuẫn này. Do đó, bài báo tạo ra động lực và cơ sở lý thuyết để nhóm thiết kế luồng `Corrective RAG` có khả năng ưu tiên tài liệu gốc.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**

1.  **Cải tiến prompt bằng kỹ thuật "Locate-and-Answer":** Bài báo chứng minh việc ép LLM phải tìm vị trí chứa thông tin trước khi trả lời giúp tăng độ chính xác đáng kể (ví dụ GPT-4o tăng từ 80.43% lên 87.09%). Trong mã nguồn thiết lập lời gọi LLM cho `Groq SDK` của dự án, nhóm có thể sửa lại System Prompt: _"Trước khi đưa ra câu trả lời, hãy trích dẫn nguyên văn câu văn trong tài liệu. Sau đó mới sinh ra câu trả lời cuối cùng."_ Điều này giúp kiềm chế ảo giác của LLM.
2.  **Tích hợp Hybrid Search (Sparse + Dense):** Hệ thống AI Study Hub hiện tại sử dụng thuần túy `Jina Embeddings` và `Pinecone` (Vector/Dense Search). Tuy nhiên, bài báo chỉ ra BM25 (tìm kiếm từ khóa) rất mạnh trong tài liệu giáo dục chứa thuật ngữ đặc thù. Nhóm nên kết hợp thêm một engine như Elasticsearch hoặc dùng tính năng Hybrid Search của Pinecone để kết hợp cả hai, giúp luồng `Basic RAG` tìm kiếm tài liệu chuẩn xác hơn.
3.  **Bổ sung "Conflict Test" vào module Benchmarking:** Báo cáo hiện tại ghi nhận nhóm đã có module `RAG Evaluation and Benchmarking` đánh giá `correctness` và `faithfulness`. Lấy cảm hứng từ bài báo, nhóm có thể tạo ra một "bộ câu hỏi gài bẫy" (cố tình cung cấp một slide có nội dung sai lệch so với kiến thức phổ thông) và chạy qua `Benchmark routes`. Nếu hệ thống đạt điểm `faithfulness` cao trên bộ test này, nhóm có thể tự tin khẳng định hệ thống `Corrective RAG` của mình thực sự bám sát tài liệu của sinh viên thay vì tự "bịa" theo kiến thức của LLM.
