# Paper 06 Summary

## Citation

Tên bài:  
Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection

Tác giả:  
Akari Asai, Zeqiu Wu, Yizhong Wang, Avirup Sil, Hannaneh Hajishirzi

Năm:  
2023 (ICLR 2024)

Nguồn:  
International Conference on Learning Representations (ICLR 2024)

DOI/Link:  
https://arxiv.org/abs/2310.11511

---

## Problem

Bài báo giải quyết vấn đề gì?

Mặc dù Retrieval-Augmented Generation (RAG) giúp giảm hallucination bằng cách bổ sung tri thức từ bên ngoài, nhưng các hệ thống RAG truyền thống vẫn tồn tại nhiều hạn chế:

### 1. Retrieve cố định

Hầu hết hệ thống:

```text
Question
→ Retrieve Top-k
→ Generate
```

bất kể:

- Có thực sự cần retrieve hay không.
- Document retrieve có hữu ích hay không.

Điều này làm:

- Tăng chi phí retrieval.
- Đưa nhiều context nhiễu vào LLM.
- Giảm chất lượng câu trả lời.

---

### 2. Không tự đánh giá câu trả lời

RAG truyền thống:

```text
Retrieve
→ Generate
→ End
```

Không có cơ chế:

- Tự kiểm tra factuality.
- Tự đánh giá chất lượng câu trả lời.
- Tự phát hiện hallucination.

---

### 3. Citation không đảm bảo đúng

Mặc dù có retrieve tài liệu:

LLM vẫn có thể:

- Sinh thông tin không nằm trong document.
- Trích dẫn sai nguồn.
- Hiểu sai context.

Bài báo đặt ra mục tiêu:

> Xây dựng một hệ thống có khả năng tự quyết định khi nào cần retrieve, tự đánh giá thông tin retrieve được và tự phản biện câu trả lời của chính nó.

:contentReference[oaicite:0]{index=0}

---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Tác giả đề xuất framework:

# Self-RAG (Self-Reflective Retrieval-Augmented Generation)

Ý tưởng cốt lõi:

```text
Retrieve
+
Generate
+
Self-Critique
```

trong cùng một mô hình.

---

### Reflection Tokens

Self-RAG bổ sung các token đặc biệt:

```text
[Retrieve]
[Relevant]
[Support]
[Utility]
```

được gọi là:

# Reflection Tokens

Các token này giúp mô hình:

- Quyết định có cần retrieve hay không.
- Đánh giá độ liên quan của tài liệu.
- Đánh giá tài liệu có hỗ trợ câu trả lời hay không.
- Đánh giá chất lượng tổng thể của câu trả lời.

:contentReference[oaicite:1]{index=1}

---

### Adaptive Retrieval

Khác với RAG truyền thống:

```text
Always Retrieve
```

Self-RAG:

```text
Retrieve On-Demand
```

Mô hình tự quyết định:

```text
Có cần retrieve không?
```

Nếu cần:

```text
Generate [Retrieve]
↓
Call Retriever
↓
Retrieve Documents
```

Nếu không:

```text
Generate Directly
```

:contentReference[oaicite:2]{index=2}

---

### Self-Critique Mechanism

Sau khi generate:

Mô hình tiếp tục sinh:

```text
Critique Tokens
```

để đánh giá:

### Relevance

```text
Document có liên quan không?
```

### Support

```text
Document có hỗ trợ câu trả lời không?
```

### Utility

```text
Câu trả lời có hữu ích không?
```

Điều này tạo ra:

```text
Self-Reflection Loop
```

:contentReference[oaicite:3]{index=3}

---

### Training Architecture

Self-RAG gồm:

### Retriever

Truy xuất tài liệu.

### Critic Model

Tạo Reflection Tokens.

### Generator

Sinh câu trả lời và Reflection Tokens.

Pipeline:

```text
Retriever
↓
Critic
↓
Reflection Tokens
↓
Generator Training
```

:contentReference[oaicite:4]{index=4}

---

## Dataset

Bài báo dùng dữ liệu gì?

Self-RAG được đánh giá trên nhiều nhóm bài toán:

| Task | Mô tả |
|----------|----------|
| Open-domain QA | Question Answering |
| Fact Verification | Kiểm chứng sự thật |
| Long-form Generation | Sinh văn bản dài |
| Reasoning Tasks | Suy luận nhiều bước |

---

Một số benchmark nổi bật:

- PopQA
- PubHealth
- ASQA
- ARC Challenge
- FEVER

:contentReference[oaicite:5]{index=5}

---

## Evaluation

Bài báo đánh giá bằng metric nào?

### QA Metrics

- Exact Match (EM)
- Accuracy

---

### Fact Verification Metrics

- F1 Score
- Accuracy

---

### Long-form Generation Metrics

- Citation Precision
- Citation Accuracy
- Factuality

