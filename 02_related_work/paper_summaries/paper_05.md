# Paper 05 Summary

## Citation
- **Tên bài:** Leveraging Large Language Models for Academic Paper Recommendation and Trend Forecasting
- **Tác giả:** Liu, Y., Wang, S., & Tan, J.
- **Năm:** 2024
- **Nguồn:** ACM Digital Library
- **DOI/Link:** https://doi.org/10.1145/3631234.3631250

## Problem
Số lượng bài báo xuất bản hàng ngày là quá lớn, dẫn đến việc các hệ thống phân tích xu hướng truyền thống (chỉ dựa vào tần suất xuất hiện của từ khóa) thường bị chậm chân trong việc phát hiện ra các hướng đi đột phá mới. Ngoài ra, việc gợi ý bài báo cho người dùng hiện tại chưa cá nhân hóa theo đúng sở thích nghiên cứu của họ.

## Method
Tác giả đề xuất kiến trúc kết hợp giữa Mô hình ngôn ngữ lớn (LLM - GPT-4 được fine-tune) và kỹ thuật RAG (Retrieval-Augmented Generation). 
1. Hệ thống dùng RAG để truy xuất các đoạn abstract mới nhất từ cơ sở dữ liệu học thuật.
2. Đưa vào LLM để phân tích ngữ nghĩa sâu, đưa ra dự báo về các từ khóa có tiềm năng bùng nổ trong 6 tháng tới.
3. Sử dụng mô hình lọc cộng tác (Collaborative Filtering) dựa trên lịch sử tương tác của người dùng để đưa ra gợi ý bài báo cá nhân hóa.

## Dataset
Sử dụng bộ dữ liệu mã nguồn mở Semantic Scholar Open Research Corpus (S2ORC) gồm thông tin của hơn 100,000 bài báo thuộc chuyên ngành Trí tuệ nhân tạo.

## Evaluation
- Định lượng: Sử dụng các metric của hệ thống gợi ý bao gồm Recall@K, Precision, và NDCG (Normalized Discounted Cumulative Gain).
- Định tính: Đánh giá của các chuyên gia về độ hợp lý của các chủ đề được LLM dự báo.

## Results
Mô hình RAG kết hợp LLM giúp nâng cao độ chính xác của tính năng gợi ý bài báo lên 25% (Recall@5 đạt 0.74) và có khả năng phát hiện sớm các từ khóa xu hướng trước khi chúng thực sự bùng nổ trên các đồ thị thống kê số lượng truyền thống.

## Limitations
Chi phí vận hành hệ thống rất lớn do việc gọi API LLM liên tục gây tốn kém tài chính. Thời gian xử lý dữ liệu (Latency) cao, không phù hợp cho việc xử lý các yêu cầu realtime với lượng truy cập lớn của người dùng phổ thông.

## Relevance to our topic
Bài báo này liên quan trực tiếp đến các tính năng nâng cao của hệ thống theo dõi xu hướng xuất bản tạp chí khoa học: "Receive notifications for newly published papers", "Save bookmarks for papers or keywords", và "View trending research topics".

## Possible improvement
Để phù hợp với ràng buộc của đồ án nhóm (Sử dụng API miễn phí, không xử lý cấu trúc quá phức tạp và giảm chi phí hệ thống), nhóm sẽ không ứng dụng LLM cho toàn bộ database. Thay vào đó, nhóm chỉ ứng dụng các thư viện học máy/NLP gọn nhẹ (như TF-IDF cải tiến kết hợp gom cụm trên Node.js) để chạy định kỳ (Batch processing), đảm bảo hệ thống vừa đạt mục tiêu phân tích xu hướng vừa tối ưu hóa tốc độ tải trang và hoàn toàn miễn phí vận hành.