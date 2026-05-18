# Paper 02 Summary

## Citation

Tên bài:
TRACE: AI-Assisted Assessment of Collaborative Projects in Computer Science Education

Tác giả:
Yu & Zagula

Năm:
2026

Nguồn:
Computer Science Education Research

DOI/Link:
Link
https://arxiv.org/pdf/2510.03998

---

## Problem

Bài báo tập trung vào vấn đề đánh giá công bằng project nhóm trong môi trường giáo dục ngành Computer Science.

Khó khăn chính:

- khó xác định đóng góp cá nhân,
- khó đánh giá project quality,
- grading collaborative projects mất nhiều thời gian,
- thiếu dữ liệu repository analytics.

---

## Method

Hệ thống TRACE sử dụng:

- repository mining,
- static analysis,
- NLP,
- AI-assisted analytics,
- GitHub API.

Hệ thống phân tích:

- commit history,
- contribution activity,
- test coverage,
- documentation,
- project quality metrics.

---

## Dataset

Dataset gồm:

- collaborative software projects,
- GitHub Classroom repositories,
- course project repositories.

---

## Evaluation

Bài báo đánh giá bằng:

- Pearson correlation giữa AI-generated grades và instructor grades,
- student perception,
- grading time reduction.

---

## Results

Kết quả chính:

- AI-assisted analytics hỗ trợ đánh giá project tốt hơn,
- giảm thời gian grading,
- hỗ trợ xác định contribution của từng thành viên,
- correlation với instructor grading ở mức tốt.

---

## Limitations

Hạn chế của bài báo:

- chưa áp dụng trực tiếp cho hackathon competitions,
- chưa hỗ trợ realtime competition workflow,
- chưa tích hợp AI code review sâu bằng LLM,
- focus chủ yếu vào educational context.

---

## Relevance to our topic

Bài báo rất hữu ích cho SEAL vì:

- sử dụng GitHub repository data,
- hỗ trợ repository evaluation,
- hỗ trợ dashboard analytics,
- hỗ trợ collaborative project assessment,
- có workflow gần với hackathon repository tracking.

SEAL có thể học từ bài báo này về:

- repository mining,
- contribution analysis,
- GitHub analytics,
- project quality metrics.

---

## Possible improvement

Nhóm có thể mở rộng bằng cách:

- thêm AI-assisted source code review bằng LLM,
- hỗ trợ hackathon competition ranking,
- xử lý realtime webhook events,
- tích hợp AI-generated rubric scoring,
- hỗ trợ competition dashboard và judge workflow.