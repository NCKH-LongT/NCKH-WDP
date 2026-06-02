# Paper 01 Summary

- **Tên bài:** Enhancing textual textbook question answering with large language models and retrieval augmented generation.
- **Tác giả:** Hessa A. Alawwad, Areej Alhothali, Usman Naseem, Ali Alkhathlan, Amani Jamal.
- **Năm:** 2025.
- **Nguồn:** Tạp chí Pattern Recognition (Elsevier). Các tác giả đến từ King Abdulaziz University, Imam Mohammad Ibn Saud Islamic University (Ả Rập Xê Út) và Macquarie University (Úc).
- **DOI/Link:** 10.1016/j.patcog.2024.111332. Mã nguồn: https://github.com/hessaAlawwad/PLR-TQA.

## Problem

**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết những thách thức trong bài toán **Hỏi đáp trên Sách giáo khoa (Textbook Question Answering - TQA)**. Cụ thể, hệ thống phải đối mặt với các ngữ cảnh văn bản rất dài (trung bình 1800 từ, hơn 50 câu mỗi bài học) và đòi hỏi khả năng suy luận phức tạp. Đặc biệt, bài báo nhấn mạnh vào việc giải quyết bài toán **"out-of-domain"** (ngoài miền) - tức là khi các khái niệm để trả lời một câu hỏi không nằm gọn trong một bài học mà nằm rải rác ở nhiều bài học khác nhau. Các mô hình ngôn ngữ lớn (LLMs) truyền thống thường gặp khó khăn trong việc nắm bắt toàn bộ ngữ cảnh dài này và dễ sinh ra "ảo giác" khi thiếu thông tin.

## Method

**Bài báo dùng phương pháp/model/hệ thống nào?**
Bài báo đề xuất khung hệ thống **PLRTQA**, kết hợp sức mạnh của **RAG** và mô hình **LLaMA-2** được tinh chỉnh.

1.  **Retrieval-Augmented Generation (RAG):** Hệ thống dùng mô hình `text-embedding-ada-002` của OpenAI để chuyển đổi nội dung sách giáo khoa thành vector và lưu vào cơ sở dữ liệu vector Pinecone. Khi có câu hỏi, RAG sẽ truy xuất các đoạn văn bản (chunks) liên quan nhất bằng độ tương đồng tích vô hướng (dot-product).
2.  **Fine-tuning LLaMA-2 bằng PEFT/LoRA:** Để tăng cường khả năng suy luận, mô hình LLaMA-2 được tinh chỉnh tham số hiệu quả (PEFT) thông qua kỹ thuật LoRA, giúp mô hình học cách trả lời dựa trên ngữ cảnh được truy xuất mà không bị quên kiến thức cũ. Hệ thống cũng thử nghiệm tích hợp thêm bộ lọc Cohere re-ranker để sắp xếp lại tài liệu.

## Dataset

**Bài báo dùng dữ liệu gì?**
Bài báo sử dụng bộ dữ liệu **TQA (CK12-QA)** gồm 1076 bài học thuộc các lĩnh vực khoa học sự sống, khoa học trái đất và vật lý. Do tập trung vào văn bản, nghiên cứu đã loại bỏ các câu hỏi chứa hình ảnh, chỉ sử dụng tổng cộng **13.693 câu hỏi phi biểu đồ (non-diagram questions)**, bao gồm định dạng Trắc nghiệm (Multiple-choice) và Đúng/Sai (True/False).

## Evaluation

**Bài báo đánh giá bằng metric nào?**
Bài báo đánh giá bằng thước đo **Accuracy (Độ chính xác)** trên các tập validation và test, phân chia chi tiết cho từng loại câu hỏi (T/F và MC).

## Results

**Kết quả chính là gì?**

- **Vượt qua các mô hình SOTA:** Hệ thống PLRTQA đạt độ chính xác tổng thể **84.24%** trên tập test, vượt qua mô hình nền tảng tốt nhất trước đó (MRHF).
- **Giải quyết triệt để "out-of-domain":** Phân tích cho thấy chỉ có 44% câu hỏi có thể lấy câu trả lời từ chính bài học chứa câu hỏi đó. Việc tích hợp RAG giúp hệ thống truy xuất và tổng hợp được ngữ cảnh từ các bài học khác, giải quyết hiệu quả sự phân tán kiến thức.
- **Nghịch lý của Re-ranker:** Một phát hiện thú vị từ phân tích loại bỏ (Ablation study) là khi sử dụng thêm bộ sắp xếp lại (Re-ranker), độ chính xác trên tập test lại **giảm** từ 83.80% xuống còn 79.22%, do bộ lọc vô tình đưa vào các chủ đề không liên quan gây phân tâm cho mô hình.

