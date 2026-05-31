# Paper 04 Summary

## Citation

Tên bài:  
Dense Passage Retrieval for Open-Domain Question Answering

Tác giả:  
Vladimir Karpukhin, Barlas Oguz, Sewon Min, Patrick Lewis, Ledell Wu, Sergey Edunov, Danqi Chen, Wen-tau Yih

Năm:  
2020

Nguồn:  
EMNLP 2020 (Conference on Empirical Methods in Natural Language Processing)

DOI/Link:  
https://aclanthology.org/2020.emnlp-main.550/

---

## Problem

Bài báo giải quyết vấn đề gì?

Trong Open-Domain Question Answering (ODQA), hầu hết các hệ thống truyền thống sử dụng BM25 hoặc TF-IDF để retrieve các đoạn văn liên quan trước khi đưa vào Reader Model.

Tuy nhiên, các phương pháp này phụ thuộc mạnh vào việc khớp từ khóa (keyword matching), dẫn đến khó tìm được các đoạn văn có ý nghĩa tương đồng nhưng sử dụng từ ngữ khác nhau.

Ví dụ:

Question:

```text
Who is the bad guy in Lord of the Rings?
```

Passage:

```text
Sala Baker portrayed the villain Sauron.
```

BM25 khó liên kết được:

```text
bad guy ≠ villain
```

Điều này làm giảm chất lượng retrieval và kéo theo giảm độ chính xác của toàn bộ hệ thống QA.

Bài báo đặt ra câu hỏi:

> Liệu Dense Retrieval có thể thay thế hoàn toàn BM25 trong Open-Domain Question Answering hay không?

---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Tác giả đề xuất mô hình:

# DPR (Dense Passage Retrieval)

DPR sử dụng kiến trúc:

### Dual Encoder

Gồm:

- Question Encoder
- Passage Encoder

Cả hai đều sử dụng BERT-base độc lập.

Pipeline:

```text
Question
↓
Question Encoder
↓
Question Embedding

Passage
↓
Passage Encoder
↓
Passage Embedding
```

Sau đó tính:

```text
Similarity = Dot Product
```

giữa vector câu hỏi và vector passage.

---

### In-Batch Negative Sampling

Trong quá trình training:

```text
Question A
→ Positive Passage A

Passage B,C,D...
→ Negative Samples
```

Tận dụng các passage trong cùng batch làm negative samples để tăng hiệu quả huấn luyện.

---

### Hard Negative Training

Ngoài random negatives, DPR còn sử dụng:

```text
BM25 Hard Negatives
```

Là các passage được BM25 đánh giá cao nhưng không chứa đáp án.

Điều này giúp mô hình học được các trường hợp dễ gây nhầm lẫn.

---

### Dense Vector Retrieval

Sau khi encode toàn bộ corpus:

```text
Passage
→ Dense Vector
→ FAISS Index
```

Khi inference:

```text
Question
→ Dense Vector
→ FAISS Search
→ Top-k Passages
```

---

## Dataset

Bài báo dùng dữ liệu gì?

Nguồn dữ liệu:

### Wikipedia Dump 2018

Sau khi xử lý:

```text
21,015,324 passages
```

được tạo từ Wikipedia.

---

Các bộ dữ liệu QA được sử dụng:

| Dataset | Mô tả |
|----------|----------|
| Natural Questions (NQ) | Google Search Questions |
| TriviaQA | Trivia Question Answering |
| WebQuestions | Freebase Questions |
| CuratedTREC | Open-domain QA |
| SQuAD v1.1 | Reading Comprehension |

---

## Evaluation

Bài báo đánh giá bằng metric nào?

### Retrieval Metrics

- Top-5 Retrieval Accuracy
- Top-20 Retrieval Accuracy
- Top-100 Retrieval Accuracy

### QA Metrics

- Exact Match (EM)

### Efficiency Metrics

- Questions per Second
- Retrieval Latency
- Indexing Time

---

## Results

Kết quả chính là gì?

### Retrieval Performance

DPR vượt BM25 trên hầu hết dataset.

Ví dụ:

### Natural Questions

| Method | Top-20 Accuracy |
|----------|----------|
| BM25 | 59.1% |
| DPR | 79.4% |

Tăng:

```text
+20.3%
```

---

### End-to-End QA

#### Natural Questions

| Method | Exact Match |
|----------|----------|
| ORQA | 33.3 |
| DPR | 41.5 |

#### TriviaQA

| Method | Exact Match |
|----------|----------|
| BM25 | 52.4 |
| DPR | 56.8 |

DPR thiết lập State-of-the-Art trên nhiều benchmark Open-Domain QA tại thời điểm công bố.

---

### Efficiency

DPR đạt:

```text
995 questions/second
```

với:

```text
Top-100 Retrieval
```

sử dụng FAISS.

Trong khi BM25 chỉ đạt:

```text
23.7 questions/second
```

trên cùng môi trường thử nghiệm.

---

## Limitations

Hạn chế của bài báo là gì?

### 1. Chi phí indexing cao

Cần:

```text
Encode
→ 21 triệu passages
→ FAISS Index
```

mất nhiều giờ xử lý.

---

### 2. Cần GPU để training

DPR sử dụng:

- BERT Encoder
- Dense Embedding
- Large Batch Training

tốn tài nguyên hơn BM25.

---

### 3. Khó giải thích kết quả

BM25 có thể giải thích bằng:

```text
Keyword Matching
```

Trong khi DPR dựa trên Dense Vector nên khó interpret hơn.

---

### 4. Chưa xử lý Multi-hop Retrieval

Pipeline DPR chủ yếu:

```text
Question
→ Retrieve
→ Reader
```

khó xử lý các câu hỏi cần nhiều bước suy luận.

Đây là điểm mà các paper sau như:

- DR-RAG
- CRAG
- Self-RAG

tiếp tục cải tiến.

---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Cực kỳ cao (Core Technical Foundation)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Hầu như toàn bộ hệ sinh thái RAG hiện đại đều kế thừa trực tiếp từ DPR.

Pipeline hiện tại của hệ thống:

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

thực chất là phiên bản mở rộng của DPR.

---

Paper này cung cấp nền tảng lý thuyết cho:

- Dense Retrieval
- Embedding Search
- Vector Database
- Semantic Search
- Retrieval Component trong RAG

Đây là paper quan trọng để giải thích:

> Vì sao hệ thống sử dụng Embedding + Pinecone thay vì chỉ dùng Keyword Search.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Fine-tune Embedding cho dữ liệu học tập

Thay vì sử dụng embedding model tổng quát:

```text
text-embedding-004
```

có thể fine-tune trên:

- Slide bài giảng
- Syllabus
- Lecture Notes

để tăng chất lượng retrieval.

---

### 2. Hard Negative Training

Sử dụng:

```text
Các chunk dễ gây nhầm lẫn
```

làm hard negatives.

Ví dụ:

- Chương 1 và Chương 2 có nội dung tương tự.
- Hai môn học có thuật ngữ giống nhau.

Giúp retriever phân biệt chính xác hơn.

---

### 3. Kết hợp DPR với DR-RAG

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

giúp xử lý các câu hỏi học thuật nhiều bước suy luận.

---

### 4. Kết hợp DPR với CRAG

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

### 5. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
BM25
vs
DPR
vs
DR-RAG Inspired Retrieval
```

trên tập tài liệu học tập thực tế.

Đánh giá:

- Recall
- Accuracy
- Faithfulness
- Response Time

để chứng minh Dense Retrieval phù hợp hơn với hệ thống hỏi đáp tài liệu học tập.