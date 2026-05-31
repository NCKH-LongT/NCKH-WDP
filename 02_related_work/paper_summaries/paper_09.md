# Paper 09 Summary

## Citation

Tên bài:  
How to Build an AI Tutor that Can Adapt to Any Course and Provide Accurate Answers Using Retrieval-Augmented Generation

Tác giả:  
Haritz Puerto, Gorkem Ozdemir, Imanol Schlag, Ethan Perez và cộng sự

Năm:  
2023

Nguồn:  
arXiv / Hugging Face Papers

DOI/Link:  
https://arxiv.org/abs/2311.17696

---

## Problem

Bài báo giải quyết vấn đề gì?

Các AI Chatbot hiện nay như:

- ChatGPT
- Gemini
- Claude

có thể trả lời nhiều câu hỏi khác nhau nhưng gặp khó khăn trong môi trường giáo dục vì:

### 1. Thiếu kiến thức môn học cụ thể

Ví dụ:

```text
Môn DBI202 của FPT
Môn PRM392
Môn SWP391
```

LLM không được huấn luyện trên các tài liệu nội bộ này.

Do đó:

- Trả lời thiếu chính xác.
- Không bám sát giáo trình.
- Không theo đúng yêu cầu của giảng viên.

---

### 2. Hallucination

Khi không biết câu trả lời:

LLM vẫn cố gắng trả lời.

Điều này dẫn đến:

```text
Hallucination
```

và có thể khiến sinh viên học sai kiến thức.

---

### 3. Khó mở rộng cho nhiều môn học

Thông thường:

```text
Một AI Tutor
=
Một môn học
```

Muốn hỗ trợ môn mới phải:

- Fine-tune lại.
- Thu thập dữ liệu mới.
- Huấn luyện lại mô hình.

Chi phí rất cao.

---

Bài báo đặt mục tiêu:

> Xây dựng một AI Tutor có thể thích ứng với bất kỳ môn học nào chỉ bằng cách cung cấp tài liệu môn học mà không cần huấn luyện lại mô hình.

---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Tác giả đề xuất:

# Course-Adaptive AI Tutor

dựa trên:

```text
RAG
+
LLM
```

---

### Bước 1: Upload Course Materials

Giảng viên cung cấp:

```text
Lecture Notes
Slides
PDF
Textbooks
Assignments
```

---

### Bước 2: Knowledge Indexing

Tài liệu được:

```text
Chunking
↓
Embedding
↓
Vector Database
```

---

### Bước 3: Retrieval

Khi sinh viên hỏi:

```text
Question
↓
Retriever
↓
Relevant Chunks
```

---

### Bước 4: Grounded Generation

LLM nhận:

```text
Question
+
Retrieved Chunks
```

↓

```text
Answer
```

---

### Điểm đặc biệt

Hệ thống không cần:

```text
Fine-tuning
```

cho từng môn học.

Chỉ cần:

```text
Upload tài liệu mới
```

là AI Tutor có thể hỗ trợ môn học đó.

---

### Adaptive Course Support

Ví dụ:

```text
Course A
→ Database Systems

Course B
→ Machine Learning

Course C
→ Software Engineering
```

Cùng một AI Tutor có thể hỗ trợ tất cả.

---

## Dataset

Bài báo dùng dữ liệu gì?

Nghiên cứu sử dụng:

### Course Materials

Bao gồm:

- Lecture Slides
- Textbooks
- Assignments
- Course Notes

---

Các câu hỏi được tạo từ:

```text
Student Questions
```

trong môi trường học tập thực tế.

---

Bài toán tập trung vào:

- Course-specific QA
- Educational Retrieval
- Grounded Learning Support

---

## Evaluation

Bài báo đánh giá bằng metric nào?

### Answer Accuracy

Đánh giá:

```text
Answer Correctness
```

---

### Grounding Quality

Đánh giá:

```text
Answer
```

có dựa trên tài liệu môn học hay không.

---

### Retrieval Quality

Đánh giá:

```text
Retrieved Context
```

có liên quan đến câu hỏi hay không.

---

### Human Evaluation

Giảng viên và người học đánh giá:

- Correctness
- Relevance
- Educational Usefulness

---

## Results

Kết quả chính là gì?

### Accurate Course-Specific Answers

AI Tutor trả lời chính xác hơn đáng kể so với:

```text
LLM Only
```

đối với các câu hỏi liên quan đến môn học cụ thể.

---

### Reduced Hallucination

Do sử dụng:

```text
Retrieved Course Materials
```

nên câu trả lời:

- Có căn cứ.
- Có nguồn tham khảo.
- Ít bịa thông tin hơn.

---

### Course Adaptability

Hệ thống có thể:

```text
Support New Course
```

chỉ bằng cách:

```text
Upload New Documents
```

không cần huấn luyện lại.

---

### Main Conclusion

Tác giả kết luận rằng:

> Retrieval-Augmented Generation là hướng tiếp cận hiệu quả để xây dựng AI Tutor có khả năng thích ứng với nhiều môn học khác nhau và cung cấp câu trả lời chính xác dựa trên tài liệu học tập.

---

## Limitations

Hạn chế của bài báo là gì?

### 1. Phụ thuộc Retrieval

Nếu:

```text
Retrieve Wrong Chunks
```

thì chất lượng câu trả lời sẽ giảm.

---

### 2. Chưa hỗ trợ Multi-hop Reasoning mạnh

Các câu hỏi yêu cầu:

```text
Nhiều bước suy luận
```

vẫn là thách thức.

---

### 3. Chưa có Self-Evaluation

Hệ thống:

```text
Retrieve
→ Generate
```

chưa có:

```text
Self-Critique
```

như Self-RAG.

---

### 4. Chưa cá nhân hóa người học

AI Tutor trả lời giống nhau cho mọi sinh viên.

Chưa xem xét:

- Trình độ hiện tại.
- Lịch sử học tập.
- Điểm mạnh/yếu.

---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Cực kỳ cao (Directly Related Paper)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Thực tế kiến trúc trong bài báo gần như giống AI Study Hub.

---

### AI Tutor Paper

```text
Course Materials
↓
Embedding
↓
Retriever
↓
LLM
↓
Answer
```

---

### AI Study Hub

```text
PDF
↓
Chunking
↓
Embedding
↓
Pinecone
↓
RAG
↓
Answer
```

---

Paper này là bằng chứng học thuật mạnh để chứng minh:

> Việc sử dụng RAG trong môi trường học tập là khả thi và mang lại hiệu quả cao hơn so với chatbot AI thông thường.

---

Đây là một trong những paper gần với AI Study Hub nhất trong toàn bộ Literature Review.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Kết hợp DR-RAG

Pipeline:

```text
Question
↓
Retrieve
↓
Dynamic Retrieval
↓
Answer
```

giúp xử lý các câu hỏi cần nhiều nguồn thông tin.

---

### 2. Kết hợp CRAG

Thêm:

```text
Retrieval Evaluation
```

để giảm retrieve sai chunk.

---

### 3. Kết hợp Self-RAG

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

### 4. Personalized Learning Assistant

Theo dõi:

```text
Student Progress
```

để:

- Gợi ý tài liệu phù hợp.
- Tạo quiz cá nhân hóa.
- Đề xuất lộ trình học tập.

---

### 5. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
ChatGPT Only
vs
Basic RAG
vs
AI Study Hub
```

trên tập tài liệu học tập thực tế.

Đánh giá:

- Accuracy
- Recall
- Hallucination Rate
- Student Satisfaction
- Response Time

để chứng minh AI Study Hub hiệu quả hơn chatbot AI tổng quát trong môi trường giáo dục.