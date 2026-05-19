# Paper 05 Summary

### Citation
- **Tên bài:** A Systematic Comparison of Large Language Models for Automated Assignment Assessment in Programming Education: Exploring the Importance of Architecture and Vendor
- **Tác giả:** Marcin Jukiewicz
- **Năm:** 2026
- **Nguồn:** Computers and Education: Artificial Intelligence / ScienceDirect / Elsevier
- **DOI/Link:** Link trong Google Sheet

### Problem
Bài báo trả lời câu hỏi: khi dùng LLM để chấm bài lập trình, model architecture và vendor có ảnh hưởng đến kết quả không? Đây là vấn đề quan trọng vì cùng một submission có thể được các model khác nhau chấm nghiêm hoặc dễ khác nhau.

### Method
Bài so sánh 18 LLM từ Anthropic, DeepSeek, Google và OpenAI. Nghiên cứu phân tích grade distribution, mean scores, variability, correlations, clustering và intraclass correlation coefficient.

### Dataset
Hơn 6,000 student submissions được thu thập trong 4 năm của một introductory programming course.

### Evaluation
Dùng statistical tests, correlation, clustering analysis, grade distribution, variability và ICC để so sánh giữa các model và với human teacher grades.

### Results
Bài cho thấy các model có internal agreement cao với model consensus, nhưng chỉ moderate agreement với human teachers’ grades. Mini/nano variants thường kém hơn full-scale counterparts. Kết luận quan trọng: model selection không trung lập và cần human oversight.

### Limitations
- Không tập trung vào dynamic rubric workflow.
- Không triển khai hệ thống hackathon.
- Không trực tiếp đo contest leaderboard.

### Relevance to our topic
Mức độ liên quan: **Cao — Core-supporting paper**. Dùng để biện luận không nên chọn model ngẫu nhiên; cần benchmark hoặc ít nhất lưu model/version và có human review.

### Possible improvement for our system
Áp dụng vào **Model Selection / Reliability Check**:
- So sánh GPT/Gemini/Claude nếu có điều kiện.
- Nếu chỉ dùng một model, phải ghi rõ model/version.
- Đo AI-human alignment và ranking agreement.

---

---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
