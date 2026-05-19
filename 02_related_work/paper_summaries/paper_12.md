# Paper 12 Summary

### Citation
- **Tên bài:** LLM-based Automated Grading with Human-in-the-Loop
- **Tác giả:** Hang Li, Yucheng Chu, Kaiqi Yang, Yasemin Copur-Gencturk, Jiliang Tang
- **Năm:** 2025
- **Nguồn:** arXiv preprint
- **DOI:** 10.48550/arXiv.2504.05239

### Problem
Bài nghiên cứu automated short-answer grading và nhấn mạnh rằng LLM fully automated vẫn khó đạt human-level trong rubric-based assessment. Rubric có thể mơ hồ, AI có thể hiểu sai hoặc thiếu domain-specific insight.

### Method
Bài đề xuất GradeHITL, một human-in-the-loop framework. LLM đặt câu hỏi cho human experts, lấy insight từ con người và dùng để refine grading rubrics dynamically. Trọng tâm không phải source code mà là cách giữ human trong vòng lặp để tăng chất lượng rubric-based grading.

### Dataset / Context
Automatic short-answer grading, không phải programming assignments.

### Evaluation
Đánh giá bằng grading accuracy và mức độ cải thiện so với LLM-powered fully automated grading.

### Results
GradeHITL cho thấy human insight có thể giúp cải thiện rubric và đưa automated grading đến gần human-level hơn.

### Limitations
- Không phải source code grading.
- Không có GitHub/repository.
- Không có contest ranking.

### Relevance to our topic
Mức độ liên quan: **Trung bình cao về phương pháp, trung bình về domain**. Dùng để biện luận vì sao AI không nên thay judge.

### Possible improvement for our system
Áp dụng vào **Human-in-the-loop Review**:
- Nếu judge override AI nhiều lần ở cùng criterion, hệ thống đánh dấu criterion đó mơ hồ.
- Admin cải tiến rubric description/prompt version sau.

---

---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
