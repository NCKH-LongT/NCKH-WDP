# Paper 05 Summary

## Citation

Tên bài:  
DR-RAG: Applying Dynamic Document Relevance to Retrieval-Augmented Generation for Question-Answering

Tác giả:  
Zijian Hei, Weiling Liu, Wenjie Ou, Juyi Qiao, Junming Jiao, Guowen Song, Ting Tian, Yi Lin

Năm:  
2024

Nguồn:  
arXiv

DOI/Link:  
https://arxiv.org/abs/2406.07348

---

## Problem

Bài báo giải quyết vấn đề gì?

Các hệ thống Retrieval-Augmented Generation (RAG) truyền thống thường gặp khó khăn trong các bài toán Multi-hop Question Answering.

Nguyên nhân là retriever chủ yếu tìm được các tài liệu có độ tương đồng cao với câu hỏi ban đầu (static-relevant documents), trong khi nhiều tài liệu cần thiết cho quá trình suy luận lại có độ tương đồng thấp nhưng vẫn đóng vai trò quan trọng (dynamic-relevant documents).

Ví dụ:

```text
Question:
Who is the spouse of the child of Peter Andreas Heiberg?
```

Retriever dễ tìm được:

```text
Peter Andreas Heiberg
→ Son
→ Johan Ludvig Heiberg
```

Nhưng khó tìm được:

```text
Johan Ludvig Heiberg
→ Wife
→ Johanne Luise Heiberg
```

vì tài liệu thứ hai không trực tiếp giống với query ban đầu.

Điều này dẫn đến:

- Recall thấp.
- Thiếu thông tin trong context.
- Hallucination từ LLM.
- Trả lời sai trong các bài toán nhiều bước suy luận.

Bài báo tập trung giải quyết vấn đề:

> Làm thế nào để retrieve được các dynamic-relevant documents phục vụ Multi-hop Question Answering?

---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Tác giả đề xuất framework:

# DR-RAG (Dynamic-Relevant Retrieval-Augmented Generation)

Framework gồm hai thành phần chính:

---

### 1. Two-stage Retrieval

#### Stage 1

Retrieve:

```text
Top-k1 Documents
```

giống RAG truyền thống.

---

#### Stage 2

Sử dụng:

# Query Document Concatenation (QDC)

Kết hợp:

```text
Question + Retrieved Document
```

để tạo truy vấn mở rộng.

Ví dụ:

```text
Who is the spouse...
+
Johan Ludvig Heiberg is son of Peter...
```

↓

```text
Expanded Query
```

↓

```text
Second Retrieval
```

Mục tiêu:

- Tìm các dynamic-relevant documents.
- Tăng Recall.
- Khai thác quan hệ giữa các tài liệu.

---

### 2. Dynamic Relevance Classifier

Sau khi retrieve được các tài liệu mới:

Hệ thống sử dụng Binary Classifier để đánh giá:

```text
Document này có thực sự giúp trả lời câu hỏi không?
```

Output:

```text
Positive
Negative
```

---

### Hai chiến lược lọc

#### CIS (Classifier Inverse Selection)

Loại bỏ các tài liệu dư thừa sau retrieval.

#### CFS (Classifier Forward Selection)

Chỉ giữ lại các tài liệu được classifier xác nhận là hữu ích.

Trong thực nghiệm:

```text
CFS
```

cho kết quả tốt nhất.

---

## Dataset

Bài báo dùng dữ liệu gì?

Tác giả đánh giá trên các bộ dữ liệu Multi-hop QA nổi tiếng:

| Dataset | Mô tả |
|----------|----------|
| MuSiQue | Multi-hop Reasoning |
| HotpotQA | Multi-document QA |
| 2Wiki Multi-hop QA | Multi-hop QA từ Wikipedia |

Đây đều là các benchmark yêu cầu:

```text
Multiple Documents
+
Reasoning Across Documents
```

để trả lời chính xác.

---

## Evaluation

Bài báo đánh giá bằng metric nào?

### QA Metrics

- Accuracy (Acc)
- Exact Match (EM)
- F1 Score

---

### Retrieval Metrics

- Recall Rate

---

### Efficiency Metrics

- Number of LLM Calls
- Query Processing Time

---

Ngoài ra bài báo còn đánh giá:

- Dynamic Document Discovery Ability
- Multi-hop Retrieval Performance

---

## Results

Kết quả chính là gì?

### Recall Improvement

DR-RAG tăng Recall lên tới:

