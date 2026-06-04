## Paper 03 Summary

### Citation

- **Tên bài:** Context-Aware Code Review Automation: A Retrieval-Augmented Approach
- **Tác giả:** B. İçöz, et al.
- **Năm:** 2026
- **Nguồn:** MDPI

### Problem

LLM tạo bình luận Code Review thường thiếu tính bối cảnh, dẫn đến các gợi ý không sát với cấu trúc tổng thể của dự án.

### Method

Kết hợp LLM với kỹ thuật RAG (Retrieval-Augmented Generation) để truy xuất các đoạn code liên quan và lịch sử commit trước khi sinh nhận xét. Đánh giá bằng phương pháp "LLM-as-a-Judge".

### Dataset / Context

Tập dữ liệu gồm các dự án Python 3.13, với 1.625 trường hợp kiểm thử.

### Evaluation

- **Độ tương đồng (BLEU, ROUGE, Cosine Similarity):** So sánh text sinh ra với text của chuyên gia.
- **Điểm đánh giá chéo:** Dùng LLM lớn (Llama-3-70B) chấm điểm LLM nhỏ hơn.

### Results

- RAG giúp cải thiện đáng kể khả năng nhận thức bối cảnh dự án so với việc chỉ nộp từng file riêng lẻ cho LLM.

### Limitations

- Phụ thuộc lớn vào chất lượng của Embedding model và thuật toán chunking mã nguồn.

### Relevance to our topic

- **Mức độ liên quan:** Rất cao.
- **Lý do:** Một dự án Hackathon gồm rất nhiều file. Không thể paste toàn bộ vào LLM. RAG là giải pháp bắt buộc để hệ thống của nhóm hoạt động.

### Possible improvement

- Áp dụng kiến trúc RAG từ bài báo để trích xuất (clone) repository từ GitHub, chunk các file code theo class/function và dùng Vector DB để truy xuất ngữ cảnh cho mô hình Gemini chấm điểm.
