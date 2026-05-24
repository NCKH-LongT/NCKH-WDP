# Paper 02 Summary

## Citation
- **Tên bài:** Dynamic Topic Modeling on Scientific Abstracts Using BERTopic
- **Tác giả:** Grootendorst, M.
- **Năm:** 2022
- **Nguồn:** arXiv / NLP Research
- **DOI/Link:** https://doi.org/10.48550/arXiv.2203.05794

## Problem
Xử lý ngôn ngữ tự nhiên trong văn bản học thuật gặp thách thức lớn do abstract bài báo khoa học chứa nhiều từ ngữ chuyên ngành phức tạp và ngữ cảnh sâu. Các thuật toán cũ (như TF-IDF hay LDA) bỏ qua ngữ cảnh của từ, dẫn đến việc gom cụm từ khóa xu hướng bị rời rạc, thiếu chính xác.

## Method
Tác giả đề xuất kỹ thuật **BERTopic** gồm các bước tuần tự:
1. Nhúng ngữ cảnh câu (Contextual Embeddings) bằng BERT.
2. Giảm chiều dữ liệu bằng UMAP.
3. Gom cụm mật độ bằng HDBSCAN để tự động tối ưu số lượng chủ đề mà không cần khai báo trước.
4. Trích xuất từ khóa đặc trưng bằng thuật toán cải tiến c-TF-IDF (Class-based TF-IDF).

## Dataset
Tập dữ liệu mở gồm 50,000 đoạn tóm tắt (abstract) các bài báo thuộc lĩnh vực Trí tuệ nhân tạo (AI) trên nền tảng arXiv.

## Evaluation
- Biểu đồ Silhouette Score để đo độ tách biệt giữa các cụm chủ đề xu hướng.
- Topic Coherence đánh giá độ tương quan ngữ nghĩa nội bộ cụm.

## Results
BERTopic đạt điểm Topic Coherence vượt trội so với LDA truyền thống (tăng từ 0.54 lên 0.72). Thuật toán tự động nhận diện được các cụm xu hướng ngách rất nhỏ như "Few-shot learning trong y tế" hay "Edge AI".

## Limitations
Mô hình yêu cầu năng lực xử lý phần cứng cao (cần GPU để chạy embedding). Khi xử lý lượng dữ liệu lớn từ API bên thứ ba, tốc độ phản hồi có thể bị chậm nếu không áp dụng cơ chế lưu trữ đệm (Caching).

## Relevance to our topic
Bài báo giải quyết bài toán cốt lõi trong yêu cầu hệ thống của nhóm: "Track publication trends by keyword or topic" và "View trending research topics". Đây chính là giải pháp công nghệ AI giúp hệ thống tự động gom nhóm hàng ngàn bài báo thu thập từ Semantic Scholar thành các "Chủ đề nổi bật" trên Dashboard mà admin không cần phân loại thủ công.

## Possible improvement
Do giới hạn phạm vi của hệ thống theo dõi xu hướng xuất bản tạp chí khoa học là "Chỉ thu thập metadata và không xử lý realtime toàn văn để giảm độ phức tạp", nhóm sẽ cải tiến bằng cách chạy thuật toán BERTopic này theo chu kỳ định kỳ (Offline batch processing - ví dụ hàng tuần) thông qua các Worker script, sau đó lưu kết quả xu hướng đã phân tích vào MongoDB. Cách này giúp ứng dụng chạy cực nhanh, giao diện Dashboard tải tức thì mà vẫn có bộ lọc xu hướng chính xác cao.