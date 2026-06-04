## Paper 06 Summary

### Citation

- **Tên bài:** Automatic Grading of Short Answers Using Large Language Models in SE Courses
- **Tác giả:** Ta Nguyen Binh Duong, Chai Yi Meng
- **Năm:** 2024
- **Nguồn:** 2024 IEEE EDUCON

### Problem

Hệ thống Autograding truyền thống chỉ chạy Test Case, không chấm được tư duy thiết kế phần mềm.

### Method

Xây dựng Web App tích hợp GPT-3.5/4 qua API để chấm điểm tự luận ngắn. Có tính năng "manual override" cho giảng viên.

### Dataset / Context

Các khóa học Kỹ thuật Phần mềm (Software Engineering).

### Evaluation

- **Độ tin cậy của điểm số:** Đánh giá định tính từ giảng viên.
- **Khả năng can thiệp (Override Frequency):** Tần suất giảng viên phải sửa điểm của AI.

### Results

- AI cung cấp feedback tức thì tốt, nhưng giảng viên thường xuyên phải tinh chỉnh lại điểm số cuối cùng.

### Limitations

- Chưa thử nghiệm trên việc đọc các repository mã nguồn phức tạp.

### Relevance to our topic

- **Mức độ liên quan:** Trung bình.
- **Lý do:** Kiến trúc Web App khá tương đồng với hệ thống quản lý Hackathon nhóm đang hướng tới.

### Possible improvement

- Xây dựng giao diện Dashboard cho giám khảo, hiển thị rõ ràng "Điểm AI đề xuất" và có thanh trượt/ô nhập liệu để giám khảo dễ dàng Override điểm số.
