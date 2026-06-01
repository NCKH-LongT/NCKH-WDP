# Paper 4 Summary

## Citation

Tên bài:
Assessing the Robustness of Retrieval-Augmented Generation Systems in K-12 Educational Question Answering with Knowledge Discrepancies

Tác giả:
Tianshi Zheng, Weihan Li, Jiaxin Bai, Weiqi Wang, Yangqiu Song

Năm:
2024

Nguồn:
arXiv

DOI/Link:
https://arxiv.org/abs/2412.08985

---

## Problem

Bài báo giải quyết vấn đề gì?

Các hệ thống Retrieval-Augmented Generation (RAG) đã chứng minh hiệu quả trong các bài toán Question Answering. Tuy nhiên trong môi trường giáo dục, đặc biệt là K-12 Education, tồn tại một vấn đề quan trọng:

```text
Knowledge Discrepancy
```

Tức là:

* Kiến thức trong textbook có thể khác với kiến thức mà LLM đã học trước đó.
* Nội dung giáo trình có thể được cập nhật mới.
* Đáp án trong tài liệu học tập có thể không hoàn toàn trùng với parametric knowledge của mô hình.

Ví dụ:

```text
Textbook:
Pluto is a dwarf planet.

LLM Memory:
Pluto is a planet.
```

Khi xảy ra sự khác biệt này, RAG có thể:

* Retrieve đúng tài liệu.
* Nhưng LLM vẫn trả lời theo kiến thức cũ trong tham số.

Điều này dẫn đến:

* Hallucination.
* Sai kiến thức học thuật.
* Giảm độ tin cậy trong môi trường giáo dục.

Bài báo tập trung nghiên cứu:

> Các hệ thống RAG có thực sự đáng tin cậy khi kiến thức trong tài liệu học tập khác với kiến thức mà LLM đã được huấn luyện hay không?

---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Tác giả không đề xuất một mô hình RAG mới.

Thay vào đó nghiên cứu tập trung vào:

# Robustness Evaluation Framework

để đánh giá độ bền vững của các hệ thống RAG trong môi trường giáo dục.

---

### EduKDQA Dataset

Tác giả xây dựng dataset mới:

# EduKDQA

(Educational Knowledge Discrepancy Question Answering)

Mục tiêu:

```text
Simulate
Knowledge Discrepancies
```

giữa:

* Textbook Knowledge.
* LLM Parametric Knowledge.

---

### Knowledge Update Simulation

Tác giả tạo ra các tình huống:

```text
Old Knowledge
↓
Updated Textbook Knowledge
```

sau đó kiểm tra:

```text
RAG System
```

có ưu tiên kiến thức từ tài liệu hay vẫn sử dụng kiến thức cũ trong mô hình.

---

### Evaluation Pipeline

```text
Question
↓
Retrieve Textbook Context
↓
LLM
↓
Answer
```

Sau đó đánh giá:

* Context Usage.
* Knowledge Integration.
* Answer Correctness.

---

## Dataset

Bài báo dùng dữ liệu gì?

Tác giả xây dựng:

# EduKDQA Dataset

Gồm:

```text
3,005 Questions
```

bao phủ:

```text
5 Subjects
```

trong môi trường giáo dục K-12.

---

Dataset được thiết kế để mô phỏng:

```text
Knowledge Discrepancy Scenarios
```

bao gồm:

* Updated Facts.
* Modified Knowledge.
* Context-dependent Questions.

---

Các câu hỏi yêu cầu:

* Retrieval.
* Reasoning.
* Context Integration.
* Knowledge Conflict Resolution.

---

## Evaluation

Bài báo đánh giá bằng metric nào?

### Question Answering Accuracy

Đánh giá:

```text
Answer Correctness
```

---

### Retrieval Performance

Đánh giá:

```text
Retrieved Context Quality
```

---

### Context Utilization

Đánh giá:

```text
LLM
```

có thực sự sử dụng context retrieve được hay không.

---

### Knowledge Integration

Đánh giá khả năng:

```text
Parametric Knowledge
+
Retrieved Knowledge
```

được kết hợp như thế nào trong quá trình trả lời.

