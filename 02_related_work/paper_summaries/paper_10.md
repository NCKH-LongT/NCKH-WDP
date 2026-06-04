## Paper 10 Summary

### Citation

- **Tên bài:** Towards LLM-Based Autograding for Short Textual Answers
- **Tác giả:** Johannes Schneider, Bernd Schenk, Christina Niklaus
- **Năm:** 2024
- **Nguồn:** CSEDU 2024

### Problem

Việc áp dụng LLM nguyên bản ("out-of-the-box") để tự động chấm điểm có đáng tin cậy không khi đánh giá là công việc chủ quan.

### Method

Thực nghiệm đối chiếu kết quả chấm của LLM với điểm bảo chứng từ hội đồng chuyên môn.

### Dataset / Context

Các bài kiểm tra ngắn định dạng văn bản.

### Evaluation

- **Độ lệch chuẩn (Standard Deviation):** Đo lường khoảng cách giữa điểm của AI và chuyên gia.

### Results

- LLM là công cụ tham chiếu xuất sắc, nhưng đôi khi đưa ra các quyết định trừng phạt điểm (penalize) vô lý.

### Limitations

- Chỉ thử nghiệm trên văn bản (Text), chưa áp dụng cho logic lập trình.

### Relevance to our topic

- **Mức độ liên quan:** Trung bình.
- **Lý do:** Nhắc nhở về rủi ro khi tin tưởng 100% vào AI.

### Possible improvement

- Áp dụng làm cơ sở lý luận (Literature Review) trong báo cáo nghiên cứu: Khẳng định hệ thống SEAL Hackathon dùng AI như một "Copilot" (người đồng hành) hỗ trợ giám khảo, tuyệt đối không dùng để tự động quyết định loại hay chọn đội thi.
