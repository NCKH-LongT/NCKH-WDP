# Paper 01 Summary

### Citation
- **Tên bài:** Implementing AI-Based Code Review Automation: A Case Study in Academic Software Development
- **Tác giả:** Omar Isam AL Mrayat, Dyala Ibrahim, Malik Jawarneh
- **Năm:** 2025
- **Nguồn:** International Journal of Artificial Intelligence Applications
- **DOI/Link:** Link trong Google Sheet

### Problem
Bài báo giải quyết vấn đề review code thủ công trong môi trường học thuật. Review code thủ công thường tốn thời gian, phụ thuộc vào kinh nghiệm người review, dễ bỏ sót lỗi và thiếu nhất quán giữa các reviewer. Mục tiêu của bài là xây dựng một hệ thống AI-assisted code review để hỗ trợ phát hiện lỗi, kiểm tra coding standard và đánh giá chất lượng code.

### Method
Bài sử dụng hướng tiếp cận AI-based code review, kết hợp mô hình GPT-4/transformer với các công cụ static analysis như Pylint, Flake8, Checkstyle. Hệ thống kiểm tra các lỗi cú pháp, lỗi ngữ nghĩa, coding standards, design/implementation patterns và sinh feedback cho developer/student.

### Dataset / Context
Bối cảnh là academic software development, gồm các student projects hoặc programming assignments trong môi trường Computer Science. Đây không phải bối cảnh cuộc thi lập trình và cũng không phải hệ thống leaderboard.

### Evaluation
Đánh giá chủ yếu dựa trên khả năng phát hiện vấn đề trong code, giảm thời gian review, so sánh với công cụ truyền thống và phản hồi từ người dùng/developer. Không có metric ranking hoặc AI-human rubric score alignment rõ như đề tài nhóm.

### Results
Bài cho thấy AI có thể hỗ trợ review code nhanh hơn và giúp phát hiện các vấn đề về code quality. Kết quả phù hợp để chứng minh AI có thể hỗ trợ kiểm tra source code trước khi judge chấm theo rubric.

### Limitations
- Không tập trung vào predefined rubric scoring.
- Không tập trung vào contest/hackathon ranking.
- Không có human judge accept/override workflow rõ.
- Nguồn học thuật yếu hơn các bài ACM/Elsevier/Springer.

### Relevance to our topic
Mức độ liên quan: **Trung bình thấp**. Bài này nên dùng làm **background** cho AI code review và static analysis, không nên xem là core paper.

### Possible improvement for our system
Áp dụng vào bước **Code Preprocessing / Static Analysis**: trước khi gửi code cho AI chấm theo rubric, hệ thống có thể chạy static analysis để phát hiện syntax issues, coding standard violations, code smells và gộp kết quả này vào prompt AI.

---

---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
