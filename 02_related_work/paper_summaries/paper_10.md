# Paper 10 Summary

## Citation

Tên bài:  
Retrieval-Augmented Generation Chatbots for Education: A Survey of Applications

Tác giả:  
Nhiều tác giả (Survey Paper)

Năm:  
2025

Nguồn:  
Applied Sciences (MDPI)

DOI/Link:  
https://www.mdpi.com/2076-3417/15/8/4234

---

## Problem

Bài báo giải quyết vấn đề gì?

Trong những năm gần đây, Large Language Models (LLMs) như:

- ChatGPT
- Gemini
- Claude
- Llama

được ứng dụng mạnh mẽ trong giáo dục.

Tuy nhiên, các hệ thống này vẫn tồn tại nhiều vấn đề:

### 1. Hallucination

LLM có thể:

- Bịa thông tin.
- Trả lời sai kiến thức học thuật.
- Không có nguồn tham chiếu rõ ràng.

Điều này đặc biệt nguy hiểm trong môi trường giáo dục.

---

### 2. Thiếu khả năng truy xuất tài liệu học tập

LLM thường không được huấn luyện trên:

- Giáo trình riêng.
- Slide bài giảng.
- Tài liệu môn học.
- Nội dung nội bộ trường học.

Do đó khó trả lời chính xác các câu hỏi học thuật chuyên biệt.

---

### 3. Thiếu tổng quan nghiên cứu

Mặc dù có rất nhiều nghiên cứu:

```text
RAG for Education
```

nhưng các công trình vẫn còn phân tán.

Chưa có một nghiên cứu tổng hợp toàn diện về:

- Educational Chatbots.
- AI Tutors.
- Academic Question Answering.
- RAG Applications in Education.

---

Bài báo hướng tới mục tiêu:

> Tổng hợp và phân tích các nghiên cứu sử dụng Retrieval-Augmented Generation trong giáo dục nhằm xác định xu hướng phát triển, kiến trúc phổ biến, lợi ích, thách thức và khoảng trống nghiên cứu hiện nay.



---

## Method

Bài báo dùng phương pháp/model/hệ thống nào?

Bài báo sử dụng:

# Systematic Literature Review (SLR)

Tác giả thực hiện:

### Literature Collection

Thu thập các nghiên cứu từ:

- Scopus
- Web of Science
- IEEE
- ACM
- Springer
- Elsevier

---

### Screening Process

Lọc các nghiên cứu liên quan đến:

```text
RAG
+
Education
+
Chatbots
+
LLMs
```

---

### Categorization

Các nghiên cứu được phân nhóm theo:

### 1. Educational Chatbots

Chatbot hỗ trợ học tập.

### 2. AI Tutors

Gia sư AI.

### 3. Question Answering Systems

Hệ thống hỏi đáp học thuật.

### 4. Personalized Learning

Học tập cá nhân hóa.

### 5. Knowledge Retrieval Systems

Hệ thống truy xuất tri thức học tập.

---

### Survey Framework

Bài báo phân tích:

```text
Educational Documents
↓
Retrieval
↓
LLM
↓
Answer Generation
```

và so sánh các kiến trúc RAG khác nhau trong giáo dục.



---

## Dataset

Bài báo dùng dữ liệu gì?

Đây là:

# Survey Paper

nên không sử dụng dataset riêng để huấn luyện.

Thay vào đó nghiên cứu tổng hợp:

```text
47 Educational RAG Studies
```

bao gồm:

- AI Tutor Systems
- Educational QA Systems
- Learning Assistants
- Course-specific Chatbots
- Academic Retrieval Systems

---

Các nghiên cứu được khảo sát sử dụng nhiều loại dữ liệu:

- PDF học tập
- Lecture Notes
- Syllabus
- Textbooks
- Course Materials
- Learning Resources



---

## Evaluation

Bài báo đánh giá bằng metric nào?

Vì là Survey Paper nên bài báo không đánh giá trực tiếp một mô hình cụ thể.

Thay vào đó phân tích các metric phổ biến được sử dụng trong các nghiên cứu Educational RAG:

### QA Metrics

- Accuracy
- Exact Match (EM)
- F1 Score

---

### Retrieval Metrics

- Recall
- Precision
- Retrieval Relevance

---

### Educational Metrics

- Student Satisfaction
- Learning Effectiveness
- User Engagement

---

### System Metrics

