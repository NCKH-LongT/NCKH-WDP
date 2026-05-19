# Paper 04 Summary

### Citation
- **Tên bài:** JorGPT: Instructor-Aided Grading of Programming Assignments with Large Language Models (LLMs)
- **Tác giả:** Jorge Cisneros-González, Natalia Gordo-Herrera, Iván Barcia-Santos, Javier Sánchez-Soriano
- **Năm:** 2025
- **Nguồn:** Future Internet, 17(6), 265
- **DOI:** 10.3390/fi17060265

### Problem
Bài báo giải quyết vấn đề chấm bài lập trình thủ công tốn thời gian, dễ thiếu nhất quán và khó mở rộng khi số lượng bài nộp lớn. Dù rubric giúp chuẩn hóa đánh giá, manual grading vẫn dễ bị ảnh hưởng bởi fatigue, khác biệt tiêu chí giữa người chấm và khối lượng bài lớn.

### Method
JorGPT là hệ thống instructor-aided grading dùng nhiều LLM từ OpenAI, Google, DeepSeek và Alibaba. Hệ thống có giao diện cho instructor chọn model, tùy chỉnh grading rubric và xử lý student code submissions.

### Rubric / Criteria
Bài dùng rubric/assessment criteria như logical correctness, code documentation, computational efficiency, readability and programming style, compliance with assignment requirements.

### Dataset
Dữ liệu từ undergraduate “Introduction to Programming” course. Bài nghiên cứu đánh giá 672 student submissions và so sánh AI-generated grades với human instructor grades.

### Evaluation
Bài dùng phân tích thống kê, adjusted R², MAE, ANOVA, residual analysis; đồng thời phân tích qualitative feedback của LLM và execution time/cost.

### Results
Bài báo cáo mô hình reduced regression đạt **adjusted R² = 0.9156** và **MAE = 0.4579** trên thang 0–10. Tác giả cũng cho rằng quy trình có thể giảm workload từ hơn 300 giờ manual grading xuống dưới 15 phút automated processing trong bối cảnh nghiên cứu.

### Limitations
- Không phải contest/hackathon.
- Không đánh giá ranking alignment trực tiếp.
- Cần human oversight để giảm rủi ro bias hoặc lệch điểm.

### Relevance to our topic
Mức độ liên quan: **Rất cao** cho rubric design và evaluation metrics. Bài này giúp nhóm chọn metric MAE, correlation/R², execution time và cost.

### Possible improvement for our system
Áp dụng vào module **Evaluation Plan**:
- So sánh AI score với judge score bằng MAE/Pearson.
- Đo time reduction.
- Đo cost khi gọi AI API.
- Ghi nhận judge override rate.

---

### Detailed application to our project
JorGPT phù hợp để nhóm thiết kế phần **evaluation plan**. Bài này cho thấy hệ thống chấm bằng LLM cần đo không chỉ điểm số mà còn độ tương đồng với người chấm, thời gian xử lý và chi phí gọi model.

#### What to reuse
- Rubric dimensions: logical correctness, documentation, efficiency, readability/style, requirement compliance.
- Human oversight: AI không nên quyết định điểm cuối.
- Metrics: MAE, correlation/R², processing time, model comparison.

#### Suggested project metrics inspired by JorGPT
| Metric | Mục đích |
|---|---|
| MAE | Đo AI lệch judge bao nhiêu điểm |
| Pearson correlation / R² | Đo AI score có cùng xu hướng với judge score không |
| Time reduction | Đo AI giúp giảm thời gian chấm không |
| Human override rate | Đo judge phải sửa AI bao nhiêu lần |
| Cost per evaluation | Ước lượng chi phí gọi model/API |


---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
