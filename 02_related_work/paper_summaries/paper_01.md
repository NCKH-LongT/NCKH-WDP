# Paper 01 Summary

## Citation

Tên bài:
Design and Evaluation of an AI-Assisted Grading Tool for Introductory Programming Assignments: An Experience Report

Tác giả:
SIGCSE Research Group

Năm:
2025

Nguồn:
SIGCSE 2025 (CORE A Conference)

DOI/Link:
Link
https://dl.acm.org/doi/abs/10.1145/3641554.3701913

---

## Problem

Bài báo giải quyết vấn đề đánh giá bài tập lập trình trong các khóa học nhập môn lập trình.

Các hệ thống autograder truyền thống chỉ kiểm tra test case và output nhưng không đánh giá sâu các yếu tố như:

- code quality,
- readability,
- coding style,
- requirement compliance,
- maintainability.

Việc chấm thủ công của TA mất nhiều thời gian và thiếu tính nhất quán.

---

## Method

Bài báo đề xuất hệ thống TA Buddy – một AI-assisted grading tool sử dụng:

- Code Llama (LLM chuyên cho code),
- grading rubric,
- instructor-in-the-loop workflow.

Input của hệ thống gồm:

- problem statement,
- source code submission,
- grading rubric.

AI sẽ sinh:

- suggested score cho từng rubric criterion,
- feedback,
- grading explanation.

Human TA có thể:

- accept,
- reject,
- override kết quả AI.

---

## Dataset

Dataset gồm:

- bài tập lập trình nhập môn,
- student code submissions,
- grading rubric,
- human grading results.

Bối cảnh:

- introductory programming courses.

---

## Evaluation

Bài báo đánh giá hệ thống bằng:

- grading time reduction,
- agreement between AI-assisted grading and manual grading,
- instructor feedback.

---

## Results

Kết quả chính:

- thời gian chấm giảm khoảng 24%,
- AI-assisted grading đạt khoảng 90% grade agreement với manual grading,
- TA đánh giá workflow hỗ trợ grading hiệu quả hơn.

---

## Limitations

Hạn chế của bài báo:

- chỉ áp dụng cho programming assignments trong giáo dục,
- chưa áp dụng cho hackathon hoặc programming competition,
- AI vẫn cần human validation,
- chưa xử lý collaborative repository evaluation.

---

## Relevance to our topic

Bài báo rất liên quan đến đề tài SEAL vì:

- sử dụng rubric-based grading,
- dùng AI hỗ trợ chấm source code,
- có human-in-the-loop workflow,
- hỗ trợ judge review.

Workflow của bài báo gần giống với SEAL:

Problem statement + source code + rubric
→ AI suggested grades
→ Human judge review
→ Final evaluation.

Trong SEAL:

- “student assignment” được thay bằng “contestant submission”,
- “TA” được thay bằng “judge/coordinator”.

---

## Possible improvement

Nhóm có thể mở rộng bằng cách:

- tích hợp GitHub repository tracking,
- đánh giá collaborative projects,
- xử lý commit activity,
- thêm realtime webhook processing,
- hỗ trợ hackathon competition workflow,
- hỗ trợ AI review cho toàn bộ repository thay vì single assignment.