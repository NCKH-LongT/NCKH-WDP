## Paper 09 Summary

### Citation

- **Tên bài:** Code Comprehension: Review and Large Language Models Exploration
- **Tác giả:** Jielun Cui, Yutong Zhao, Chong Yu, et al.
- **Năm:** 2024
- **Nguồn:** 2024 IEEE SEAI

### Problem

Quá trình đọc hiểu dự án mã nguồn của người khác (Code Comprehension) mất rất nhiều thời gian, đặc biệt trong các hội đồng chấm thi.

### Method

Khảo sát các phương pháp đọc hiểu truyền thống và thử nghiệm thiết kế Prompt chuyên biệt để đo lường năng lực diễn giải kiến trúc mã nguồn của LLM.

### Dataset / Context

Lịch sử commit và docstrings từ các dự án mã nguồn mở Python.

### Evaluation

- **Độ chính xác của Tóm tắt (Summarization Accuracy):** Đánh giá chất lượng đoạn văn tóm tắt chức năng dự án.

### Results

- LLM có khả năng tóm tắt luồng hoạt động (Data flow) rất tốt nếu được cung cấp đủ file liên kết.

### Limitations

- Chủ yếu là nghiên cứu lý thuyết/khảo sát, chưa có một hệ thống ứng dụng cụ thể.

### Relevance to our topic

- **Mức độ liên quan:** Cao.
- **Lý do:** Một tính năng cực hay cho hệ thống là tự động tạo "Project Summary" cho giám khảo trước khi họ vào xem code chi tiết.

### Possible improvement

- Thêm chức năng AI Auto-Summary: Khi đội thi nộp link GitHub, hệ thống gọi AI tóm tắt 3 ý chính: "Dự án làm gì", "Dùng công nghệ gì", "Cấu trúc thư mục ra sao" để giám khảo nắm bắt nhanh trong 1 phút.
