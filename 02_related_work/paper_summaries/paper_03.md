# Paper 03 Summary

## Citation

Tên bài:  
Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks

Tác giả:  
Patrick Lewis, Ethan Perez, Aleksandra Piktus, Fabio Petroni, Vladimir Karpukhin, Naman Goyal, Heinrich Küttler, Mike Lewis, Wen-tau Yih, Tim Rocktäschel, Sebastian Riedel, Douwe Kiela

Năm:  
2020

Nguồn:  
NeurIPS 2020 (Conference on Neural Information Processing Systems)

DOI/Link:  
https://arxiv.org/abs/2005.11401

---

## Problem

Bài báo giải quyết vấn đề gì?

Các Large Language Models (LLMs) có khả năng lưu trữ kiến thức trong tham số của mô hình (parametric memory), tuy nhiên vẫn tồn tại nhiều hạn chế:

- Không dễ cập nhật kiến thức mới.
- Không thể giải thích rõ nguồn gốc thông tin được sử dụng để trả lời.
- Dễ sinh ra hallucination (bịa thông tin).
- Hiệu suất giảm trên các bài toán yêu cầu kiến thức thực tế (knowledge-intensive tasks).

Tác giả đặt ra vấn đề:

> Liệu có thể kết hợp khả năng sinh ngôn ngữ của mô hình sinh (Generator) với một hệ thống truy xuất tri thức bên ngoài (Retriever) để tạo ra câu trả lời chính xác và đáng tin cậy hơn hay không?

Bài báo hướng tới việc xây dựng một framework có khả năng:

- Truy xuất thông tin từ nguồn dữ liệu ngoài.
- Sinh câu trả lời dựa trên thông tin đã retrieve.
- Cập nhật tri thức mà không cần train lại toàn bộ mô hình.

:contentReference[oaicite:0]{index=0}

---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Tác giả đề xuất framework:

# RAG (Retrieval-Augmented Generation)

RAG kết hợp:

### Parametric Memory

Là kiến thức nằm trong tham số của mô hình ngôn ngữ.

Ví dụ:

- BART
- Seq2Seq Transformer

### Non-Parametric Memory

Là bộ nhớ bên ngoài:

- Wikipedia
- Knowledge Base
- Document Collection

được lưu dưới dạng Dense Vector Index.

Pipeline:

```text
Question
↓
Retriever
↓
Top-k Documents
↓
Generator
↓
Answer
```

---

### Retriever

Sử dụng:

**Dense Passage Retriever (DPR)**

để tìm các tài liệu liên quan nhất từ Wikipedia.

---

### Generator

Sử dụng:

**BART**

để sinh câu trả lời dựa trên:

```text
Question + Retrieved Documents
```

---

### Hai biến thể RAG

#### RAG-Sequence

Toàn bộ câu trả lời sử dụng cùng một tập documents retrieve được.

#### RAG-Token

Mỗi token trong quá trình sinh có thể sử dụng các documents khác nhau.

RAG-Token linh hoạt hơn nhưng phức tạp hơn.

:contentReference[oaicite:1]{index=1}

---

## Dataset

Bài báo dùng dữ liệu gì?

Tác giả đánh giá trên nhiều bài toán NLP yêu cầu kiến thức thực tế.

Các bộ dữ liệu QA chính gồm:

| Dataset | Mô tả |
|----------|----------|
| Natural Questions (NQ) | Google Search Questions |
| WebQuestions | Freebase Questions |
| CuratedTREC | Open-domain QA |
| TriviaQA | Trivia Question Answering |

Nguồn tri thức:

- Wikipedia Dense Index

được encode bằng DPR.

:contentReference[oaicite:2]{index=2}

---

## Evaluation

Bài báo đánh giá bằng metric nào?

### QA Metrics

- Exact Match (EM)
- Accuracy

### Generation Metrics

- Factuality
- Diversity
- Specificity

### Retrieval-based Evaluation

- Quality of Retrieved Documents

Ngoài ra bài báo còn đánh giá:

