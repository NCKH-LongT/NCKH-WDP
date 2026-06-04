## Paper 02 Summary

### Citation

- **Tên bài:** Automated Code Review in Practice
- **Tác giả:** Umut Cihan, Vahid Haratian, Arda İçöz, et al.
- **Năm:** 2024
- **Nguồn:** IEEE Xplore

### Problem

Tác động thực tế của các công cụ AI code review đối với hiệu suất làm việc và chất lượng phần mềm vẫn chưa được định lượng rõ ràng.

### Method

Sử dụng phương pháp thực nghiệm (Empirical Study) kết hợp dữ liệu định lượng (phân tích Pull Request) và định tính (khảo sát) qua công cụ Qodo PR Agent.

### Dataset / Context

Áp dụng trên môi trường phát triển phần mềm thực tế thông qua các Pull Request trên GitHub.

### Evaluation

- **Thời gian xử lý (Resolution Time):** Thời gian đóng một Pull Request.
- **Tỷ lệ giải quyết (Resolution Rate):** Tỷ lệ comment của AI được xử lý.

### Results

- 73,8% comment của AI được lập trình viên giải quyết.
- Thời gian đóng Pull Request trung bình tăng từ 5h52m lên 8h20m.

### Limitations

- Mẫu khảo sát định tính còn nhỏ.
- Phụ thuộc vào một công cụ cụ thể (Qodo).

### Relevance to our topic

- **Mức độ liên quan:** Cao.
- **Lý do:** Cho thấy một thực tế là dùng AI có thể làm tăng thời gian review nếu giám khảo phải đọc và kiểm chứng quá nhiều text từ AI sinh ra.

### Possible improvement

- Nghiên cứu cách giới hạn độ dài câu trả lời của AI (Prompt engineering) để tạo ra các nhận xét ngắn gọn, đi thẳng vào vấn đề (như chấm điểm Clean Code, Cấu trúc), giúp giám khảo tiết kiệm thời gian đọc.
