# Paper 06 Summary

### Citation
- **Tên bài:** Hands-on Analysis of Using Large Language Models for the Auto Evaluation of Programming Assignments
- **Năm:** 2024
- **Nguồn:** Information and Software Technology / ScienceDirect
- **DOI:** 10.1016/j.infsof.2024.107657

### Problem
Bài nghiên cứu việc dùng LLM để tự động đánh giá programming assignments. Vấn đề chính là cần biết LLM có thể đánh giá code về correctness, quality, style và best practices ổn định hay không.

### Method
Bài dùng nhiều LLM để auto-evaluate programming assignments và chạy nhiều iterations cho mỗi model nhằm đo consistency. Đây là điểm quan trọng vì LLM có thể không ổn định giữa các lần chạy.

### Dataset / Context
Programming assignments trong giáo dục lập trình. Bối cảnh gần với hệ thống nhóm vì đều là source code cần đánh giá, nhưng không phải hackathon.

### Evaluation
Bài đánh giá exact match, ±1 accuracy và consistency qua 10 iterations cho mỗi model.

### Results
Theo thông tin ScienceDirect, Gemini 1.5 Pro đạt exact match 86% và ±1 accuracy 98%; GPT-4o đạt exact match 69% và ±1 accuracy 97% trong thí nghiệm được mô tả.

### Limitations
- Không tập trung vào predefined dynamic rubric.
- Không có human-in-the-loop workflow rõ như TA Buddy.
- Không đánh giá ranking/leaderboard.

### Relevance to our topic
Mức độ liên quan: **Cao** cho reliability. Bài này giúp nhóm thêm bước consistency check khi AI chấm điểm.

### Possible improvement for our system
Áp dụng vào **AI Consistency Check**:
- Cùng một code + rubric, chạy AI 2 lần.
- Nếu lệch quá ngưỡng, đánh dấu `needsHumanReview = true`.
- Có thể đo score variance như một metric nghiên cứu.

---

---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
