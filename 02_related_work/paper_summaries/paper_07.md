# Paper 07 Summary

## Citation

Tên bài:  
Corrective Retrieval Augmented Generation

Tác giả:  
Shi-Qi Yan, Jia-Chen Gu, Yun Zhu, Zhen-Hua Ling

Năm:  
2024

Nguồn:  
arXiv

DOI/Link:  
https://arxiv.org/abs/2401.15884

---

## Problem

Bài báo giải quyết vấn đề gì?

Mặc dù Retrieval-Augmented Generation (RAG) giúp giảm hallucination bằng cách bổ sung tri thức từ bên ngoài, nhưng chất lượng của toàn bộ hệ thống vẫn phụ thuộc rất lớn vào Retriever.

Một vấn đề phổ biến là:

```text
Bad Retrieval
→ Bad Context
→ Bad Answer
```

Nếu retriever lấy:

- Sai tài liệu.
- Tài liệu không liên quan.
- Tài liệu thiếu thông tin.

thì LLM vẫn cố gắng sinh câu trả lời từ context đó, dẫn đến:

- Hallucination.
- Trả lời sai.
- Citation không chính xác.
- Context Noise.

RAG truyền thống thường:

```text
Question
→ Retrieve
→ Generate
```

mà không có cơ chế kiểm tra:

```text
Retrieved Documents có thực sự tốt không?
```

Bài báo đặt ra mục tiêu:

> Xây dựng một hệ thống có khả năng đánh giá chất lượng retrieval và tự sửa lỗi retrieval trước khi sinh câu trả lời.

:contentReference[oaicite:0]{index=0}

---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Tác giả đề xuất framework:

# CRAG (Corrective Retrieval-Augmented Generation)

Ý tưởng cốt lõi:

```text
Retrieve
↓
Evaluate
↓
Correct
↓
Generate
```

Thay vì sử dụng trực tiếp retrieval results như RAG truyền thống.

:contentReference[oaicite:1]{index=1}

---

### 1. Retrieval Evaluator

CRAG bổ sung:

# Lightweight Retrieval Evaluator

để đánh giá:

```text
Retrieved Documents
```

có đủ chất lượng hay không.

Output:

```text
Confidence Score
```

Ví dụ:

```text
High Confidence
Medium Confidence
Low Confidence
```

:contentReference[oaicite:2]{index=2}

---

### 2. Corrective Strategy

Nếu:

```text
Retrieval Quality = Poor
```

CRAG sẽ kích hoạt:

# Corrective Retrieval

thay vì dùng trực tiếp context lỗi.

Ví dụ:

```text
Retrieve
↓
Evaluate
↓
Need Correction
↓
Web Search
↓
Refined Documents
```

:contentReference[oaicite:3]{index=3}

---

### 3. Web Search Augmentation

Một điểm quan trọng của CRAG:

Nếu corpus nội bộ không đủ:

```text
Knowledge Base
```

CRAG có thể:

```text
Call Web Search
```

để mở rộng nguồn tri thức.

Điều này giúp:

- Cập nhật kiến thức mới.
- Tìm tài liệu bổ sung.
- Giảm thiếu thông tin.

:contentReference[oaicite:4]{index=4}

---

### 4. Decompose-then-Recompose Algorithm

CRAG không sử dụng toàn bộ document retrieve được.

Thay vào đó:

```text
Document
↓
Decompose
↓
Filter Important Information
↓
Recompose
↓
LLM
```

Mục tiêu:

- Loại bỏ context nhiễu.
- Chỉ giữ thông tin quan trọng.

:contentReference[oaicite:5]{index=5}

---

### 5. Plug-and-Play Architecture

CRAG được thiết kế theo hướng:

```text
Plug-and-Play
```

Có thể gắn trực tiếp vào:

- Basic RAG
- DPR-based RAG
- Self-RAG
- Advanced RAG Systems

mà không cần huấn luyện lại toàn bộ LLM.

:contentReference[oaicite:6]{index=6}

---

## Dataset

Bài báo dùng dữ liệu gì?

CRAG được đánh giá trên:

### Short-form QA Tasks

Các bài toán Question Answering ngắn.

### Long-form Generation Tasks

Các bài toán sinh văn bản dài cần nhiều tri thức.

---

Tổng cộng:

```text
4 Datasets
```

bao phủ:

- Retrieval Quality.
- Knowledge-intensive QA.
- Long-form Generation.

:contentReference[oaicite:7]{index=7}

---

## Evaluation

Bài báo đánh giá bằng metric nào?

### QA Metrics

- Accuracy
- Exact Match (EM)
- F1 Score

---

### Retrieval Metrics

- Retrieval Quality
- Confidence Accuracy

---

### Generation Metrics