```text
86.75%
```

so với các retrieval strategy truyền thống.

---

### QA Performance

Cải thiện:

| Metric | Improvement |
|----------|----------|
| Accuracy | +6.17% |
| Exact Match | +7.34% |
| F1 Score | +9.36% |

---

### HotpotQA

| Method | Accuracy |
|----------|----------|
| Adaptive-RAG | 44.40 |
| DR-RAG | 55.68 |

---

### Efficiency

So với Adaptive-RAG:

- Chỉ gọi LLM một lần.
- Giảm khoảng 74.2% thời gian xử lý.
- Retrieval hiệu quả hơn trong các bài toán Multi-hop QA.

---

### Kết luận chính

Tác giả chứng minh rằng:

```text
Dynamic-Relevant Documents
```

đóng vai trò rất quan trọng trong QA và việc khai thác các tài liệu này giúp cải thiện đáng kể chất lượng câu trả lời.

---

## Limitations

Hạn chế của bài báo là gì?

### 1. Cần huấn luyện classifier riêng

Framework không hoạt động theo kiểu:

```text
Plug-and-Play
```

Cần:

- Tạo dữ liệu huấn luyện.
- Fine-tune classifier.
- Bảo trì classifier riêng.

---

### 2. Chưa đánh giá trên domain đặc thù

Các thí nghiệm chủ yếu thực hiện trên:

```text
Wikipedia QA Benchmarks
```

Chưa kiểm chứng trên:

- Giáo dục.
- Y tế.
- Pháp luật.
- Doanh nghiệp.

---

### 3. Tăng độ phức tạp hệ thống

RAG:

```text
Question
→ Retrieve
→ Generate
```

DR-RAG:

```text
Question
→ Retrieve
→ QDC
→ Retrieve Again
→ Classifier
→ Generate
```

Khó triển khai và bảo trì hơn.

---

### 4. Chưa xử lý Self-Reflection

Framework vẫn phụ thuộc vào:

```text
Retriever
+
Classifier
```

Chưa có cơ chế:

- Self-Correction.
- Self-Evaluation.

như các paper mới hơn như:

- CRAG
- Self-RAG

---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Rất cao (Core Retrieval Improvement Paper)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Hiện tại hệ thống đang sử dụng:

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

Đây là:

```text
Basic RAG
```

---

Bài báo chỉ ra rằng:

Top-k Retrieval có thể bỏ sót các chunk quan trọng nếu thông tin nằm phân tán ở nhiều phần khác nhau của tài liệu.

Điều này rất giống môi trường học tập.

Ví dụ:

```text
MMA301 gồm những thành phần điểm nào
và Final Exam chiếm bao nhiêu phần trăm?
```

Thông tin có thể nằm ở:

```text
Chunk A
→ Course Structure

Chunk B
→ Grading Policy
```

Basic RAG có thể chỉ retrieve được một chunk.

DR-RAG giúp retrieve được cả hai.

---

Paper này đặc biệt phù hợp với:

- Lecture Notes.
- PDF môn học.
- Syllabus.
- Slide bài giảng.

vì kiến thức thường phân tán ở nhiều chương khác nhau.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Multi-hop Retrieval cho tài liệu học tập

Thay vì:

```text
Question
→ Retrieve Once
→ LLM
```

Sử dụng:

```text
Question
→ Retrieve
→ Expanded Query
→ Retrieve Again
→ LLM
```

Giúp tăng khả năng tìm đủ thông tin từ nhiều chương.

---

### 2. Thay Classifier bằng LLM Judge

Thay vì huấn luyện classifier riêng:

```text
Question
Document A
Document B

Document B có hữu ích không?
```

LLM sẽ đánh giá trực tiếp.

Ưu điểm:

- Dễ triển khai hơn.
- Phù hợp với đồ án sinh viên.

---

### 3. Kết hợp DPR + DR-RAG

Pipeline:

```text
Question
↓
DPR Retrieval
↓
Dynamic Retrieval
↓
LLM
```

Giúp vừa có:

- Semantic Search mạnh.
- Multi-hop Retrieval.

---

### 4. Kết hợp CRAG

Thêm bước:

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

### 5. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
Basic RAG
vs
DR-RAG Inspired RAG
```

trên tập tài liệu học tập thực tế.

Đánh giá:

- Recall
- Accuracy
- Faithfulness
- Response Time

để chứng minh Dynamic Retrieval giúp cải thiện chất lượng hỏi đáp học tập.