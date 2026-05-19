# Paper 08 Summary

### Citation
- **Tên bài:** A Comparative Study of Large Language Models in Programming Education: Accuracy, Efficiency, and Feedback in Student Assignment Grading
- **Năm:** 2025
- **Nguồn:** Applied Sciences, MDPI, 15(18), 10055
- **DOI:** 10.3390/app151810055

### Problem
Bài so sánh các LLM trong việc chấm bài lập trình, tập trung vào độ chính xác, hiệu quả và chất lượng feedback. Vấn đề là chưa rõ model nào phù hợp nhất cho grading programming assignments.

### Method
So sánh nhiều LLM như GPT-4/GPT-4 Turbo, Claude 3 và Gemini 1.5 Pro bằng structured prompts aligned with predefined rubric.

### Rubric / Criteria
Rubric gồm các tiêu chí như functionality, code structure, documentation và efficiency.

### Dataset
Dữ liệu từ Moodle/LMS với Python assignments thuộc các khóa Introduction to Programming, Programming 2 và Advanced Programming Concepts. Theo thông tin sheet, có 315 assignments và chọn 100 submissions để phân tích chi tiết.

### Evaluation
So sánh AI-generated grades với instructor-assigned grades; đánh giá accuracy, agreement, efficiency và feedback quality.

### Results
Bài cho thấy LLM có tiềm năng hỗ trợ grading nếu prompt/rubric được cấu trúc rõ. Đây là bài tốt để tham khảo cách chia experiment thành data preparation, rubric definition, AI-based evaluation và comparative analysis.

### Limitations
- Không phải cuộc thi lập trình.
- Ranking chưa phải metric chính.
- Cần kiểm tra kỹ setup nếu dùng kết quả làm bằng chứng chính.

### Relevance to our topic
Mức độ liên quan: **Rất cao** cho model comparison và rubric-based evaluation.

### Possible improvement for our system
Áp dụng vào **Model Comparison**:
- Dùng cùng một bộ submissions cho nhiều model chấm.
- So sánh model bằng MAE, correlation và ranking metrics.

---

---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
