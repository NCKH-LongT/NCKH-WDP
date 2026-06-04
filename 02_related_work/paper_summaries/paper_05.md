## Paper 05 Summary

### Citation

- **Tên bài:** Towards Reliable LLM Grading Through Self-Consistency and Selective Human Review
- **Tác giả:** L. Korthals, et al.
- **Năm:** 2026
- **Nguồn:** MDPI

### Problem

LLM chấm bài thường mắc lỗi không nhất quán, thiên kiến chấm điểm quá chặt (underscoring).

### Method

Đề xuất hệ thống SURE sử dụng Self-consistency (cho LLM sinh kết quả nhiều lần rồi lấy số đông) và Ensemble (kết hợp nhiều LLM). Kết hợp Human-in-the-loop để con người duyệt lại ca khó.

### Dataset / Context

Dữ liệu từ 46 sinh viên với 130 bài tập lập trình và câu hỏi mở.

### Evaluation

- **Độ chính xác (Accuracy):** So sánh điểm của AI với điểm bảo chứng của con người.
- **Thời gian tiết kiệm:** Số giờ giảm tải cho giảng viên.

### Results

- Đạt độ chính xác ngang bằng con người ở 70-90% trường hợp.

### Limitations

- Tốn chi phí API gấp nhiều lần do phải gọi LLM nhiều lần cho cùng một bài toán (Self-consistency).

### Relevance to our topic

- **Mức độ liên quan:** Trung bình.
- **Lý do:** Kỹ thuật khá nặng, có thể gây quá tải API nếu áp dụng trực tiếp, nhưng cơ chế Human-in-the-loop rất phù hợp với ý tưởng hệ thống.

### Possible improvement

- Hệ thống SEAL Hackathon chỉ dùng AI để "đề xuất" (Draft Score), giám khảo bắt buộc phải review và ấn nút "Approve/Edit" (Human-in-the-loop) để đảm bảo công bằng tuyệt đối.
