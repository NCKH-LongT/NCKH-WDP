# Paper 13 Summary

### Citation
- **Tên bài:** AI-based Automated Grading of Source Code of Introductory Programming Assignments
- **Tác giả:** Jayant Havare et al.
- **Năm:** 2025
- **Nguồn:** IEEE/ACM International Conference on Program Comprehension, ICPC 2025 Research Track
- **DOI/Link:** IBM Research / ICPC 2025 link trong sheet

### Problem
Bài giải quyết vấn đề chấm source code theo rubric ở quy mô lớn. Test-case-based autograding không đủ vì không cho partial marks tốt và không chấm được code quality hoặc yêu cầu đặc thù trong problem statement.

### Method
Bài dùng LLM for code để tự động chấm source code theo instructor-specified rubrics. Đây là hướng rất gần TA Buddy, nhưng nhấn mạnh hơn vào AI-based automated grading của source code.

### Rubric / Criteria
Rubric do instructor định nghĩa, dùng để chấm các tiêu chí cụ thể trong problem statement, partial correctness và source code quality.

### Dataset / Context
Introductory programming assignments. Một số nguồn ngoài cho biết thí nghiệm dùng large-scale submissions; nhóm cần đọc full paper nếu có PDF để ghi metric chính xác.

### Evaluation
Đánh giá khả năng LLM chấm source code theo rubric và so sánh với manual grading/TA grading. Nếu nhóm có full paper, cần bổ sung chính xác metric, dataset size và model.

### Results
Bài là bằng chứng mạnh rằng **LLM + source code + instructor rubric** là hướng nghiên cứu thực sự trong ICPC 2025, phù hợp để làm core reference cho đề tài.

### Limitations
- Không phải hackathon.
- Chưa chắc có ranking metrics.
- Cần full paper để lấy chi tiết số liệu nếu viết báo cáo chính thức.

### Relevance to our topic
Mức độ liên quan: **Rất cao — Core paper**. Đây là một trong những bài sát nhất cho module AI source code grading.

### Possible improvement for our system
Dùng làm nền tảng cho module **AI Source Code Scoring**:
- dynamic rubric từ MongoDB
- code snapshot/diff từ GitHub
- LLM chấm từng criterion
- judge review
- final score/ranking.

---

### Detailed application to our project
Bài này là core reference cho hướng **LLM + source code + instructor-specified rubric**. Nếu nhóm cần bảo vệ rằng đề tài có cơ sở học thuật rõ ràng, bài này nên được trích dẫn cùng TA Buddy.

#### Minimum feature inspired by this paper
- Rubric có thể cấu hình bởi Admin/BTC.
- AI không chỉ chạy test case mà đọc source code/diff.
- AI cho partial score theo từng rubric criterion.
- Judge xác nhận điểm cuối.

#### Research extension for our system
Dự án có thể bổ sung metric ranking mà bài gốc chưa nhấn mạnh:
- Spearman rank correlation giữa AI ranking và human ranking.
- Top-k agreement để xem AI có chọn đúng đội vào chung kết không.


---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
