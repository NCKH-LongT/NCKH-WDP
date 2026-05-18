# Paper 03 Summary

## Citation

Tên bài:
A Systematic Comparison of Large Language Models for Automated Assignment Assessment in Programming Education: Exploring the Importance of Architecture and Vendor

Tác giả:
Research Group on AI-based Programming Assessment

Năm:
2026

Nguồn:
Computers and Education: Artificial Intelligence (Q1 Journal)

DOI/Link:
Link
https://www.sciencedirect.com/science/article/pii/S2666557326000364

---

## Problem

Bài báo nghiên cứu sự khác biệt giữa nhiều Large Language Models trong automated grading bài lập trình.

Mục tiêu chính:

- xem model architecture ảnh hưởng thế nào đến grading quality,
- so sánh các AI vendors,
- đánh giá mức độ agreement với human grading.

---

## Method

Bài báo benchmark 18 LLM khác nhau từ:

- OpenAI,
- Anthropic,
- Google,
- DeepSeek.

Bao gồm:

- GPT-4.1,
- GPT-4o,
- GPT-5 variants,
- Claude,
- Gemini,
- DeepSeek.

Hệ thống sử dụng automated assignment assessment workflow.

---

## Dataset

Dataset gồm:

- hơn 6,000 student submissions,
- dữ liệu trong 4 năm của introductory programming courses.

---

## Evaluation

Bài báo sử dụng:

- statistical tests,
- correlation analysis,
- clustering,
- grade distribution analysis,
- Intraclass Correlation Coefficient (ICC),
- variability analysis.

---

## Results

Kết quả chính:

- các model có high internal agreement với model consensus,
- nhưng chỉ moderate agreement với điểm giáo viên,
- model architecture và vendor ảnh hưởng rõ ràng đến grading behavior,
- không có model nào thay thế hoàn toàn human grading.

---

## Limitations

Hạn chế:

- chỉ tập trung vào educational grading,
- không hỗ trợ competition workflows,
- không tích hợp repository analytics,
- không xử lý collaborative projects,
- chưa đánh giá realtime repository monitoring.

---

## Relevance to our topic

Bài báo rất quan trọng cho SEAL vì:

- giúp lựa chọn AI model phù hợp,
- hỗ trợ benchmark nhiều model,
- chứng minh AI không nên thay thế hoàn toàn human judges,
- hỗ trợ nghiên cứu AI-human grading agreement.

SEAL có thể áp dụng:

- lưu AI score theo từng model,
- so sánh AI score với human score,
- benchmark nhiều AI providers,
- hỗ trợ configurable AI provider system.

---

## Possible improvement

Nhóm có thể mở rộng bằng cách:

- tích hợp GitHub repository analytics,
- hỗ trợ hackathon competition workflow,
- thêm rubric-based evaluation,
- hỗ trợ realtime webhook processing,
- kết hợp repository activity với AI grading,
- xây dựng AI-assisted competition evaluation platform.