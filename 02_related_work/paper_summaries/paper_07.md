## Paper 07 Summary

### Citation

- **Tên bài:** CodEv: An Automated Grading Framework Leveraging LLM for Feedback
- **Tác giả:** En-Qi Tseng, Pei-Cing Huang, Chan Hsu, et al.
- **Năm:** 2024
- **Nguồn:** IEEE BigData

### Problem

Các công cụ chấm code tĩnh bỏ qua tính dễ đọc (readability) và tư duy cấu trúc mã nguồn.

### Method

Dùng Zero-shot-CoT, yêu cầu AI bẻ nhỏ bộ tiêu chí tùy chỉnh (custom criteria) thành các bước nhỏ để chấm điểm và tạo nhận xét mang tính xây dựng.

### Dataset / Context

Bài nộp thực hành lập trình của sinh viên đại học.

### Evaluation

- **Chất lượng nhận xét (G-Eval):** Đánh giá tính xây dựng, độ chính xác và tính cụ thể của feedback.

### Results

- CodEv vượt trội so với phân tích tĩnh (SonarQube) trong việc đánh giá tài liệu và cấu trúc code.

### Limitations

- Việc thiết kế Prompt phức tạp, nhạy cảm với các thay đổi nhỏ trong câu chữ.

### Relevance to our topic

- **Mức độ liên quan:** Rất cao.
- **Lý do:** Hackathon không thể chạy Test Case (vì mỗi nhóm làm một sản phẩm khác nhau). Chỉ có thể chấm qua cấu trúc code và architecture.

### Possible improvement

- Sử dụng framework G-Eval để định hình lại bộ Prompt. Yêu cầu AI đưa ra "Feedback mang tính xây dựng" (Constructive feedback) để hiển thị cho sinh viên sau khi cuộc thi kết thúc.
