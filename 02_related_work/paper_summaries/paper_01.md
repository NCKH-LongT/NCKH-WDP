## Paper 01 Summary

### Citation

- **Tên bài:** BitsAI-CR: Automated Code Review via LLM in Practice
- **Tác giả:** Tao Sun, Jian Xu, Yuanpeng Li, Zhao Yan, Ge Zhang, et al.
- **Năm:** 2025
- **Nguồn:** arXiv (ByteDance)
- **Link:** https://arxiv.org/abs/2501.15134

### Problem

Quá trình đánh giá mã nguồn tốn nhiều thời gian. Các LLM hiện tại thường sinh ra "ảo giác" hoặc nhận xét chung chung, khiến lập trình viên có xu hướng phớt lờ cảnh báo của AI.

### Method

Đề xuất framework hai giai đoạn: (1) RuleChecker dùng luật tĩnh để tìm lỗi; (2) ReviewFilter dùng LLM để thẩm định lại nhằm lọc bỏ cảnh báo giả. Đề xuất thang đo "Outdated Rate" đo lường tỷ lệ chấp nhận của con người.

### Dataset / Context

Triển khai trên hệ thống công nghiệp của ByteDance đối với các dự án ngôn ngữ Go.

### Evaluation

- **Độ chính xác (Precision):** Tỷ lệ các bình luận của AI hoàn toàn chính xác về mặt kỹ thuật.
- **Mức độ áp dụng (Outdated Rate):** Tỷ lệ lập trình viên thực sự sửa code theo gợi ý của AI.

### Results

- Đạt độ chính xác 75% cho các nhận xét tự động.
- Phục vụ 12.000 người dùng tích cực hàng tuần.
- Tỷ lệ áp dụng nhận xét ổn định ở mức 26,7%.

### Limitations

- Chỉ tập trung vào ngôn ngữ Go.
- Môi trường thử nghiệm là dự án nội bộ của doanh nghiệp, có thể khác với mã nguồn mở hoặc bài thi sinh viên.

### Relevance to our topic

- **Mức độ liên quan:** Rất cao.
- **Lý do:** Bài báo giải quyết trực tiếp bài toán làm sao để con người tin tưởng vào nhận xét mã nguồn của AI, rất sát với việc giám khảo dùng AI để review code trong Hackathon.

### Possible improvement

- Thay vì đo "Outdated Rate" của lập trình viên, nhóm có thể đo "Tỷ lệ đồng thuận của Giám khảo" (Judge Acceptance Rate) đối với các nhận xét và điểm số do AI đề xuất.