- Khả năng cập nhật tri thức.
- Mức độ giảm hallucination.
- Chất lượng sinh văn bản.

:contentReference[oaicite:3]{index=3}

---

## Results

Kết quả chính là gì?

RAG đạt State-of-the-Art trên nhiều bài toán Open-domain QA tại thời điểm công bố.

Các kết quả nổi bật:

### Natural Questions

RAG vượt các mô hình Seq2Seq truyền thống.

### WebQuestions

Thiết lập State-of-the-Art mới.

### CuratedTREC

Đạt kết quả tốt hơn các hệ thống QA trước đó.

---

Ngoài QA:

RAG tạo ra câu trả lời:

- Chính xác hơn.
- Đa dạng hơn.
- Ít hallucination hơn.

so với các mô hình chỉ sử dụng Parametric Memory.

Tác giả kết luận:

> Việc kết hợp Parametric Memory và Non-Parametric Memory giúp mô hình sinh ngôn ngữ hiệu quả hơn đáng kể trên các bài toán yêu cầu tri thức thực tế.

:contentReference[oaicite:4]{index=4}

---

## Limitations

Hạn chế của bài báo là gì?

### 1. Phụ thuộc mạnh vào Retrieval

Nếu Retriever lấy sai tài liệu:

```text
Bad Retrieval
→ Bad Context
→ Bad Answer
```

toàn bộ pipeline sẽ suy giảm hiệu năng.

---

### 2. Chưa xử lý tốt Multi-hop Reasoning

RAG chủ yếu:

```text
Retrieve Once
→ Generate
```

Khó xử lý các câu hỏi cần nhiều bước suy luận.

---

### 3. Chi phí Retrieval tăng

Cần:

- Dense Embedding
- Vector Search
- Index Storage

làm tăng tài nguyên hệ thống.

---

### 4. Hallucination vẫn tồn tại

Mặc dù giảm đáng kể nhưng:

LLM vẫn có thể:

- Hiểu sai context.
- Sinh thông tin không tồn tại.

:contentReference[oaicite:5]{index=5}

---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Cực kỳ cao (Foundational Paper)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Thực tế toàn bộ kiến trúc hiện tại của hệ thống đều xuất phát từ paper này.

Ví dụ:

```text
Student Question
↓
Embedding
↓
Pinecone
↓
Top-k Retrieval
↓
LLM
↓
Answer
```

đây chính là phiên bản hiện đại của kiến trúc RAG được đề xuất trong bài báo.

Paper này cung cấp nền tảng lý thuyết quan trọng cho:

- Retrieval-Augmented Generation.
- Vector Database.
- Embedding Search.
- Knowledge Grounding.
- Hallucination Reduction.

Đây là paper bắt buộc phải xuất hiện trong chương:

- Literature Review.
- Related Works.
- Theoretical Foundation.

của AI Study Hub.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Thay Wikipedia bằng tài liệu học tập

Thay vì:

```text
Wikipedia
```

sử dụng:

```text
PDF
Slides
Lecture Notes
Syllabus
```

để xây dựng Academic RAG System.

---

### 2. Kết hợp DR-RAG

Pipeline:

```text
Question
↓
Retrieve
↓
Dynamic Retrieval
↓
Generate
```

Giúp xử lý các câu hỏi học thuật nhiều bước suy luận.

---

### 3. Kết hợp CRAG

Thêm Retrieval Evaluator:

```text
Retrieve
↓
Evaluate
↓
Correct
↓
Generate
```

để giảm retrieve sai chunk.

---

### 4. Kết hợp Self-RAG

Cho phép hệ thống:

- Tự đánh giá câu trả lời.
- Tự kiểm tra độ tin cậy.
- Tự quyết định có cần retrieve thêm hay không.

---

### 5. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
LLM Only
vs
Basic RAG
vs
Enhanced RAG
```

trên tập tài liệu học tập thực tế.

Đánh giá bằng:

- Accuracy
- Recall
- Faithfulness
- Response Time

để chứng minh hiệu quả của Retrieval-Augmented Generation trong môi trường giáo dục.