- Response Time
- Hallucination Rate
- Citation Accuracy



---

## Results

Kết quả chính là gì?

Bài báo chỉ ra rằng:

# RAG đang trở thành kiến trúc chủ đạo cho Educational AI Systems.

---

### 1. Significant Reduction of Hallucination

Các hệ thống:

```text
RAG-based Educational Chatbots
```

giảm đáng kể hallucination so với:

```text
LLM-only Systems
```

---

### 2. Better Academic Grounding

RAG giúp:

- Trả lời dựa trên tài liệu học tập.
- Tăng độ tin cậy.
- Cung cấp nguồn tham khảo.

---

### 3. Support for Personalized Learning

Nhiều nghiên cứu cho thấy RAG có thể hỗ trợ:

- Adaptive Learning.
- Personalized Recommendations.
- Student-specific Guidance.

---

### 4. Growing Research Trend

Số lượng nghiên cứu:

```text
Educational RAG
```

tăng mạnh từ năm 2023 đến 2025.

---

### Main Conclusion

Tác giả kết luận:

> Retrieval-Augmented Generation là một trong những hướng tiếp cận tiềm năng nhất để xây dựng các hệ thống hỗ trợ học tập thông minh trong tương lai.



---

## Limitations

Hạn chế của bài báo là gì?

### 1. Chỉ là Survey Paper

Bài báo:

```text
Không đề xuất mô hình mới
```

mà chủ yếu tổng hợp các nghiên cứu hiện có.

---

### 2. Phụ thuộc vào chất lượng nghiên cứu được khảo sát

Nếu các nghiên cứu nguồn có hạn chế:

thì kết luận tổng hợp cũng bị ảnh hưởng.

---

### 3. Chưa có Benchmark thống nhất

Bài báo chỉ ra rằng:

Các nghiên cứu Educational RAG hiện nay sử dụng:

- Dataset khác nhau.
- Metric khác nhau.
- Kiến trúc khác nhau.

nên khó so sánh trực tiếp.

---

### 4. Chưa giải quyết hoàn toàn Hallucination

Dù RAG giúp giảm hallucination nhưng:

```text
Bad Retrieval
→ Bad Answer
```

vẫn là vấn đề lớn.



---

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?

Mức độ liên quan:

# Cực kỳ cao (Literature Review Foundation Paper)

Đề tài:

**AI Study Hub – Hệ thống hỏi đáp tài liệu học tập ứng dụng RAG**

Đây là paper gần như phù hợp nhất để viết:

```text
Chapter 2
Literature Review
```

vì nó tổng hợp trực tiếp:

```text
Educational RAG Systems
```

---

Khác với:

- DPR
- RAG
- DR-RAG
- CRAG
- Self-RAG

là các paper kỹ thuật,

paper này tập trung vào:

```text
Ứng dụng RAG trong giáo dục
```

chính là domain của AI Study Hub.

---

Paper giúp chứng minh:

> Việc áp dụng Retrieval-Augmented Generation trong môi trường học tập là xu hướng nghiên cứu mạnh và có giá trị thực tiễn cao.

---

Ngoài ra paper còn cung cấp:

- Research Trends
- Research Gaps
- Existing Educational Systems
- Future Research Directions

rất phù hợp để trích dẫn trong phần:

```text
Related Works
```

của AI Study Hub.

---

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?

### 1. Vietnamese Educational RAG

Phần lớn nghiên cứu khảo sát:

```text
English Educational Systems
```

AI Study Hub có thể mở rộng theo hướng:

```text
Vietnamese Academic RAG
```

---

### 2. Advanced Retrieval

Kết hợp:

```text
DPR
+
DR-RAG
+
CRAG
```

để cải thiện Retrieval Quality.

---

### 3. Self-Evaluation Layer

Kết hợp:

```text
Self-RAG
```

giúp:

- Kiểm tra câu trả lời.
- Giảm hallucination.
- Tăng citation accuracy.

---

### 4. Personalized Learning Assistant

Theo dõi:

```text
Student Learning History
```

để:

- Gợi ý tài liệu.
- Đề xuất quiz.
- Xây dựng lộ trình học tập.

---

### 5. Hướng nghiên cứu cho AI Study Hub

So sánh:

```text
ChatGPT
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
- Citation Accuracy
- Student Satisfaction
- Response Time

để chứng minh AI Study Hub phù hợp với môi trường giáo dục hơn các chatbot AI tổng quát.