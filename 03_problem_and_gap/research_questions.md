# Research Questions (Câu hỏi nghiên cứu)

## RQ1: Đánh giá hiệu quả giảm thiểu ảo giác của luồng Corrective RAG so với Basic RAG trong hệ thống AI Study Hub

### 1. Bối cảnh & Lý do (Context & Motivation)

Trong hệ thống AI Study Hub, sinh viên sẽ tải lên các tài liệu học tập cá nhân đa dạng (PDF, DOCX, PPTX) để truy vấn. Tuy nhiên, các mô hình ngôn ngữ lớn (LLM) như Groq SDK thường gặp hiện tượng ảo giác (hallucinations) khi chỉ dựa vào kiến thức tham số hoặc khi hệ thống truy xuất (retriever) trả về các tài liệu không liên quan. Để giải quyết vấn đề này, AI Study Hub đã thiết kế hai chế độ: Basic RAG (truy xuất ngữ nghĩa cơ bản) và Corrective RAG (tích hợp viết lại câu hỏi, lọc các đoạn văn bản theo độ liên quan, và kiểm tra mức độ bám sát tài liệu). Việc nghiên cứu câu hỏi này là cần thiết để chứng minh tính ưu việt của kiến trúc Corrective RAG (được lấy cảm hứng từ khung CRAG) trong việc cải thiện độ tin cậy của câu trả lời so với RAG truyền thống.

### 2. Phương pháp đánh giá (Evaluation Methodology)

Sử dụng phương pháp **A/B Testing** thông qua module **RAG Evaluation and Benchmarking** đã được tích hợp sẵn trong backend của AI Study Hub.

- **Tập dữ liệu:** Xây dựng một tập hợp các câu hỏi chuẩn (Benchmark questions) dựa trên các tài liệu đã tải lên.
- **Thực nghiệm:** Chạy song song cả hai luồng Basic RAG và Corrective RAG trên cùng một tập câu hỏi thông qua các API `Benchmark routes` (`/api/benchmarks`).
- **Thu thập dữ liệu:** Hệ thống sẽ tự động lưu trữ log đánh giá vào MongoDB cho mỗi câu trả lời sinh ra.

### 3. Metric đo lường (Metrics)

Sử dụng các metric tự động do AI Study Hub cung cấp trong module Evaluation:

- **Faithfulness (Độ trung thực) / Grounding result:** Đánh giá xem câu trả lời có hoàn toàn dựa trên `source chunks` được truy xuất hay không.
- **Correctness (Độ chính xác):** Đánh giá tính đúng đắn của câu trả lời so với đáp án kỳ vọng.
- **Relevance score:** Điểm số đánh giá mức độ liên quan của câu trả lời đối với câu hỏi gốc.

---

## RQ2: Tác động của cơ chế "Lọc đoạn văn bản theo độ liên quan" (Chunk Filtering) đến độ trễ và chất lượng truy xuất

### 1. Bối cảnh & Lý do (Context & Motivation)

Hệ thống RAG thường truy xuất một lượng lớn tài liệu và nhồi tất cả vào LLM để sinh câu trả lời, điều này không chỉ đưa vào các thông tin rác (redundant information) làm giảm chất lượng sinh văn bản mà còn làm tăng thời gian xử lý và chi phí API. Dự án AI Study Hub đã ứng dụng kỹ thuật "filters chunks by relevance" (lọc các đoạn văn bản theo độ liên quan) trong luồng Corrective RAG. Lấy cảm hứng từ lý thuyết của mạng phân loại nhẹ trong DR-RAG, cần nghiên cứu xem khâu lọc này có thực sự giúp hệ thống loại bỏ độ nhiễu mà không làm tăng quá mức thời gian chờ (response time) của sinh viên hay không.

### 2. Phương pháp đánh giá (Evaluation Methodology)

Thực hiện **Nghiên cứu cắt bỏ (Ablation Study)** trên môi trường triển khai thực tế.

- **Thiết lập:** So sánh hai cấu hình của hệ thống: (1) Đưa toàn bộ K chunk truy xuất từ Pinecone vào Groq SDK để sinh câu trả lời. (2) Chạy qua luồng lọc chunk để loại bỏ các chunk rác trước khi đưa vào Groq SDK.
- **Đo lường:** Theo dõi và trích xuất dữ liệu từ bảng `Chat History` trong MongoDB, nơi lưu trữ siêu dữ liệu đánh giá (evaluation metadata) của hệ thống.

### 3. Metric đo lường (Metrics)

- **Response time (Thời gian phản hồi):** Đo lường tổng thời gian từ khi sinh viên đặt câu hỏi đến khi hệ thống trả về câu trả lời hoàn chỉnh.
- **Redundancy Ratio (Tỷ lệ nhiễu):** Tính toán dựa trên việc so sánh `retrieved_chunk_count` (số chunk lấy từ Pinecone) và `relevant_chunk_count` (số chunk thực sự hữu ích sau khi lọc).
- **Completeness (Độ hoàn thiện):** Đảm bảo việc lọc chunk không làm mất đi các ý quan trọng của câu trả lời.