- Factual Correctness
- Robustness
- Long-form Answer Quality

---

Ngoài ra còn đánh giá:

### Retrieval Correction Effectiveness

Khả năng:

```text
Detect
+
Correct
```

retrieval lỗi.

:contentReference[oaicite:8]{index=8}

---

## Results

Kết quả chính là gì?

CRAG cải thiện đáng kể hiệu năng của các hệ thống RAG truyền thống.

---

### Retrieval Robustness

CRAG cho thấy khả năng:

```text
Detect Bad Retrieval
```

và kích hoạt corrective strategy hiệu quả.

---

### Better QA Performance

Trên nhiều dataset:

CRAG vượt:

- Basic RAG
- Conventional Retrieval Pipelines

về:

- Accuracy
- Factuality
- Robustness

:contentReference[oaicite:9]{index=9}

---

### Long-form Generation

CRAG cải thiện:

- Context Quality.
- Citation Reliability.
- Answer Correctness.

---

### Main Conclusion

Tác giả chứng minh:

```text
Retrieve
↓
Evaluate
↓
Correct
↓
Generate
```

hiệu quả hơn:

```text
Retrieve
↓
Generate
```

của RAG truyền thống.

:contentReference[oaicite:10]{index=10}

---

## Limitations

Hạn chế của bài báo là gì?

### 1. Tăng Latency

CRAG bổ sung:

```text
Retrieval Evaluation
+
Correction Step
```

làm tăng thời gian xử lý.

---

### 2. Phụ thuộc Web Search

Nếu:

```text
External Search
```

không ổn định:

hiệu năng có thể giảm.

---

### 3. Retrieval Evaluator vẫn có thể sai

Nếu evaluator đánh giá sai:

```text
Good Retrieval
→ Marked Bad

Bad Retrieval
→ Marked Good
```

sẽ ảnh hưởng toàn bộ pipeline.

---

### 4. Chưa có Self-Reflection hoàn chỉnh

CRAG chủ yếu:

```text
Correct Retrieval
```

chứ chưa:

```text
Self-Evaluate Final Answer
```

như Self-RAG.

:contentReference[oaicite:11]{index=11}

---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Rất cao (Retrieval Reliability Paper)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Hiện tại hệ thống:

```text
Question
↓
Embedding
↓
Pinecone
↓
Top-k Retrieval
↓
LLM
```

chưa có bước:

```text
Retrieved Chunks có thực sự tốt không?
```

---

Ví dụ:

Sinh viên hỏi:

```text
Final Exam chiếm bao nhiêu phần trăm?
```

Nhưng retriever lấy nhầm:

```text
Attendance Policy
```

RAG truyền thống vẫn trả lời.

Điều này tạo ra:

```text
Hallucination
```

---

CRAG bổ sung:

```text
Retrieve
↓
Evaluate
↓
Correct
↓
Generate
```

giúp:

- Giảm retrieve sai chunk.
- Giảm context noise.
- Tăng độ tin cậy của câu trả lời.

---

Điều này rất quan trọng với:

- PDF môn học.
- Lecture Notes.
- Syllabus.
- Educational QA.

nơi độ chính xác của thông tin có giá trị cao.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Retrieval Confidence Layer

Sau khi retrieve:

```text
Question
↓
Retrieve
↓
Confidence Check
↓
LLM
```

Nếu confidence thấp:

```text
Retrieve Again
```

---

### 2. LLM-based Retrieval Evaluator

Thay vì train evaluator riêng:

```text
Question
+
Chunks
↓
LLM Judge
↓
Confidence Score
```

Dễ triển khai hơn trong đồ án sinh viên.

---

### 3. Hybrid Retrieval + CRAG

Kết hợp:

```text
Dense Retrieval
+
Keyword Retrieval
+
CRAG Evaluation
```

để tăng Recall.

---

### 4. Kết hợp DR-RAG + CRAG

Pipeline:

```text
Question
↓
DPR Retrieval
↓
Dynamic Retrieval
↓
Retrieval Evaluation
↓
LLM
```

giúp:

- Multi-hop Retrieval.
- Retrieval Correction.

cùng lúc.

---

### 5. Kết hợp Self-RAG + CRAG

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

giúp hệ thống vừa:

- Sửa lỗi Retrieval.
- Tự đánh giá câu trả lời.

---

### 6. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
Basic RAG
vs
DR-RAG
vs
CRAG
vs
Self-RAG
```

trên tập tài liệu học tập thực tế.

Đánh giá:

- Accuracy
- Recall
- Faithfulness
- Citation Accuracy
- Response Time

để chứng minh Retrieval Correction giúp cải thiện độ chính xác và giảm hallucination trong hệ thống hỏi đáp học tập.