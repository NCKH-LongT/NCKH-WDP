# Paper 08 Summary

## Citation

Tên bài:  
A Novel Framework for Educational Q&A: Leveraging RAG and LLM Code Interpreters

Tác giả:  
Nhiều tác giả (PMC Open Access Publication)

Năm:  
2024

Nguồn:  
PubMed Central (PMC)

DOI/Link:  
https://pmc.ncbi.nlm.nih.gov/articles/PMC12668533/

---

## Problem

Bài báo giải quyết vấn đề gì?

Các hệ thống học tập sử dụng Large Language Models (LLMs) đang ngày càng phổ biến trong giáo dục. Tuy nhiên, các hệ thống này vẫn tồn tại nhiều hạn chế:

### 1. Hallucination

LLM có thể tạo ra thông tin:

- Không tồn tại trong tài liệu học tập.
- Không chính xác.
- Không có nguồn tham chiếu.

Điều này gây nguy hiểm trong môi trường giáo dục vì sinh viên có thể học sai kiến thức.

---

### 2. Thiếu khả năng truy xuất tri thức chuyên biệt

Các mô hình như:

- ChatGPT
- Gemini
- Claude

được huấn luyện trên dữ liệu tổng quát.

Do đó khó trả lời chính xác các câu hỏi liên quan đến:

- Môn học cụ thể.
- Giáo trình riêng.
- Slide bài giảng.
- Tài liệu nội bộ của trường.

---

### 3. Khó xử lý các câu hỏi yêu cầu suy luận

Ví dụ:

```text
Từ công thức A và định nghĩa B,
hãy giải thích tại sao kết quả C xảy ra?
```

Những câu hỏi dạng này yêu cầu:

- Truy xuất kiến thức.
- Suy luận logic.
- Thực hiện tính toán.

LLM truyền thống thường gặp khó khăn.

---

Bài báo hướng tới mục tiêu:

> Xây dựng một hệ thống hỏi đáp học tập có khả năng truy xuất tri thức từ tài liệu học tập và thực hiện suy luận chính xác bằng cách kết hợp Retrieval-Augmented Generation (RAG) với Code Interpreter.

---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Tác giả đề xuất framework:

# Educational RAG Framework

Kết hợp:

```text
RAG
+
LLM
+
Code Interpreter
```

---

### Thành phần 1: Knowledge Retrieval

Tài liệu học tập được:

```text
PDF
Slides
Textbooks
Lecture Notes
```

↓

```text
Chunking
```

↓

```text
Embedding
```

↓

```text
Vector Database
```

↓

```text
Semantic Retrieval
```

Khi sinh viên đặt câu hỏi:

```text
Question
↓
Retriever
↓
Relevant Chunks
```

---

### Thành phần 2: LLM Answer Generation

Sau khi retrieve:

```text
Question
+
Relevant Documents
```

↓

```text
LLM
```

↓

```text
Answer
```

---

### Thành phần 3: Code Interpreter

Điểm mới của nghiên cứu là:

# Code Interpreter Integration

Cho phép hệ thống:

- Thực hiện tính toán.
- Chạy mã Python.
- Giải bài toán số học.
- Hỗ trợ STEM Education.

Ví dụ:

```text
Question
↓
Need Calculation?
↓
Code Interpreter
↓
Result
↓
Final Answer
```

Điều này giúp cải thiện khả năng suy luận của hệ thống.

---

## Dataset

Bài báo dùng dữ liệu gì?

Nghiên cứu sử dụng:

### Educational Materials

Bao gồm:

- Giáo trình.
- Lecture Notes.
- PDF học tập.
- Course Materials.

---

Các câu hỏi được xây dựng dựa trên:

```text
Educational Question Answering
```

trong nhiều lĩnh vực học thuật khác nhau.

Mục tiêu là đánh giá khả năng:

- Truy xuất kiến thức.
- Giải thích khái niệm.
- Suy luận.
- Tính toán.

trong môi trường giáo dục thực tế.

---

## Evaluation

Bài báo đánh giá bằng metric nào?

### Answer Accuracy

Đánh giá độ chính xác của câu trả lời.

---

### Retrieval Effectiveness

Đánh giá:

```text
Question
↓
Retrieved Context
```

có phù hợp hay không.

---

### Reasoning Capability

Đánh giá khả năng:

