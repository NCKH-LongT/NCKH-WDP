# Paper 09 Summary

### Citation
- **Tên bài:** Automated Grading Method of Python Code Submissions Using Large Language Models and Machine Learning
- **Tác giả:** Mariam Mahdaoui, Said Nouh, My Seddiq El Kasmi Alaoui, Khalid Kandali
- **Năm:** 2025
- **Nguồn:** Information, MDPI, 16(8), 674
- **DOI:** 10.3390/info16080674

### Problem
Bài giải quyết bài toán chấm tự động Python submissions trong bối cảnh giáo dục lập trình, nơi chấm thủ công tốn nhiều công sức và thiếu nhất quán.

### Method
Bài kết hợp GPT-4-Turbo với machine learning. Workflow gồm automatic correction, similarity/static analysis, feature extraction và model dự đoán điểm. PyCaret được dùng để chọn mô hình ML. Extra Trees Regressor dùng cho điểm liên tục, Random Forest Classifier dùng cho phân loại mức điểm.

### Dataset
350 Python submissions từ SCW-ITS, được human evaluator chấm trên thang 0–100.

### Evaluation
Đánh giá bằng MAE, R² cho regression; accuracy và Quadratic Weighted Kappa cho classification.

### Results
Theo abstract MDPI, Extra Trees Regressor đạt MAE 4.43/100 và R² 0.83; Random Forest Classifier đạt accuracy 91% và Quadratic Weighted Kappa 0.84.

### Limitations
- Tập trung Python, không phải project/hackathon nhiều ngôn ngữ.
- Rubric không rõ theo từng criterion.
- Cần dataset điểm human để train/calibrate ML model.

### Relevance to our topic
Mức độ liên quan: **Cao nếu nhóm muốn hybrid scoring**, trung bình nếu MVP chỉ dùng LLM API.

### Possible improvement for our system
Future work: thu thập judge score qua nhiều mùa thi, sau đó dùng ML để calibrate AI score hoặc dự đoán final score từ static metrics + AI suggestions + judge history.

---

---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
