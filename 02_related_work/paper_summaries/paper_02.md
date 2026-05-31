# Paper 02 Summary

## Citation

- **Tên bài:** Dense Passage Retrieval for Open-Domain Question Answering
- **Tác giả:** Vladimir Karpukhin, Barlas Oguz, Sewon Min, Patrick Lewis, Ledell Wu, Sergey Edunov, Danqi Chen, Wen-tau Yih
- **Năm:** 2020
- **Nguồn:** EMNLP 2020 (Conference on Empirical Methods in Natural Language Processing)
- **DOI/Link:** https://aclanthology.org/2020.emnlp-main.550/ :contentReference[oaicite:0]{index=0}

## Problem

Open-domain Question Answering (ODQA) thường sử dụng các phương pháp truy xuất truyền thống như BM25 hoặc TF-IDF để tìm các đoạn văn liên quan trước khi đưa vào Reader Model.

Tuy nhiên các phương pháp này phụ thuộc mạnh vào sự trùng khớp từ khóa (keyword matching), dẫn đến khó tìm được những đoạn văn có ý nghĩa tương đồng nhưng sử dụng từ vựng khác nhau.

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

Do đó làm giảm chất lượng retrieval và kéo theo giảm hiệu quả toàn bộ hệ thống QA.

Bài báo đặt ra câu hỏi:

> Liệu Dense Retrieval có thể thay thế hoàn toàn BM25 trong Open-domain QA hay không?

:contentReference[oaicite:1]{index=1}

---

## Method

Bài báo đề xuất mô hình:

# DPR (Dense Passage Retrieval)

Sử dụng kiến trúc:

### Dual Encoder

Gồm:

- Question Encoder
- Passage Encoder

Cả hai đều sử dụng BERT-base độc lập.

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

Giữa vector câu hỏi và vector đoạn văn.

### Training Strategy

Tác giả đề xuất:

#### In-Batch Negative Sampling

Trong một batch:

```text
Question A → Passage A (positive)

Passage B,C,D...
→ negative samples
```

Giúp tăng số lượng negative samples mà không tốn thêm chi phí tính toán.

#### Hard Negative

Ngoài random negative, DPR còn sử dụng:

```text
BM25 Hard Negatives
```

Là các passage được BM25 đánh giá cao nhưng không chứa đáp án.

Điều này giúp DPR học được những trường hợp dễ nhầm lẫn.

:contentReference[oaicite:2]{index=2}

---

## Dataset

Bài báo đánh giá trên 5 bộ dữ liệu QA nổi tiếng:

| Dataset | Mô tả |
|----------|----------|
| Natural Questions (NQ) | Google Search Questions |
| TriviaQA | Trivia Questions |
| WebQuestions | Freebase Questions |
| CuratedTREC | TREC QA |
| SQuAD v1.1 | Reading Comprehension |

Nguồn tài liệu:

- Wikipedia Dump 2018
- Hơn 21 triệu passages được tạo từ Wikipedia

:contentReference[oaicite:3]{index=3}

---

## Evaluation

Bài báo sử dụng các metric:

### Retrieval Metrics

- Top-5 Retrieval Accuracy
- Top-20 Retrieval Accuracy
- Top-100 Retrieval Accuracy

### QA Metrics

- Exact Match (EM)

### Efficiency Metrics

- Throughput (Questions/Second)
- Retrieval Latency

:contentReference[oaicite:4]{index=4}

---

## Results

### Retrieval Performance

DPR vượt BM25 trên hầu hết dataset.

Ví dụ:

#### Natural Questions

| Method | Top-20 Accuracy |
|----------|----------|
| BM25 | 59.1% |
| DPR | 79.4% |

Tăng hơn:

```text
+20.3%
```

:contentReference[oaicite:5]{index=5}

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

DPR thiết lập State-of-the-Art trên nhiều benchmark Open-domain QA tại thời điểm công bố.

:contentReference[oaicite:6]{index=6}

---

### Efficiency

DPR:

- 995 câu hỏi/giây
- Top-100 retrieval
- Sử dụng FAISS để tìm kiếm vector

Trong khi BM25 chỉ đạt:

- 23.7 câu hỏi/giây

trên cùng môi trường thử nghiệm.

:contentReference[oaicite:7]{index=7}

---

## Limitations

### 1. Chi phí indexing lớn

DPR cần:

- Encode toàn bộ corpus thành vector
- Xây dựng FAISS Index

Với Wikipedia:

```text
21 triệu passages
```

Quá trình indexing mất nhiều giờ.

### 2. Yêu cầu GPU

Huấn luyện DPR cần:

- BERT
- Dense Embedding
- Large Batch Training

Chi phí tài nguyên cao hơn BM25.

### 3. Khó giải thích kết quả

BM25 cho biết passage được chọn vì từ khóa nào.

DPR sử dụng vector embedding nên khó giải thích hơn.

### 4. Chưa xử lý Multi-hop Retrieval

DPR chủ yếu thực hiện:

```text
Question
→ Retrieve
→ Reader
```

Không giải quyết tốt các câu hỏi cần nhiều bước suy luận như các phương pháp DR-RAG sau này.

:contentReference[oaicite:8]{index=8}

---

## Relevance to our topic

### Mức độ liên quan: Cực kỳ cao (Core Technical Foundation)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Hầu như toàn bộ pipeline Retrieval hiện nay đều kế thừa tư tưởng của DPR.

Ví dụ:

```text
Question
↓
Embedding Model
↓
Vector Database
↓
Top-k Retrieval
↓
LLM
```

Chính là phiên bản mở rộng của DPR.

Đặc biệt:

- Pinecone
- ChromaDB
- Weaviate
- Qdrant

đều hoạt động dựa trên nguyên lý Dense Retrieval do DPR phổ biến.

Bài báo này là nền tảng lý thuyết quan trọng để giải thích:

- Vì sao cần Embedding
- Vì sao cần Vector Database
- Vì sao Dense Retrieval tốt hơn BM25 trong nhiều trường hợp

đối với AI Study Hub.

---

## Possible improvement for our system

### 1. Áp dụng DPR Retrieval Pipeline

Thay vì:

```text
Question
→ Keyword Search
→ LLM
```

Sử dụng:

```text
Question
→ Embedding
→ Pinecone
→ Top-k Retrieval
→ LLM
```

Giống kiến trúc DPR.

### 2. Hard Negative Training

Trong tương lai có thể fine-tune embedding model trên dữ liệu học tập bằng:

- Các chunk dễ gây nhầm lẫn
- Các chương có nội dung gần giống nhau

để cải thiện retrieval.

### 3. Kết hợp DPR + DR-RAG

DPR giải quyết:

```text
Dense Retrieval
```

DR-RAG giải quyết:

```text
Multi-hop Retrieval
```

Kết hợp hai ý tưởng có thể tạo ra:

```text
AI Study Hub Enhanced RAG
```

cho chất lượng retrieval tốt hơn.

### 4. Hướng nghiên cứu cho Paper

So sánh:

```text
BM25
vs
DPR-style Retrieval
vs
DR-RAG Inspired Retrieval
```

trên tập tài liệu học tập thực tế.

Các metric:

- Recall
- Accuracy
- Faithfulness
- Response Time

để chứng minh giá trị của Dense Retrieval trong môi trường giáo dục.