---

## RQ3: Mức độ tin cậy (Robustness) của AI Study Hub khi đối mặt với sự mâu thuẫn kiến thức (Knowledge Shifts) trong học liệu

### 1. Bối cảnh & Lý do (Context & Motivation)

Trong môi trường giáo dục đại học, các bài giảng do sinh viên tải lên (slide, ghi chép) thường chứa các quy ước, số liệu hoặc định nghĩa đặc thù của giảng viên, có thể khác biệt hoặc mâu thuẫn với kiến thức nội tại (parametric knowledge) mà LLM đã được học trước đó. Các nghiên cứu (như KNOWSHIFTQA) chỉ ra rằng hiệu suất của RAG có thể giảm tới 27% khi đối mặt với sự mâu thuẫn này do LLM có xu hướng thiên vị kiến thức cũ. Cần đánh giá xem luồng RAG của AI Study Hub có khả năng vượt qua "sức ỳ" của LLM để trả lời trung thành theo đúng file tài liệu của sinh viên hay không.

### 2. Phương pháp đánh giá (Evaluation Methodology)

Áp dụng phương pháp **Cập nhật tri thức giả định (Hypothetical Knowledge Update)**.

- **Tạo bộ dữ liệu:** Tạo ra các file tài liệu giả lập (.txt hoặc .docx) trong đó chủ động thay đổi một vài sự thật hoặc công thức quen thuộc thành một thông tin khác hợp lý nhưng sai thực tế phổ thông (Ví dụ: Đổi "Nước sôi ở 100 độ C" thành "Nước sôi ở 120 độ C"). Tải các file này lên tính năng `Document Library` của AI Study Hub.
- **Kiểm thử:** Đặt câu hỏi trực tiếp trên giao diện `/aichatbox` yêu cầu AI trả lời dựa trên file vừa tải lên. Đánh giá xem hệ thống trả lời theo đáp án 100 độ (kiến thức nội tại của LLM) hay 120 độ (kiến thức trong file).

### 3. Metric đo lường (Metrics)

- **Accuracy (Độ chính xác theo tài liệu):** Tỷ lệ phần trăm LLM trả lời đúng theo thông tin đã bị thay đổi trong tài liệu.
- **Grounding result:** Kiểm tra xem hệ thống có cung cấp đúng nguồn trích dẫn (`source chunks`) từ file tài liệu giả định hay không.

---

## RQ4: Đánh giá hiệu quả của Code Interpreter trong việc giải quyết các bài tập tính toán và suy luận logic đa bước

### 1. Bối cảnh & Lý do (Context & Motivation)

Tài liệu học tập mà sinh viên đưa lên AI Study Hub bao gồm cả các tệp tính toán như XLSX (Excel). Các mô hình ngôn ngữ lớn thường rất yếu trong việc thực hiện các phép tính toán học phức tạp hoặc suy luận logic đa bước, dẫn đến việc "bịa" ra kết quả sai. Giải pháp tích hợp LLM Code Interpreter (Trình thông dịch mã Python) kết hợp với RAG đã được chứng minh là tăng độ chính xác từ 10-15% cho các câu hỏi dạng này. Mặc dù hiện tại kiến trúc backend chưa ghi nhận Code Interpreter, nhưng đây là một hướng nghiên cứu cực kỳ tiềm năng để nâng cấp luồng xử lý câu hỏi đối với file XLSX.

### 2. Phương pháp đánh giá (Evaluation Methodology)

So sánh đối chứng giữa **LLM + RAG thuần túy** và **LLM + RAG + Code Interpreter**.

- **Tích hợp Sandbox:** Xây dựng thêm một dịch vụ thực thi mã Python độc lập (Python Sandbox) ở backend. Khi Groq SDK nhận diện câu hỏi cần tính toán, nó sẽ sinh code Python, đẩy sang Sandbox thực thi để lấy kết quả.
- **Tập dữ liệu:** Sử dụng các file XLSX thực tế của sinh viên hoặc các bộ dữ liệu trắc nghiệm khoa học/toán học (như ScienceQA hoặc ARC-Challenge).
- **Thực nghiệm:** Chạy các truy vấn yêu cầu thống kê số liệu, tính toán phức tạp trên cả hai hệ thống và ghi nhận kết quả.

### 3. Metric đo lường (Metrics)

- **Calculation Accuracy (Độ chính xác tính toán):** Tỷ lệ các bài toán đưa ra được con số/kết quả cuối cùng chính xác hoàn toàn.
- **Execution Success Rate (Tỷ lệ thực thi thành công):** Số lần Code Interpreter chạy code thành công mà không gặp lỗi cú pháp (Syntax errors) hay lỗi logic.
- **Explanation Quality / Traceability:** Đánh giá định tính xem hệ thống có hiển thị minh bạch các bước giải (code execution logs) trên giao diện Assistant-UI cho sinh viên hiểu hay không.
