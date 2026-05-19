# Paper 10 Summary

### Citation
- **Tên bài:** BeGrading: Large Language Models for Enhanced Feedback in Programming Education
- **Tác giả:** Mina Yousef et al.
- **Năm:** 2024/2025 online publication
- **Nguồn:** Neural Computing and Applications, Springer
- **DOI:** 10.1007/s00521-024-10449-y

### Problem
Bài nghiên cứu việc dùng LLM để tự động hóa grading programming assignments và cung cấp feedback kịp thời, khách quan cho sinh viên. Manual grading tốn thời gian và feedback thường chậm.

### Method
BeGrading là một customized/fine-tuned LLM cho grading programming assignments. Bài dùng real data và synthetic data để huấn luyện, đồng thời so sánh với các model như Codestral, GPT-4o, Gemini.

### Dataset
Dataset gồm 3,470 samples từ Nile University assignments và 374 questions từ sách có đáp án/model answers. Dữ liệu được augment để bao phủ nhiều grading levels.

### Evaluation
Đánh giá độ lệch điểm so với model/human/optimized dataset score, so sánh với Codestral và các LLM khác.

### Results
Abstract báo cáo BeGrading có absolute difference rate 19%, tương đương ±0.95/5; Codestral so với dataset optimized score có difference 15%, tương đương ±0.75/5. Kết quả cho thấy LLM fine-tuned nhỏ có tiềm năng grading đáng tin cậy.

### Limitations
- Không tập trung predefined rubric/ranking.
- Fine-tuning cần dataset lớn.
- Không trực tiếp có human judge accept/override workflow.

### Relevance to our topic
Mức độ liên quan: **Trung bình cao cho feedback/future work**. Không nên làm MVP nhưng rất tốt để viết hướng phát triển.

### Possible improvement for our system
Sau vài mùa thi, nhóm có thể dùng dữ liệu thật: source code + rubric + judge score + judge comment để fine-tune/calibrate AI grader riêng cho hackathon.

---

### Detailed application to our project
BeGrading phù hợp cho phần **future work** hơn là MVP. Bài này cho thấy có thể fine-tune hoặc customize LLM cho grading nếu có đủ dữ liệu bài nộp và điểm tương ứng.

#### Future work for our hackathon system
Sau vài mùa thi, hệ thống có thể thu thập:
- Source code hoặc repository snapshot.
- Rubric version.
- AI suggested scores.
- Judge final scores.
- Judge comments.
- Ranking results.

Từ đó nhóm có thể xây dựng dataset riêng cho SEAL Hackathon và fine-tune/calibrate model để chấm sát tiêu chuẩn của cuộc thi hơn.


---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