- Suy luận.
- Tính toán.
- Giải thích.

---

### Educational Quality

Đánh giá bởi chuyên gia giáo dục dựa trên:

- Correctness.
- Relevance.
- Completeness.

---

## Results

Kết quả chính là gì?

Nghiên cứu cho thấy việc kết hợp:

```text
RAG
+
Code Interpreter
```

mang lại hiệu quả tốt hơn so với chỉ sử dụng LLM đơn thuần.

---

### Cải thiện độ chính xác

Hệ thống trả lời chính xác hơn đối với:

- Câu hỏi học thuật.
- Câu hỏi từ tài liệu môn học.
- Câu hỏi cần dẫn chứng từ tài liệu.

---

### Giảm Hallucination

Nhờ sử dụng:

```text
Retrieved Context
```

các câu trả lời bám sát nội dung tài liệu hơn.

---

### Tăng khả năng suy luận

Code Interpreter giúp xử lý:

- Công thức.
- Phép tính.
- Các bài toán học thuật.

mà LLM truyền thống thường gặp khó khăn.

---

### Kết luận chính

Tác giả kết luận rằng:

> Việc kết hợp Retrieval-Augmented Generation với Code Interpreter tạo ra một nền tảng học tập thông minh có khả năng cung cấp câu trả lời chính xác, có căn cứ và phù hợp với môi trường giáo dục.

---

## Limitations

Hạn chế của bài báo là gì?

### 1. Phụ thuộc chất lượng Retrieval

Nếu:

```text
Retrieved Documents
```

không chính xác thì chất lượng câu trả lời vẫn giảm.

---

### 2. Tăng độ phức tạp hệ thống

Framework gồm:

```text
Retriever
+
LLM
+
Code Interpreter
```

nên khó triển khai hơn chatbot thông thường.

---

### 3. Chưa đánh giá trên quy mô lớn

Nghiên cứu chủ yếu đánh giá trên môi trường học tập thử nghiệm.

Chưa kiểm chứng trên:

- Hàng nghìn môn học.
- Hàng triệu tài liệu.
- Quy mô đại học lớn.

---

### 4. Chi phí tính toán cao hơn

Code Interpreter làm tăng:

- Latency.
- Compute Cost.
- Resource Consumption.

---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Cực kỳ cao (Domain-Specific Educational Paper)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Khác với DPR, RAG hay Self-RAG là các paper nền tảng tổng quát, paper này tập trung trực tiếp vào:

```text
Educational Question Answering
```

chính là bài toán mà AI Study Hub đang giải quyết.

---

Điểm tương đồng:

### AI Study Hub

```text
Student
↓
Upload PDF
↓
Embedding
↓
Pinecone
↓
RAG
↓
Answer
```

### Framework trong bài báo

```text
Student
↓
Educational Documents
↓
Retrieval
↓
LLM
↓
Answer
```

---

Paper này giúp chứng minh:

> Việc áp dụng RAG trong giáo dục là hướng nghiên cứu khả thi và có hiệu quả thực tế.

Đây là tài liệu rất phù hợp để đưa vào:

- Literature Review.
- Related Works.
- Motivation of Research.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Bổ sung Citation-Based Answering

Sau khi trả lời:

```text
Answer
+
Source Chunks
```

để sinh viên biết nguồn thông tin.

---

### 2. Kết hợp Self-RAG

Pipeline:

```text
Question
↓
Retrieve
↓
Generate
↓
Self-Evaluate
```

giúp giảm hallucination.

---

### 3. Hỗ trợ bài tập tính toán

Tích hợp:

```text
Python Interpreter
```

hoặc:

```text
Math Solver
```

cho các môn:

- Toán.
- Xác suất thống kê.
- Vật lý.
- Kinh tế.

---

### 4. Personalized Learning

Phân tích:

```text
Learning History
```

để:

- Gợi ý tài liệu.
- Đề xuất bài học tiếp theo.
- Tạo quiz tự động.

---

### 5. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
LLM Only
vs
Basic RAG
vs
Educational RAG
```

trên tập tài liệu học tập thực tế.

Đánh giá:

- Accuracy
- Recall
- Hallucination Rate
- Student Satisfaction
- Response Time

để chứng minh RAG phù hợp cho hệ thống hỗ trợ học tập thông minh.