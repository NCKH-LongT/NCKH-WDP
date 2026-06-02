# Paper 07 Summary

## Citation

- **Tên bài:** Corrective Retrieval Augmented Generation.
- **Tác giả:** Shi-Qi Yan, Jia-Chen Gu, Yun Zhu, Zhen-Hua Ling.
- **Năm:** 2024 (Ước lượng dựa trên các tài liệu trích dẫn mới nhất trong bài như Self-RAG 2024).
- **Nguồn:** Các tác giả đến từ University of Science and Technology of China, University of California (UCLA) và Google DeepMind.
- **DOI/Link:** https://arxiv.org/abs/2401.15884

## Problem

**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết **vấn đề ảo giác (hallucinations) trong các Mô hình Ngôn ngữ Lớn (LLMs)** sinh ra do truy xuất thông tin không chính xác. Mặc dù phương pháp RAG (Retrieval-Augmented Generation) giúp cung cấp thêm kiến thức nền, nhưng nếu **hệ thống truy xuất (retriever) trả về tài liệu sai lệch hoặc không liên quan**, LLM sẽ bị cản trở, sinh ra câu trả lời sai sự thật hoặc bị đánh lừa. Đa số các phương pháp RAG hiện tại đều kết hợp toàn bộ tài liệu được truy xuất một cách bừa bãi mà không quan tâm đến độ chính xác của chúng.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Bài báo đề xuất framework **CRAG (Corrective Retrieval-Augmented Generation)**, mang tính chất "plug-and-play" (cắm và chạy), để tự sửa lỗi kết quả truy xuất. Hệ thống bao gồm 3 thành phần chính:

1.  **Bộ đánh giá truy xuất (Retrieval Evaluator):** Sử dụng một mô hình ngôn ngữ nhỏ gọn (T5-large, 0.77B parameters) để đánh giá độ liên quan của tài liệu được truy xuất đối với câu hỏi, sau đó phân loại thành 3 hành động: **Correct (Chính xác), Incorrect (Không chính xác), và Ambiguous (Mơ hồ)**.
2.  **Thuật toán tinh chỉnh kiến thức (Knowledge Refinement):** Nếu tài liệu là _Correct_ hoặc _Ambiguous_, hệ thống dùng chiến lược phân rã - tái tổ hợp (decompose-then-recompose) để chia nhỏ văn bản, lọc bỏ thông tin nhiễu và chỉ giữ lại các "dải kiến thức" (knowledge strips) cốt lõi.
3.  **Bổ sung bằng Web Search (Tìm kiếm Web):** Nếu tài liệu bị đánh giá là _Incorrect_ (hoặc _Ambiguous_), hệ thống sẽ bỏ qua/bổ sung tài liệu gốc và tự động sinh truy vấn từ khóa để tìm kiếm thông tin trên Web (sử dụng API), giúp vượt qua giới hạn của tập dữ liệu tĩnh.

## Dataset

**Bài báo dùng dữ liệu gì?**
Bài báo đánh giá mô hình trên **4 bộ dữ liệu** đại diện cho các tác vụ sinh văn bản khác nhau:

1.  **PopQA:** Câu hỏi ngắn về các thực thể hiếm (short-form generation).
2.  **Biography:** Sinh văn bản tiểu sử dài (long-form generation).
3.  **PubHealth:** Tác vụ xác minh thông tin y tế đúng/sai.
4.  **Arc-Challenge:** Câu hỏi trắc nghiệm khoa học thường thức.

## Evaluation

**Bài báo đánh giá bằng metric nào?**

- **Accuracy (Độ chính xác):** Sử dụng cho 3 bộ dữ liệu PopQA, PubHealth, và Arc-Challenge.
- **FactScore:** Sử dụng để đánh giá mức độ chính xác về mặt sự thật của các văn bản dài sinh ra trong bộ dữ liệu Biography.

## Results

**Kết quả chính là gì?**

- **CRAG cải thiện đáng kể hiệu suất** của các phương pháp nền tảng như RAG tiêu chuẩn và Self-RAG tiên tiến nhất. Khi kết hợp CRAG với mô hình SelfRAG-LLaMA2-7b, hệ thống đã **tăng 7.0% Accuracy trên PopQA, 14.9% FactScore trên Biography, 36.6% trên PubHealth và 15.4% trên Arc-Challenge** so với RAG thông thường.
- Bộ đánh giá truy xuất (Retrieval Evaluator) dựa trên T5 cực kỳ nhẹ nhưng có **độ chính xác (84.3%) vượt trội so với ChatGPT (58.0%)** trong việc đánh giá chất lượng tài liệu.
- CRAG chứng minh được tính linh hoạt, chi phí tính toán thấp và có thể mở rộng (generalizability) tốt trên nhiều tác vụ tạo văn bản khác nhau.