## Limitations

**Hạn chế của bài báo là gì?**

- **Bỏ qua dữ liệu đa phương thức:** Bài báo chỉ tập trung giải quyết phần văn bản (textual TQA) mà cố tình bỏ qua các thông tin trực quan cốt lõi của sách giáo khoa như biểu đồ, hình ảnh (visual components).
- **Hạn chế của Re-ranker:** Thuật toán re-ranking hiện tại chưa tối ưu, dẫn đến việc lấy nhầm thông tin gây nhiễu cho bước sinh văn bản.
- Trong một số trường hợp, RAG vẫn truy xuất những đoạn văn bản không khớp với trọng tâm câu hỏi (ví dụ: tập trung nhầm vào yếu tố con người thay vì động đất), khiến LLM bị "đánh lừa" và dự đoán sai.

## Relevance to our topic

**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này phục vụ cực kỳ tốt cho khía cạnh **Domain Ứng dụng (Giáo dục/Học tập)** của hệ thống quản lý. Nó làm rõ hoàn toàn bối cảnh mà dự án **AI Study Hub** trong file `REPORT.md` đang cố gắng giải quyết:
Tính năng _Document Library_ cho phép sinh viên tải lên nhiều file bài giảng, giáo trình. Bài báo đã chỉ ra một rào cản lớn trong "Domain giáo dục" là kiến thức không bao giờ nằm độc lập trong một file/bài học, mà mang tính liên đới (out-of-domain). Kiến trúc của bài báo sử dụng chính xác các công nghệ mà AI Study Hub đang triển khai: dùng mô hình Embedding, lưu vào **Pinecone vector database**, và gọi LLM để sinh câu trả lời. Bài báo cung cấp minh chứng khoa học vững chắc rằng việc kết hợp bộ nhớ từ vector database và LLM có thể thay thế giáo viên trong việc kết nối kiến thức rời rạc thành một câu trả lời hoàn chỉnh.

## Possible improvement

**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**

1.  **Cấu hình Truy xuất Xuyên Tài liệu (Cross-Document Retrieval):** AI Study Hub đang lưu trữ trường `subject` (môn học) trong mô hình `Document`. Để giải quyết bài toán "out-of-domain" được bài báo nêu ra, luồng RAG của nhóm có thể cho phép người dùng tùy chọn: tìm câu trả lời giới hạn trong file đang mở, hay tìm kiếm toàn cục trên **tất cả các file có cùng `subject`**. Backend sẽ dùng filter meta-data trên Pinecone để hiện thực hóa điều này, giúp AI giải quyết được các câu hỏi ôn tập cuối kỳ mang tính tổng hợp cao.
2.  **Đánh giá cẩn trọng tính năng Re-ranking trong Corrective RAG:** Bài báo phát hiện rằng việc dùng thêm Re-ranker có thể làm giảm hiệu suất sinh văn bản. Trong chế độ `Corrective RAG` của nhóm, hệ thống đang dùng LLM để lọc các chunk liên quan (_filters chunks by relevance_). Nhóm nên sử dụng các API `Benchmark routes` sẵn có để đối chiếu chéo (A/B testing) xem khâu lọc/re-rank này có thực sự làm tăng `relevance score` và `correctness` so với `Basic RAG` hay không, tránh đi vào "vết xe đổ" giảm độ chính xác như nghiên cứu này.
3.  **Bổ sung OCR để giải quyết điểm yếu Đa phương thức:** Bài báo thừa nhận hạn chế lớn nhất là chưa xử lý được biểu đồ, hình ảnh trong sách. Báo cáo `REPORT.md` cho thấy hệ thống hiện tại cũng chỉ _extracted text_ (trích xuất văn bản) từ các file. Nhóm có thể biến đây thành một điểm cải tiến mạnh mẽ bằng cách tích hợp API OCR hoặc dùng trực tiếp tính năng Vision của Groq SDK (nếu có) để quét biểu đồ trong bài giảng, vượt qua giới hạn của nghiên cứu TQA tiêu chuẩn này.
