## Paper 04 Summary

### Citation

- **Tên bài:** Large Language Model as an Assignment Evaluator
- **Tác giả:** Cheng-Han Chiang, Wei-Chih Chen, Chun-Yi Kuan, et al.
- **Năm:** 2024
- **Nguồn:** ACL Anthology (EMNLP 2024)

### Problem

Quá tải trong việc chấm bài tập của giảng viên. Cần kiểm chứng xem LLM có thể làm Trợ giảng AI (LLM TAs) chấm điểm nhất quán không.

### Method

Sử dụng Prompt Chain of Thought (CoT) yêu cầu mô hình phân tích và suy luận trước khi đưa ra điểm. Thu thập phản hồi sinh viên để đánh giá tính công bằng.

### Dataset / Context

Khóa học thực tế với hơn 1.000 sinh viên.

### Evaluation

- **Tỷ lệ chấp nhận (Acceptance Rate):** Phần trăm sinh viên đồng ý với điểm số.
- **Độ bám sát Rubric (Rubric Consistency):** Khả năng AI tuân thủ đúng barem điểm.

### Results

- 75% sinh viên chấp nhận điểm từ LLM.
- 22% phát hiện AI đôi khi chấm chệch khỏi tiêu chí định sẵn.

### Limitations

- Môi trường học thuật, bài tập thường có đáp án chuẩn, khác với sự sáng tạo vô hạn trong Hackathon.

### Relevance to our topic

- **Mức độ liên quan:** Rất cao (Đặc biệt cho module chấm điểm theo Rubric).
- **Lý do:** Chứng minh tính khả thi của việc ép LLM chấm điểm theo barem.

### Possible improvement

- Sử dụng kỹ thuật CoT: Yêu cầu AI xuất ra một JSON giải thích từng tiêu chí chấm điểm (UI/UX, Backend, Database) trước khi tổng hợp thành điểm cuối cùng cho đội Hackathon.