---

## Results

Kết quả chính là gì?

Nghiên cứu cho thấy:

### RAG vẫn gặp khó khăn với Knowledge Discrepancies

Ngay cả khi:

```text
Retriever
```

lấy đúng tài liệu,

LLM vẫn có xu hướng:

```text
Trust Internal Memory
```

thay vì sử dụng kiến thức mới từ textbook.

---

### Significant Performance Drop

Các hệ thống RAG hiện tại bị giảm hiệu năng đáng kể khi:

```text
Retrieved Knowledge
≠
LLM Parametric Knowledge
```

---

### Knowledge Integration Remains Difficult

Những câu hỏi yêu cầu:

```text
Textbook Knowledge
+
LLM Knowledge
```

là nhóm khó nhất đối với các hệ thống hiện nay.

---

### Main Conclusion

Tác giả kết luận rằng:

> Knowledge Discrepancy là một thách thức quan trọng nhưng chưa được nghiên cứu đầy đủ trong Educational RAG Systems.

---

## Limitations

Hạn chế của bài báo là gì?

### 1. Tập trung vào đánh giá

Nghiên cứu chủ yếu:

```text
Evaluate
```

chứ không đề xuất một kiến trúc RAG mới để giải quyết hoàn toàn vấn đề.

---

### 2. Chỉ tập trung vào K-12 Education

Chưa kiểm chứng trên:

* Đại học.
* Tài liệu chuyên ngành.
* Research Papers.
* Higher Education Systems.

---

### 3. Chưa có Self-Correction Framework

Paper chỉ chỉ ra vấn đề:

```text
Knowledge Discrepancy
```

nhưng chưa đưa ra:

```text
Complete Solution
```

như:

* Self-RAG.
* CRAG.
* DR-RAG.

---

### 4. Chưa đánh giá đa ngôn ngữ

Dataset chủ yếu tập trung vào môi trường tiếng Anh.

---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Rất cao (Educational Reliability Paper)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

---

Một vấn đề thực tế trong AI Study Hub:

Sinh viên upload:

```text
MMA301 Syllabus 2026
```

Nhưng:

```text
LLM
```

có thể đang mang kiến thức cũ hoặc kiến thức tổng quát.

---

Ví dụ:

```text
Question:
Final Exam chiếm bao nhiêu phần trăm?
```

Textbook:

```text
Final Exam = 50%
```

Nhưng LLM có thể:

```text
Generate
40%
```

nếu dựa vào kiến thức khác đã học trước đó.

---

Paper này chứng minh rằng:

```text
Correct Retrieval
≠
Correct Answer
```

Đây là insight rất quan trọng cho AI Study Hub.

---

Paper giúp nhóm giải thích:

> Tại sao chỉ xây dựng RAG thôi vẫn chưa đủ để đảm bảo độ chính xác trong môi trường giáo dục.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Retrieval Priority Mechanism

Buộc hệ thống ưu tiên:

```text
Retrieved Educational Context
```

hơn:

```text
LLM Internal Knowledge
```

khi trả lời.

---

### 2. Self-RAG Integration

Sau khi generate:

```text
Answer
↓
Self-Evaluation
↓
Faithfulness Check
```

để kiểm tra xem câu trả lời có thực sự dựa trên tài liệu hay không.

---

### 3. Citation-Based Answering

Mỗi câu trả lời cần:

```text
Answer
+
Source Chunk
```

để sinh viên kiểm chứng thông tin.

---

### 4. Knowledge Conflict Detection

Thêm module:

```text
Retrieved Knowledge
vs
LLM Memory
```

để phát hiện mâu thuẫn tri thức.

---

### 5. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
Basic RAG
vs
CRAG
vs
Self-RAG
vs
Knowledge-Discrepancy-Aware RAG
```

trên tập tài liệu học tập thực tế.

Đánh giá:

* Accuracy
* Faithfulness
* Hallucination Rate
* Citation Accuracy
* Knowledge Conflict Resolution

để chứng minh khả năng xử lý sự khác biệt giữa tài liệu học tập và kiến thức sẵn có của LLM trong môi trường giáo dục.
