## Paper 08 Summary

### Citation

- **Tên bài:** Evaluating LLM-Generated Code: A Benchmark and Developer Study
- **Tác giả:** J. Szych
- **Năm:** 2026
- **Nguồn:** arXiv

### Problem

Các benchmark hiện tại chỉ đo tính đúng đắn thuật toán, bỏ qua khả năng tích hợp và tiêu chuẩn "production-ready" của dự án.

### Method

Đề xuất đánh giá 3 cấp độ: Logic nghiệp vụ, Chất lượng mã nguồn (bằng công cụ) và Đánh giá từ hội đồng thực tế (Human Review).

### Dataset / Context

Các dự án Computer Science phức tạp đòi hỏi nhiều tầng kiến trúc.

### Evaluation

- **Điểm đánh giá toàn diện:** So sánh giữa code thuần túy và code có khả năng deploy.

### Results

- LLM gặp khó khăn lớn khi đánh giá các phần liên quan đến DevOps hoặc tích hợp giao diện phức tạp.

### Limitations

- Tập trung nhiều vào code do AI tạo ra thay vì code của con người.

### Relevance to our topic

- **Mức độ liên quan:** Trung bình.
- **Lý do:** Giúp nhóm nhận diện được "điểm mù" của AI.

### Possible improvement

- Trong tiêu chí chấm Hackathon, có thể loại trừ các mục "Khả năng triển khai/DevOps" ra khỏi phần AI chấm tự động, và giao hoàn toàn phần này cho Giám khảo con người.
