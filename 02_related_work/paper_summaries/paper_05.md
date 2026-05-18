# Paper 05 Summary

## Citation

Tên bài:
Implementing AI-Based Code Review Automation: A Case Study in Academic Software Development

Tác giả:
AL Mrayat, Ibrahim & Jawarneh

Năm:
2025

Nguồn:
Academic Software Development Research

DOI/Link:
Link
https://ijaia.com/index.php/IJAIA/article/view/65/10

---

## Problem

Bài báo tập trung vào vấn đề review source code trong môi trường đại học và software engineering education.

Các vấn đề chính gồm:

- quá trình code review thủ công mất nhiều thời gian,
- thiếu tính nhất quán giữa các reviewer,
- khó review số lượng lớn student assignments,
- instructor khó phát hiện đầy đủ code issues trong thời gian ngắn,
- static analysis tools truyền thống chưa đủ để tạo feedback chi tiết cho sinh viên.

Mục tiêu của bài báo là:

- tự động hóa một phần quy trình code review,
- giảm thời gian review,
- cải thiện consistency trong feedback.

---

## Method

Bài báo sử dụng AI-assisted code review pipeline kết hợp:

### AI Models

- GPT-4 / transformer-based models

### Static Analysis Tools

- Pylint
- Flake8
- Checkstyle

### Workflow

Pipeline tổng quát:

Static Analysis
→ GPT-4 Analysis
→ AI-generated Feedback
→ Instructor Validation

Hệ thống sử dụng:

- coding standards,
- static analysis reports,
- source code input,
- AI-generated explanations.

AI hỗ trợ:

- issue detection,
- feedback generation,
- coding standard review,
- maintainability suggestions.

---

## Dataset

Dataset gồm:

- 150 student projects,
- 450 programming assignments,
- computer science courses.

Dữ liệu bao gồm:

- source code submissions,
- static analysis outputs,
- instructor reviews.

---

## Evaluation

Bài báo đánh giá hệ thống bằng:

- issue detection accuracy,
- review time reduction,
- student feedback,
- instructor observations.

Ngoài ra bài báo còn xem xét:

- consistency của generated feedback,
- usefulness của AI-generated comments.

---

## Results

Kết quả chính:

- giảm đáng kể thời gian review source code,
- AI-generated feedback giúp tăng consistency,
- AI hỗ trợ phát hiện nhiều coding issues hơn static analysis đơn thuần,
- instructor đánh giá workflow hữu ích trong academic environments,
- student feedback tích cực hơn khi nhận được detailed explanations.

Bài báo cũng cho thấy:

- AI hoạt động tốt nhất khi kết hợp với static analysis tools,
- human validation vẫn cần thiết để đảm bảo accuracy.

---

## Limitations

Hạn chế của bài báo:

- không sử dụng rubric-based grading rõ ràng,
- chủ yếu tập trung vào academic assignments,
- chưa hỗ trợ collaborative repository evaluation,
- chưa tích hợp GitHub repository analytics,
- chưa hỗ trợ realtime webhook processing,
- AI chưa thể thay thế hoàn toàn instructor review,
- chưa áp dụng cho hackathon hoặc programming competition workflows.

---

## Relevance to our topic

Bài báo rất liên quan đến đề tài SEAL vì:

- sử dụng AI-assisted code review,
- kết hợp static analysis với LLM,
- có human-in-the-loop workflow,
- hỗ trợ source code evaluation.

SEAL có thể áp dụng pipeline tương tự:

Static Analysis
→ AI Review
→ Judge Validation
→ Final Evaluation

Bài báo giúp xác nhận rằng:

- AI có thể giảm review workload,
- AI-generated feedback hữu ích cho evaluation,
- kết hợp static analysis + LLM hiệu quả hơn chỉ dùng một phương pháp.

Ngoài ra bài báo còn hỗ trợ ý tưởng:

- AI-assisted judge dashboard,
- repository evaluation workflow,
- code quality analytics.

---

## Possible improvement

SEAL có thể mở rộng mạnh hơn bằng cách:

- tích hợp GitHub repository tracking,
- hỗ trợ realtime GitHub webhook processing,
- đánh giá collaborative projects,
- thêm rubric-based scoring,
- hỗ trợ AI-generated criterion scores,
- phân tích commit activity,
- benchmark nhiều AI providers,
- hỗ trợ competition ranking workflows,
- xây dựng AI-assisted hackathon evaluation platform.

SEAL cũng có thể cải tiến bằng cách:

- lưu AI review history,
- so sánh AI score với human judge score,
- hỗ trợ configurable AI provider system,
- hỗ trợ repository-level analytics thay vì chỉ assignment-level review.