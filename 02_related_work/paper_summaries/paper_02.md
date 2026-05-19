# Paper 02 Summary

### Citation
- **Tên bài:** TRACE: AI-Assisted Assessment of Collaborative Projects in Computer Science Education
- **Tác giả:** Yu & Zagula
- **Năm:** 2026
- **Nguồn:** arXiv preprint
- **DOI/Link:** Link trong Google Sheet

### Problem
Bài báo giải quyết vấn đề đánh giá project nhóm trong giáo dục khoa học máy tính. Trong project nhóm, giảng viên khó đánh giá công bằng chất lượng project và đóng góp cá nhân vì dữ liệu nằm rải rác trong GitHub, commits, issues, pull requests, README, documentation và quá trình cộng tác.

### Method
TRACE sử dụng repository mining, static analysis, NLP, AI-assisted analytics và GitHub API để đánh giá project quality và individual contribution. Hệ thống phân tích repository, activity logs và artifacts của project để sinh điểm hoặc dashboard hỗ trợ instructor review.

### Rubric / Criteria
Các tiêu chí có thể liên hệ với rubric gồm code quality, test coverage, documentation, functionality, usability và contribution. Bài không phải rubric-based grading thuần túy, nhưng tiêu chí có thể được cấu hình trọng số theo mục tiêu môn học.

### Dataset / Context
Bối cảnh là collaborative software projects trong CS education, thường liên quan GitHub Classroom hoặc GitHub repositories. Đây không phải cuộc thi lập trình, nhưng rất gần với phần GitHub workflow của dự án nhóm.

### Evaluation
Đánh giá bằng cách so sánh AI-generated/project grades với instructor grades, kết hợp phân tích thời gian chấm, perception của sinh viên/giảng viên và tính minh bạch trong đánh giá.

### Results
TRACE cho thấy repository-based analytics có thể hỗ trợ đánh giá project nhóm và giảm workload cho instructor. Bài hữu ích để thiết kế dashboard GitHub tracking và project assessment.

### Limitations
- Là arXiv preprint, chưa chắc đã peer-reviewed.
- Tập trung project nhóm/course project, không phải contest/hackathon.
- Tập trung nhiều vào contribution cá nhân hơn là source code grading theo rubric.

### Relevance to our topic
Mức độ liên quan: **Trung bình cao** nếu hệ thống dùng GitHub repository. Bài này phù hợp cho nhánh GitHub Integration hơn là AI chấm rubric trực tiếp.

### Possible improvement for our system
Áp dụng vào module **GitHub Repository Analytics**: lấy commit count, file changes, test coverage, README, documentation và activity logs để hỗ trợ AI/judge đánh giá Git Activity, Documentation và Project Structure.

---

---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
