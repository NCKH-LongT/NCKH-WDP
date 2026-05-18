# Paper 06 Summary

## Citation

Tên bài:  
JorGPT: Instructor-Aided Grading of Programming Assignments with Large Language Models (LLMs)

Tác giả:  
Unknown

Năm:  
2025

Nguồn:  
Future Internet, Volume 17, Issue 6, Article 265 (JCR Q2)

DOI/Link:  
Link
https://www.mdpi.com/1999-5903/17/6/265

---

## Problem

Bài báo giải quyết vấn đề chấm bài lập trình thủ công trong môi trường giáo dục đại học.

Các khó khăn chính gồm:

- instructor mất nhiều thời gian để grading source code,
- grading dễ thiếu tính nhất quán,
- khó đánh giá đồng đều giữa nhiều submissions,
- traditional autograders chỉ đánh giá output/test cases,
- khó đánh giá các yếu tố qualitative như:
  - readability,
  - documentation,
  - programming style,
  - maintainability,
  - requirement compliance.

Mục tiêu của bài báo là xây dựng một hệ thống hỗ trợ giảng viên chấm source code bằng Large Language Models (LLMs).

---

## Method

Bài báo đề xuất hệ thống JorGPT — một instructor-aided grading platform sử dụng Large Language Models.

### AI Method

Hệ thống sử dụng:

- Large Language Models (LLMs),
- instructor-aided grading workflow,
- customizable grading rubric.

### Workflow

Input của hệ thống gồm:

- programming assignment,
- source code submission,
- grading rubric.

Instructor có thể:

- chọn AI model,
- tùy chỉnh rubric,
- xem AI-generated evaluation.

### Rubric Criteria

Bài báo sử dụng assessment instrument gồm:

- logical correctness,
- code documentation,
- computational efficiency,
- readability,
- programming style,
- compliance with assignment requirements.

---

## Dataset

Dataset gồm:

- undergraduate programming assignments,
- source code submissions trong môn “Introduction to Programming”.

Bối cảnh nghiên cứu thuộc:

- programming education,
- academic grading systems.

---

## Evaluation

Bài báo đánh giá hệ thống bằng:

- statistical analysis,
- AI-human grading comparison.

Các metrics chính gồm:

- adjusted R²,
- Mean Absolute Error (MAE).

Mục tiêu là đo khả năng:

- LLM tái hiện human grading,
- agreement giữa AI-generated grades và instructor grades.

---

## Results

Kết quả chính:

- adjusted R² = 0.9156,
- MAE = 0.4579.

Kết quả cho thấy:

- LLM có khả năng mô phỏng human grading ở mức tốt,
- AI-generated grading có độ tương quan cao với instructor grading,
- instructor-aided workflow giúp giảm workload trong grading process.

Ngoài ra bài báo còn cho thấy:

- rubric-based evaluation giúp AI grading ổn định hơn,
- configurable rubric hỗ trợ flexible grading workflow.

---

## Limitations

Hạn chế của bài báo:

- chỉ tập trung vào educational programming assignments,
- chưa áp dụng cho programming competitions hoặc hackathons,
- không hỗ trợ collaborative repository evaluation,
- không tích hợp GitHub repository analytics,
- không xử lý realtime repository monitoring,
- chưa benchmark nhiều AI providers khác nhau,
- AI vẫn chưa thay thế hoàn toàn human grading.

---

## Relevance to our topic

Bài báo rất liên quan đến đề tài SEAL vì:

- sử dụng LLM để hỗ trợ source code evaluation,
- hỗ trợ rubric-based grading,
- có human-in-the-loop workflow,
- hỗ trợ AI-human collaborative evaluation.

SEAL có thể học hỏi từ bài báo về:

- thiết kế grading rubric,
- AI-assisted judging workflow,
- AI-human score comparison,
- rubric customization system.

Các rubric dimensions trong bài báo rất hữu ích cho SEAL:

- correctness,
- documentation,
- efficiency,
- readability/style,
- requirement compliance.

Ngoài ra bài báo còn hỗ trợ ý tưởng:

- judge dashboard với AI suggestions,
- configurable AI provider system,
- AI-generated criterion scoring.

---

## Possible improvement

SEAL có thể mở rộng thêm bằng cách:

- tích hợp GitHub repository tracking,
- hỗ trợ collaborative project evaluation,
- xử lý realtime GitHub webhooks,
- phân tích commit activity,
- benchmark nhiều AI models,
- hỗ trợ competition ranking workflows,
- thêm repository analytics dashboard,
- lưu AI score theo từng provider/model,
- so sánh AI score với human judge score.

Ngoài ra SEAL có thể kết hợp:

- repository mining,
- AI-assisted code review,
- rubric-based evaluation,
- realtime competition monitoring

để xây dựng một AI-assisted hackathon evaluation platform hoàn chỉnh hơn.