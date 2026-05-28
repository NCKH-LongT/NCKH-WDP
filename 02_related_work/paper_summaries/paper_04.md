# Paper 04 Summary

## Citation
- **Tên bài:** Enhancing Hotel Recommendation Systems with LLM-Based Sentiment Analysis and RAG Architecture
- **Tác giả:** Thanh-Chung Dao, Hoang-Quynh Nguyen, Xuan-Hieu Phan
- **Năm:** 2024
- **Nguồn:** Information (MDPI), Vol. 15, No. 11
- **DOI/Link:** https://doi.org/10.3390/info15110700

## Problem
Các hệ thống gợi ý khách sạn truyền thống (Collaborative Filtering hoặc Content-Based) thường bỏ qua các thông tin ngữ nghĩa sâu sắc ẩn trong các bài đánh giá (reviews) dạng văn bản tự do của người dùng. Ngoài ra, việc thiếu khả năng tích hợp tri thức thời gian thực và bối cảnh cá nhân hóa khiến hệ thống dễ đưa ra các gợi ý lỗi thời hoặc không khớp chính xác với mong muốn thực tế của khách hàng.

## Method
Tác giả đề xuất một framework kiến trúc tích hợp hai thành phần kỹ thuật tiên tiến:
1. **LLM-Based Sentiment Analysis (Phân tích cảm xúc bằng LLM):** Sử dụng các mô hình ngôn ngữ lớn để trích xuất điểm số cảm xúc (sentiment scores) chi tiết từ văn bản đánh giá của khách hàng, thay thế cho các phương pháp gán nhãn thủ công hoặc học máy truyền thống.
2. **Kiến trúc RAG (Retrieval-Augmented Generation):** Sử dụng một cơ sở dữ liệu Vector (Vector Database) lưu trữ các biểu diễn nhúng (embeddings) của dữ liệu khách sạn và phản hồi. Khi có truy vấn từ người dùng, pipeline RAG sẽ truy xuất các ngữ cảnh phù hợp nhất để làm giàu prompt cho LLM sinh câu trả lời và gợi ý phòng.

## Dataset / Context
Hệ thống được thử nghiệm và đánh giá thực nghiệm trên domain quản lý và đặt phòng khách sạn, sử dụng tập dữ liệu lớn chứa hàng ngàn đánh giá đa chiều của khách hàng về dịch vụ phòng, tiện ích và vị trí địa lý.

## Evaluation & Metrics
Framework được đo lường thông qua:
- Độ chính xác của phân tích cảm xúc (so sánh BERTScore và độ tương đồng ngữ nghĩa).
- Hiệu suất gợi ý: Precision@K, Recall@K, và F1-Score@K tại các mức K khác nhau (K=3, 5, 10).
- Khảo sát trải nghiệm người dùng (User Acceptance Rate).

## Results
- Việc kết hợp điểm số cảm xúc trích xuất từ LLM vào pipeline RAG giúp tăng đáng kể độ chính xác của hệ thống gợi ý (tăng từ 12% - 15% chỉ số F1-Score so với hệ thống RAG thuần túy không có phân tích cảm xúc).
- Khung kiến trúc chứng minh tính khả thi cao khi xử lý mượt mà các truy vấn phức tạp mang tính cá nhân hóa cao của khách hàng (ví dụ: "Tìm phòng khách sạn yên tĩnh, phù hợp cho trẻ em và có view biển").

## Limitations
- Chi phí tính toán và token API tăng lên do hệ thống phải xử lý song song hai tác vụ: phân tích cảm xúc trên tập dữ liệu reviews lớn và thực hiện truy vấn vector RAG.
- Độ trễ (latency) hệ thống có xu hướng tăng nhẹ khi số lượng tài liệu ngữ cảnh cần truy xuất quá lớn.

## Relevance to our topic
Mức độ liên quan: Tuyệt đối (Core-Technical paper). Bài báo này là một "bản thiết kế" hoàn hảo, kết hợp toàn bộ các kỹ thuật phân tích phản hồi (như bài 2) và kiến trúc chatbot RAG (như bài 1) vào đúng domain Khách sạn của SmartStay AI.

## Possible improvement for our system
Áp dụng trực tiếp vào **SmartStay AI**:
1. **Xây dựng module gợi ý thông minh (Smart Recommendation Engine):** Thay vì chỉ cho khách hàng tìm kiếm phòng theo bộ lọc cứng (giá, số giường), SmartStay AI sẽ tích hợp pipeline RAG + Sentiment của bài báo này vào ô tìm kiếm hoặc khung chat. Cho phép khách gõ câu lệnh tự nhiên để hệ thống tự quét cơ sở dữ liệu Vector và trả về danh sách phòng được cá nhân hóa kèm lý do trích xuất từ review của các khách trước.
2. **Tối ưu hóa:** Áp dụng kết luận của bài báo số 1 (sử dụng GPT-4.1-mini và Multilingual-E5-Large) để giải quyết triệt để vấn đề hạn chế về mặt "độ trễ hệ thống" mà bài báo số 4 này gặp phải.