## Limitations

**Hạn chế của bài báo là gì?**

- Hệ thống bắt buộc phải **huấn luyện tinh chỉnh (fine-tune) một bộ đánh giá truy xuất bên ngoài** (external retrieval evaluator) dựa trên T5, điều này làm tăng một bước thiết lập mô hình. Tác giả định hướng tương lai sẽ tìm cách loại bỏ bộ đánh giá ngoài này và trang bị luôn khả năng tự đánh giá cho bản thân LLM.
- Trên một số mô hình ngôn ngữ cụ thể như LLaMA2-hf-7b, khả năng đọc hiểu chỉ dẫn (instruction comprehension) khá yếu đối với các dạng câu hỏi đóng (ví dụ: trả lời True/False cho PubHealth), làm giảm độ chính xác tổng thể.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này chính là **cơ sở lý thuyết cốt lõi cho luồng xử lý "Corrective RAG"** mà nhóm đang trực tiếp triển khai trong dự án AI Study Hub.
Cụ thể, nền tảng AI Study Hub của nhóm cho phép sinh viên tải tài liệu học tập lên và đặt câu hỏi, sử dụng RAG pipeline được chia thành hai chế độ: Basic RAG và Corrective RAG. Bài báo đã cung cấp kiến trúc chuẩn mực để nhóm xây dựng các tính năng cho chế độ Corrective RAG, bao gồm: đánh giá độ liên quan của các đoạn văn bản (filtering chunks by relevance), viết lại câu hỏi (query rewriting), và sử dụng luồng truy xuất dự phòng (fallback retrieval) khi tài liệu ban đầu không đáp ứng đủ thông tin. Bên cạnh đó, định hướng của bài báo về việc đánh giá chất lượng RAG cũng hoàn toàn khớp với module Benchmarking mà nhóm đang xây dựng để so sánh điểm số tính chính xác (correctness) và độ trung thực (faithfulness) giữa 2 mode RAG.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**
Dựa vào kiến trúc hiện tại của AI Study Hub và các phương pháp trong bài báo, nhóm có thể thực hiện các cải tiến sau:

1. **Sử dụng mô hình Evaluator nội bộ, gọn nhẹ để giảm phụ thuộc API:** Hiện tại, backend của nhóm đang phụ thuộc khá nhiều vào Groq SDK để thực hiện việc sinh câu trả lời, viết lại câu hỏi và cả đánh giá (evaluation). Bài báo chứng minh rằng bộ đánh giá truy xuất (Retrieval Evaluator) chỉ cần một mô hình rất nhỏ (ví dụ T5-large với 0.77B tham số) là đã có thể đánh giá tài liệu chính xác hơn cả ChatGPT. Nhóm có thể triển khai một mô hình nhỏ gọn cục bộ cho bước "lọc chunk" để giảm chi phí gọi API Groq và tăng tốc độ phản hồi (response time).
2. **Mở rộng cơ sở dữ liệu dự phòng bằng Web Search API:** Trong AI Study Hub, tài liệu đang bị giới hạn bởi các file (PDF, DOCX...) do sinh viên tự tải lên vào thư viện. Theo cơ chế hành động _Incorrect_ của bài báo, hệ thống nên tìm kiếm thêm thông tin bên ngoài nếu tài liệu nội bộ không liên quan. Nhóm có thể tích hợp Google Search API hoặc Wikipedia API vào bước fallback; nếu tài liệu sinh viên thiếu thông tin, AI Study Hub sẽ tự tìm kiếm trên web để bổ sung ngữ cảnh thay vì chỉ trả lời không biết.
3. **Phân tích hành vi RAG trên Admin Dashboard:** Hệ thống của nhóm đã có trang quản trị (Admin Dashboard) theo dõi hoạt động và lưu trữ lịch sử đánh giá chi tiết của RAG. Nhóm có thể cải tiến bằng cách ghi nhận trực tiếp 3 trạng thái kích hoạt mà bài báo đề xuất (_Correct, Incorrect, Ambiguous_) vào MongoDB. Từ đó, admin có thể theo dõi tỷ lệ phần trăm các câu hỏi cần đến fallback retrieval, giúp đánh giá xem sinh viên có đang đặt câu hỏi nằm ngoài phạm vi tài liệu đã upload hay không.