---

### Human Evaluation

Đánh giá:

- Correctness
- Supportiveness
- Utility

---

Ngoài ra còn đánh giá:

### Reflection Quality

Kiểm tra:

```text
Reflection Tokens
```

có phù hợp với đánh giá của con người hay không.

:contentReference[oaicite:6]{index=6}

---

## Results

Kết quả chính là gì?

Self-RAG vượt nhiều hệ thống:

- ChatGPT
- Llama2-Chat + RAG
- Conventional RAG Models

trên nhiều benchmark.

:contentReference[oaicite:7]{index=7}

---

### Open-domain QA

Self-RAG đạt kết quả tốt hơn các hệ thống Retrieval-Augmented truyền thống.

---

### Fact Verification

Tăng đáng kể khả năng:

```text
Fact Grounding
```

và giảm hallucination.

---

### Long-form Generation

Cải thiện mạnh:

- Citation Accuracy.
- Factual Consistency.
- Evidence Support.

---

### Human Evaluation

Người đánh giá xác nhận:

- Reflection Tokens phần lớn phù hợp với đánh giá thực tế.
- Self-RAG tạo câu trả lời đáng tin cậy hơn.

:contentReference[oaicite:8]{index=8}

---

### Kết luận chính

Tác giả chứng minh:

```text
Retrieve
+
Generate
+
Self-Critique
```

hiệu quả hơn đáng kể so với:

```text
Retrieve
+
Generate
```

của RAG truyền thống.

:contentReference[oaicite:9]{index=9}

---

## Limitations

Hạn chế của bài báo là gì?

### 1. Kiến trúc phức tạp

Self-RAG yêu cầu:

- Retriever
- Critic
- Generator
- Reflection Tokens

làm tăng độ phức tạp triển khai.

---

### 2. Training Cost cao

Cần:

- Train Critic Model.
- Tạo Reflection Tokens.
- Fine-tune Generator.

Chi phí cao hơn RAG truyền thống.

---

### 3. Latency tăng

Do có thêm:

```text
Retrieve
+
Critique
+
Reflection
```

nên inference chậm hơn.

---

### 4. Vẫn phụ thuộc Retrieval

Nếu retrieve sai:

```text
Bad Retrieval
→ Bad Reflection
→ Bad Answer
```

Self-RAG không hoàn toàn loại bỏ lỗi retrieval.

:contentReference[oaicite:10]{index=10}

---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Rất cao (Advanced RAG Architecture)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Hiện tại hệ thống:

```text
Question
↓
Retrieve
↓
LLM
↓
Answer
```

chưa có cơ chế:

- Tự đánh giá câu trả lời.
- Tự đánh giá retrieval.
- Tự phát hiện hallucination.

---

Self-RAG cung cấp hướng tiếp cận:

```text
Question
↓
Retrieve
↓
Generate
↓
Self-Evaluate
↓
Final Answer
```

giúp tăng:

- Reliability.
- Factuality.
- Citation Accuracy.

---

Điều này rất quan trọng trong môi trường giáo dục.

Ví dụ:

```text
Sinh viên hỏi:
Final Exam chiếm bao nhiêu phần trăm?
```

Nếu retrieve sai:

RAG thường vẫn trả lời.

Trong khi Self-RAG có thể:

```text
Đánh giá:
Context không đủ
```

và yêu cầu retrieve thêm.

---

Paper này đặc biệt phù hợp với:

- Educational QA.
- Academic RAG.
- Document Question Answering.

nơi độ chính xác rất quan trọng.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Self-Evaluation Layer

Sau khi generate:

```text
Answer
↓
LLM Judge
↓
Faithfulness Check
```

để đánh giá:

- Answer có đúng context không.
- Có hallucination không.

---

### 2. Adaptive Retrieval

Thay vì luôn:

```text
Top-k Retrieval
```

cho phép hệ thống quyết định:

```text
Có cần retrieve không?
```

giúp giảm latency.

---

### 3. Retrieval Confidence Score

Thêm bước:

```text
Retrieve
↓
Confidence Evaluation
↓
Generate
```

để tránh sử dụng context kém chất lượng.

---

### 4. Kết hợp CRAG + Self-RAG

Pipeline:

```text
Question
↓
Retrieve
↓
Correct Retrieval
↓
Generate
↓
Self-Evaluate
```

giúp vừa:

- Correct Retrieval.
- Self Reflection.

---

### 5. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
Basic RAG
vs
DR-RAG
vs
CRAG
vs
Self-RAG Inspired System
```

trên tập tài liệu học tập thực tế.

Đánh giá:

- Accuracy
- Recall
- Faithfulness
- Citation Accuracy
- Response Time

để chứng minh Self-Reflection giúp cải thiện chất lượng hỏi đáp học tập và giảm hallucination trong môi trường giáo dục.